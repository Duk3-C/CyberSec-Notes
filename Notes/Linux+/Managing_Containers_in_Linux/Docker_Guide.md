# Docker Learning Guide — Study Path + Free Resources

**Companion note:** `Managing_Containers_in_Linux/Managing_Container_Administration_Storage_and_Networking.md` covers the CompTIA Linux+ view of containers (OCI, runc/containerd, container vs VM). This guide is the hands-on Docker path that builds on it.

**Exam tie-in:** Linux+ (XK0-005) Domain 5 — Scripting, Containers & Automation (19%). Expected skills: container concepts, `docker` lifecycle (run/stop/restart), images from registries, `dockerfile` basics, volume mounting, port publishing, and container management commands.

---

## 1. Install Docker Engine (Debian/Ubuntu)

```bash
# Official repo method (recommended)
sudo apt update
sudo apt install -y ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

**Post-install (avoid sudo for every command):**
```bash
sudo usermod -aG docker $USER
# log out/in (or `newgrp docker`) to apply
docker version      # client + server version
docker run hello-world   # smoke test
```

> Security note: the `docker` group grants root-equivalent access — only add trusted users.

---

## 2. Core Learning Path

### 2.1 Images vs Containers (do this first)
- **Image** = read-only template/blueprint (layered filesystem)
- **Container** = running instance of an image (writable layer on top)
- Registry (Docker Hub) → `pull` image → `run` container

```bash
docker pull nginx:alpine        # fetch image (name:tag)
docker images                   # list local images
docker run -d -p 8080:80 --name web nginx:alpine
docker ps                       # running containers (add -a for all)
docker logs web                 # container logs
docker exec -it web bash        # shell inside container
docker stop web && docker rm web
docker rmi nginx:alpine         # remove image
```

**Practice:** run nginx, exec into it, modify `/usr/share/nginx/html/index.html`, watch it in browser, clean up.

### 2.2 Building Images — Dockerfile
Key instructions: `FROM` (base image), `RUN` (build-time command), `COPY` (files in), `CMD` vs `ENTRYPOINT` (runtime default vs fixed command), `EXPOSE` (documentation only — `-p` does the publishing), `ENV`, `WORKDIR`, `USER`.

```dockerfile
FROM python:3.12-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
COPY app.py .
EXPOSE 8000
USER 10001
CMD ["python", "app.py"]
```

```bash
docker build -t myapp:1.0 .
docker image history myapp:1.0   # see layer caching in action
```

**Golden rules:**
- Order matters — frequent changes (code) last, stable deps first → better layer cache
- Use specific tags (`python:3.12-slim`), never `latest` in production
- Add `.dockerignore` (node_modules, .git, secrets)

### 2.3 Volumes & Bind Mounts (data persistence)
Containers are ephemeral — the writable layer dies with the container.

```bash
# Named volume (managed by Docker, survives rm)
docker volume create data
docker run -d -v data:/var/lib/mysql --name db mysql:8

# Bind mount (host path mapped in)
docker run -d -p 8080:80 -v /home/user/site:/usr/share/nginx/html nginx:alpine

docker volume ls && docker volume inspect data
```

**Practice:** run a `-v`-mounted nginx, edit a host file, refresh browser — no rebuild needed.

### 2.4 Networking
- Default bridge: per-container IP, DNS resolves container **names**
- `-p HOST:CONTAINER` publishes ports (e.g. `-p 8080:80`)
- `--network host` skips NAT (reuses host net), `none` = isolated
- `--network mynet` — user-defined bridge gives DNS + container linking

```bash
docker network create mynet
docker run -d --network mynet --name web nginx:alpine
docker run -it --network mynet --name tester alpine sh
# inside tester: wget -qO- http://web   → resolves by NAME, not IP
```

### 2.5 Docker Compose (multi-container apps)
Declarative YAML: services, networks, volumes, ports, env.

```yaml
# compose.yml
services:
  db:
    image: postgres:16-alpine
    environment:
      POSTGRES_PASSWORD: changeme
    volumes:
      - pgdata:/var/lib/postgresql/data
  app:
    build: .
    ports:
      - "8000:8000"
    depends_on:
      - db
volumes:
  pgdata:
