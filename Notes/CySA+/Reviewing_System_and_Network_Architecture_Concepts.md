## Explore Operating System Concepts
---
**System Hardening** enhances the security of an operating system, application, device, or service
by reducing its attack surface. Hardening involves enabling or disabling specific features and
restricting access to sensitive areas of the system, such as protected operating system files,
windows registry, configuration files, and logs.

**Windows Registry and File System**
		Database for storing operating system, device, and software application configuration
		information. The registry is comprised of a set of five root keys that contain computer and user
		databases. 
		
Configuration Files
		Linux does not have a registry database like Windows. All configuration settings are stored in
		text files saved in the file system. As a general rule, all configuration files are contained
		within subdirectories of the /etc directory but are also often located in /usr, /opt, /var,
		among others.
		Software applications and operating systems like Windows use configuration files extensively. They
		allow the operating system and applications running on it to be configured and depend upon different
		formatting standards.
---
		
## Understanding Virtualization, Containers, and Emulation
---
Virtualization:
		Hypervisors fall into two major catergories. Type I and Type II. Type I hyprvisors are the kind
		used in an enterprise setting and are purpose-built, lean, and efficient. To look at the console
		of a server running a Type I hypervisor would yield a screen with a message directing the
		observer to use special-purpose, remote management tools to interact with it. A type II
		hypervisor is one added to a full-featured operating system.
		
Containerization:
		Container includes all necessary components and dependencies. Similar to virtual machines but
		more lightweight. Share the host system's operating system kernel. Easily deploy and manage
		applications across different environments.
---

## Explore Impacts of Serverless Computing and SDN
---
Serverless Computing:
		Modern design pattern for service delivery. It is strongly associated with modern web
		applications, but providers appear with products to completely replace the concept of the
		corporate LAN. Serverless platforms eliminate the need to manage physical or virtual server
		instances, so there is little to no management effort for software and patches, administration
		privileges, or file system security monitoring.
		Serverless does have considerable risks, As a new technology, use cases and best practices
		continue to mature, especially concerning security. There is also a critical and unavoidable
		dependency on the service provider, with limited options for disaster recovery should that
		service provision fail.
---

## Software-Defined Networking (SDN)
---
Network segmentation divides a large network into smaller networks, or subnetworks, to improve
security and performance. Segmentation helps to control access and limit the spread of malicious
traffic by implementing control points designed to decide whether traffic should be allowed to pass.

SDN abstracts physical network devices, like routers and switches, replacing them with a virtual
control plane that makes all decisions regarding traffic management. SDN allows for building
cloud-based networks using virtualized equivalents of physical routers, firewalls, and other network
devices used in on-premises networks.
