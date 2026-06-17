##Container Concepts
    A **container** is a complete, portable solution. It contains the application code and everything needed to run the software. This complete package is portable and will run on any platform hosting a container solution. Containerized software developed on a Linux workstation runs the same way on a Windows cloud-based **virtual machine**. 
    Examples of containerized applications include Apache or nginx web servers, databases, or monitoring and logging utilities.
    You can deploy containers on physical,  on-premises servers, or in a cloud infrastructure. Hosting containers in the cloud provides all the usual cloud benefits: scalability, high availability, and quick deployments.
    Containers consist of the following three elements:
        - Container management software: Specialized software that provides the container environment.
        - Container images: Templates for building containers that will run in the manageent environment
        - Containerized application: Self-sufficient software software packages that use the compute,storage, and network functionality provided by containers.

    Container engines use the **Open Container Initiative (OCI)** standard for container-image formats. The OCI is a governance body managing open-container format among developers of container technologies. The runc and containerd container runtimes use OCI specifications.
    
    Comparing Containers to Virtual Machines
        Containers provide a different form of virtualization than the one offered by VMs. A container is a complete, portable solution. It contains the application code, runtime, binaries and libraries, settings, and other components. 
        Containerized software developed on a Linux workstation runs the same way on a cloud-based VM.