```

```bash
docker compose up -d          # start everything
docker compose ps
docker compose logs -f app
docker compose down           # stop + remove (volumes persist)
docker compose down -v        # + delete volumes
```

### 2.6 Image Hygiene / Day-2 Ops
```bash
docker system df              # disk usage
docker system prune -a        # remove unused images/containers/networks/build cache
docker stats                  # live CPU/mem per container
docker logs -f --tail 100 web
docker inspect web            # deep dive into config/state
docker cp web:/etc/nginx/nginx.conf ./
```

---

## 3. Hands-On Ladder (do in order)

- [ ] **L1** Run `nginx:alpine` on port 8080; `exec` inside; create a file; remove everything with `docker system prune -a`
- [ ] **L2** Bind-mount a local `~/site` folder as the web root; change content live
- [ ] **L3** Write a Dockerfile for a tiny Python/Node app (FROM + COPY + RUN + CMD); build + run
- [ ] **L4** Multi-stage build: build stage (e.g. `golang:1.22` or `node:22`) → slim runtime stage with only the binary/output
- [ ] **L5** Compose app: web app + PostgreSQL with named volume; restart and confirm data survives `docker compose down`
- [ ] **L6** Harden it: non-root `USER`, `--read-only`, drop caps (`--cap-drop ALL`), add healthcheck, verify with a scan (below)

---

## 4. Container Security (also Linux+ relevant: SELinux/AppArmor, caps)

- **Never run as root** — `USER 10001` in Dockerfile; `--user` at runtime
- **Minimal base images** — `alpine` / `distroless` / `slim` variants (smaller attack surface)
- **Secrets** — never in `ENV` in the image or `docker build` args logs; mount files (`-v secret:/run/secrets:ro`) or use `--env-file`
- **Scan images** — `docker scout quickview <image>` (free w/ Docker subscription) or open-source `trivy image <image>`
- **Lockdown flags:**
  ```bash
  docker run -d --cap-drop ALL --security-opt no-new-privileges --read-only --tmpfs /tmp -p 8080:80 nginx:alpine
  ```
- **Backups** — named volumes are in `/var/lib/docker/volumes/`; backup with `docker run --rm -v myvol:/data -v $(pwd):/backup alpine tar czf /backup/myvol.tar.gz -C /data .`

---

## 5. Curated Free Resources (verified working Aug 2026)

### Official (start here)
- **Docker 45-min workshop** — step-by-step build/run/share/compose: `https://docs.docker.com/get-started/workshop/`
- **Docker Getting Started guides** (concepts, images, Compose, Dockerfile best practices): `https://docs.docker.com/guides/getting-started/`
- **Free training hub** (official learning paths): `https://www.docker.com/trainings/`

### Interactive browser labs (no install needed)
- **DockerLabs (Collabnix)** — huge free curriculum: beginner → intermediate → expert, incl. security + swarm. `https://dockerlabs.collabnix.com/` (repo: `github.com/collabnix/dockerlabs`)
- **Killercoda Docker playground** — free in-browser Docker VM: `https://killercoda.com/playgrounds/docker`
- **KodeKloud free Docker labs** — browser-based practice: `https://kodekloud.com/studio/labs/docker`
- **Docker Course Labs (Elton Stoneman)** — hands-on labs for *Learn Docker in a Month of Lunches*: `https://docker.courselabs.co/`
- ⚠️ *Play with Docker (PWD) is deprecated — unavailable since March 1, 2026. Use the above instead.*

### YouTube (free, complete courses)
- **freeCodeCamp — Docker Full Course (7 hrs, 2026)** — Dockerfile, images, Hub, networking, storage, Compose, Swarm, real projects: `https://www.youtube.com/watch?v=rjjES5IsPdg`
- **freeCodeCamp — Docker Containers & Kubernetes Fundamentals (5.5 hrs)** — hands-on w/ Guy Barrette: `https://www.youtube.com/watch?v=kTp5xUtcalw`
- **TechWorld with Nana — Docker Tutorial for Beginners (3 hrs)** — best explanation of images/containers/volumes/networks/Compose: `https://www.youtube.com/watch?v=3c-iBn73dDE`
- **DevOps Directive — Complete Docker Course: Beginner to PRO (4.5 hrs)**: `https://www.youtube.com/watch?v=RqTEHSBrYFw`

### Books (free)
- ***Docker Deep Dive* (Nigel Poulton)** — the #1 Docker book; free 2020-edition PDF on GitHub: `https://github.com/Garabito/Books-Resources-programming` (Devops → `Docker Deep Dive (Nigel Poulton).pdf`)
- ***Learn Docker in a Month of Lunches* (Elton Stoneman)** — book is paid (Manning), but all labs are free: `https://docker.courselabs.co/`

### Cheatsheets
- **Docker cheatsheet (cheatsheetworks)** — all commands on one page: search "Docker cheatsheet PDF/cheatsheetworks"
- **Docker CLI reference** (always authoritative): `https://docs.docker.com/reference/cli/docker/`

---

## 6. What to Do After Docker

1. **Docker Swarm** (covered in the freeCodeCamp course + DockerLabs) — built-in orchestration
2. **Kubernetes** (only if you want orchestration at scale) — `minikube` for local practice
3. **Security-adjacent**: signing images (Docker Content Trust), SBOMs, Docker Scout/Trivy in CI — direct CySA+/DevSecOps crossover