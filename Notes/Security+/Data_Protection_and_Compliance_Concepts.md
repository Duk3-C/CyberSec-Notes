## Data Classification and Compliance

Data Types:
    Regulated data refers to specific categories of information subject to legal or regulatory
    requirements regarding their handling, storage, and protection. 
    Trade secret data refers to valuable, confidential information that gives a business a
    competitive advantage. Trade secrets encompass much nonpublic, proprietary information,
    including formulas, processes, methods, techiniques, customer lists, pricing information,
    marketing strategies, and other business-critical data. 

Data classification and typing schemas tag data assets so that they can be managed through the
information lifecycle. A data classification schema is a decision tree for applying one or more tags
or labels to each data asset. Many data classification schemas are based on the degree of
confidentiality required:
    - Public (unclassified)
    - Confidential
    - Secret
    - Top Secret

Data Sovereignty refers to a jurisdiction preventing or restricting processing and storage from
taking place on systems that do not physicallt reside within that jurisdiction.

Geographic access requirements fall into two different scenarios:
    - Storage locations might have to be carefully selected to mitigate data sovereignty issues.
    Most cloud providers allow a choice of datacenter for processing and storage, ensuring that
    information is not illegally transferred from a particular privacy jurisdiction without consent.
    
Privacy data refers to personally identifiable or sensitive information associated with an
individual's personal, financial, or social identity, including data that, if exposed or mishandled,
could infringe upon an individual's privacy rights. 

Both privacy data and confidential data are subject to legal and ethical considerations.
Organizations must comply with relevant laws and regulations, such as data protection and privacy
laws, to safeguard both data types. However, there are also notable differences between privacy data
and confidential data.

A data breach occurs when information is read, modified, or deleted without authorization. "Read" in
this sense can mean either seen by a person  or transferred to a network or storage media. A data
breach is the loss of any type of data (but notably corporate information and intellectual
property), while a privacy breach refers specially to loss or disclosure of personal and sensitive
data.

A data or privacy breach can have severe organizational consequences:
    - Reputation damage
    - Identity theft 
    - Fines
    - IP theft

Internal and external compliance reporting aim to assess and disclose an organization;s compliance
status, but they differ in scope, audience, and purpose. Internal compliance reporting primarly
serves internal stakeholders, focuses on operational details, and supports internal decision-making.

Classifying data as "at rest", "in motion", and "in use" is crucial for effective data protection
and security measures. By analyzing data based on its state, organizations can tailor security
measures and controls to address the specific risks and requirements associated with each data
state. This classification helps organizations identify vulnerabilities, prioritize security
investments, and ensure appropriate safeguards to protect sensitive data throughout its lifecycle.
It also facilitates compliance with data protections regulations and industry best practices.

Data at rest - this state means that the data is in some sort of persistent storage media. Examples
of types of data that may be at rest include financial information stored in databases, archived
audiovisual media, operatinal policies and other management documents, system configuration data,
and more.

Data in transit (or data in motion) - This is the state when data is transmitted over a network.
Examples of types of data that may be in transit include website traffic, remote access traffic,
data being synchronized between cloud repositories, and more. In this state, data can be protected
by a transport encryption protocol, such as TLS or IPSec.

Data in use (or data in processing) - this is the state when data is present in volatile memory,
such as system RAM or CPU registers and cache. Examples of types of data that may be in use include
documents open in a word processing application, database data that is currently being modified,
event logs being generated while an operating system is running, and more.
