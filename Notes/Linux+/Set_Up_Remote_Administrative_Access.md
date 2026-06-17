###Secure Shell Configuration
    SSH is an even more important tool with the rapid growth of cloud computing. SSH allows cloud administrators to recurely connect to remote cloud resources. It is an essential tool for all administrators, not just Linux sysadmins.
    
    Two configuration files manage SSH on Linux. The first, `/etc/ssh/ssh_config`, defines SSH client settings and usually is not customized. The second, /etc/ssh/sshd_config, has many configuration options, most of which are security-oriented.
    Common SSH server configurations with the `/etc/ssh/sshd_config` include changing ports, preventing the root user from connecting over the network via SSH, and requiring key-based authentication. To block the root user from authenticating over SSH, type `PermitRootLogin no`.

---

###Key-based Authentication
    The standard SSH authentication process is a password challenge. The connecting user submits a username and password that is recognized on the local system. Password-based authentication, however, has some significant limitations: passwords may be intercepted, guessed, or found after being written down. Automated processes, such as remote backup scripts that connect over SSH, can be interrupted by password challenges. 
    **Key-pased authentication** generates a public-private key pair that uniquely identifies the user. The private key remains on the user's workstation, and the public key is stored on the remote system. When the user attempts to connect, the keys are checked to ensure they match, and a match guarantees the user's identity.
    ***Cloud service providers strongly urge administrators to administer systems via SSH key-based authentication. Many organizations rely on SSH authenticated keys for on-premises and cloud resources***.
    
---

###Data Transfer Tools
    **The `scp` Command**:
        The SCP tool copies data to or from a remote host over SSH. Because it uses SSH, data you send will be encrypted in transit, protecting its confidentiality. Like SSH, SCP uses TCP port 22 by default. You might use `scp` to transfer backup jobs or other security-related files to remote sites for storage.
        The following is an example of copying a file to a remote host using the `scp` command: 
        ```bash
        scp file.txt user@host:/home/dir
        ```

    `wget` is a command-line utility only, while `curl` uses the cross-platform `libcurl` library and is, therefore, more easily ported to other systems.
    `wget` and `curl` are HTTP clients that can download files from remote webservers. Most HTTP connections occur using web browsers. They download a series of files the browser assembles into a web page. However, simple downloads don't justify the use of a browser. Furthermore, it's difficult to script or automate browser-based downloads.
    `wget` is better suited for straightforward file downloads from a web serverm while `curl` is better suited to building and managing more complex requests and responses from the web servers.
    
    **The `nc` Command**: 
        The `netcat` or `nc` command can test connectivity and send data across network connections. The command may be spelled out as "netcat" or abbreviated as "nc" depending on the distribution. You can identify systems by IP address or hostname.
        When troubleshooting, use `nc` to listen on the destination computer and attempt a connection from the source computer to verify network functionality. 
        The syntax of the `nc` command is `nc {options}`.
        
        **Port Scan a computer:**
            ```bash
            nc -z -v domain.tld 1-1000 
            ```
        This scans ports 1 to 1000
        
        Transfer file content between two computers:
            ```bash
            nc -l 4242 > received.file  # Listen on Port
            nc comp1 < original.file    # Connect to listener`
            ```
        
        Connect two computers for the purpose of transferring information:
            ```bash
            nc -l 4242                  # Listen on port
            nc comp1 4242               # Connect to listener
            ```
