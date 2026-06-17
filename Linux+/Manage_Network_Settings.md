###NetworkManager
    Many Linux distributions include a utility called **NetworkManager** to help properly configure the IP information. NetworkManager includes three different user interfaces, depending on wether a graphical user interface (GUI) is available on the Linux system.

###The `nmcli` Command
    The `nmcli` tool is the most fundamental of the NetworkManager user interfaces. It contains many subcommands to view and configure network information. Because many Linux servers will not include a GUI, it is important to be comfortable with nmcli to manage network settings.
    
    The syntax of the `nmcli` command is `nmcli {options} {subcommand} {argumentes}`.
    Here are some standard subcomands for `nmcli`:
        - `general status` Displays a summary of network connectivity data.
        - `connection show` Displays identification information for each **network interface card (NIC)**
        - `con up {deviceID}` Enables the specified NIC
        - `con down {deviceID}` Disables the specified NIC
        - `con edit {deviceID}` Enters interactive mode to configure the specified NIC.
        - `device status` Displays the current status of each NIC
    
###Netplan
    The Canonical organization, which produces Ubuntu Linux, develop Netplan as an easier way of managing network settungs compared to NetworkManager or other interfaces. Netplan consists of network configuration files that define settings, rather than using a series of commands that may vary between distributions. The files use the Yaml Ain't Markup Language (YAML) format, which is a standard structure for many **Infrastructure as Code**(IaC) utilities that centralize and streamline configuration management in large environments. Using a YAML-based configuration file makes Netplan easy to integrate into a larger automated server configuration management environment.
    some of the common `netplan` subcommands are:
        - `generate` Creates NetworkManager or system-networkd configuration files, depending on the network backend in use.
        - `try` Applies the cknfiguration to the system but allows a rollback option if the attempt fails.
        - `apply` Applies the configuration to the system
        - `info` Shows available Netplan features
        - `netplan ip` Displays IP settings
        - `status` Displays the system's current network state.

###Name Resolution Configuration
    Imagine if every website you have bookmarked or every email address in your contacts information was shown as an IP address instead of a name. this information is virtually useless to humans, who have a very difficult time recalling ling strings of numbers.
    
    **Name Resolution** maps there easy-to-remember names to difficult-to-remember IP address. It allows an administrator to specify a connection to a piece of equipment named "sales-color-printer" and the network to understand that as 192.168.2.42.
