## Explore Packet Capture Tools
---
Wireshark:
		open-source graphical packet capture utility, with installer packages for most operating
		systems. Having chosen the interfaces to listen on, the output is displayed in a three-pane
		view, with the top pane showing each frame, the bottom-left pane showing the fields from the
		currently selected frame, and the bottom-right pane showing the raw data from the frame in hex
		and ASCII.
		
tcpdump:
		**tcpdumb** is a command line packet capture utility for Linux,though a version of the program
		called windump is available for Windows. The basic syntax for the command is `tcpdumb -i eth`,
		where `eth` represents the interface to listen on.
		
"
The PCAP file format has some limitations, which has led to the development of PCAP Next Generation
(PCAPNG). Wireshark now uses PCAPNG by default, and tcpdump can process files in the new format too.
"

---
## Explore Endpoint Detection and Response (EDR)
EDR is an important security solution designed to provide proactive capabilities by combining
traditional endpoint security with advanced analytics to detect and respond to suspicious activity.

Advantages offered by EDR Solutions:
		- Detecting Malicious Activity 
		- Improved incident response 
		- Proactive Prevention
		- Risk Assessment
		- Incident Investigation

**EDR Platform Capabilities**
		- Malware Detection
		- URL Filtering
		- Honeypots
		- Monitoring 
		- Orchestration
		- Detect Emerging Threats

---
## Use Common Analysis Tools
Whois:
		Whois is a look-ups  service that provides information about a domain name or IP
		address, email address, phone number, and other information about the person or entity
		associated with a domain name or IP address.
		
AbuseIPDB:
		AbuseIPDB is a very popular website used by analysts to investigate suspicious traffic. The site
		also provides an API for automation services to integrate with SOAR platforms.
		A securiy analyst can use AbuseIPDB to identify malicious network traffic or suspicious emails
		by submitting an IP address to the platform's database search tool.
		
Strings command:
		The strings command extracts and displays viewable characters stored within a binary. Using the
		strings command helps to reveal different characteristics of a binary, including how it
		operates.
		
Virus Total:
		provides a free service designed to inspect files and URLs using over 70 antimalware scanners
		and domain blocklisting services. The website provides a comprehensive report describing any
		malicious content, including the type of malware, malware names provided by various antimalware
		vendors, indicators, file hashes , different file names observed in the wild, relationships to
		domains, IP addresses and files, behavioral characteristics, and community discussion.
		
---
## Sandboxing for Malware Analysis
**Sandboxing** is a technique that isolates untrusted data in a closed virtual environment to
conduct tests and analyze the data for threats and vulnerabilities. Sandbox environments
intentionally limit interfacing with the host environments to maintain the hosts; integrity. 

To effectively analyze malware, sandboxes should provide the following features:
		- Monitor any system changes without direct user interaction
		- Execute known malware files and monitor for changes to processes and services
		- Monitor network sockets for attempted connections, such as using DNS for Command & Control
		- Monitor all system calls and API calls made by programs
		- Monitor program instructions between system and API calls
		- Take periodic snapshots of the environment
		- Record file creation/deletion during the malware's execution 
		- Dump the virtual machine's memory at key points during execution.
			
Joe Sandbox is a malware analysis platform that inspects executable files, suspicious URLs, and many
other features. It offers easy access to behavior analysis, sinature detection, and sandboxing
technology to identify and analyze malicious files in a safe and controlled environment.

---

## Understand Security Orchestration Automation and Response (SOAR)
SOAR is designed to automate some of the routine tasks ordinarily performed by security personnel in
response to a security incident.

The basis of SOAR is to scan security and threat intelligence data collected from multiple sources
within the enterprise and then analyze it using various techniques defined via playbooks. A SOAR can
also assist with provisioning tasks, such as creating and deleting user accounts, making shares
available, or launching VMs from templates. The SOAR will use technologies such as cloud and SDN/SDV
APIs, orchestration tools, and cyber threat intelligence (CTI) feeds to integrate the different
systems it manages. It will also leverage technologies such as automated malware signature creation
and user and entity behaviour analytics (UEBA) to detect and identify threats.
