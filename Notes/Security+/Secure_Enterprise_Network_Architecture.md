## Enterprise Network Architecture

Secure network infrastucture and application architecture are put there to support secure business
workflows. A workflow is a series of tasks that a business needs to perform, such as accepting
customer orders from a web store. Remember that security means the attributes of confidentiality,
integrity, and availability.

Analyzing the systems involved in provisioning email can ilustrate the sorts of architecture
desicions that need to be made:
    Access
    Email mailboc server
    Mail transfer server

Network Infrastructure:
    A network is comprised of nodes and liks. 
    There are two types of nodes. A host node is one that initiates data transfers. Hosts are
    usually either servers or client. An intermediary node forwards traffic around the network.
    
    Each network node must be identifiable via a unique address.

OSI Model layers
    - Application
    - Presentation
    - Session
    - Transport
    - Network
    - Datalink
    - Physical

An on-premises network is one installed to a single site and operated by a single company. This can
also be referred to as an enterprise local area network (LAN).

Layer 3 switches also do routing, as well as all the basic stuff they do in the second layer.

Layer 3 forwarding, or routing, applies a logical addressing scheme to identify each network. Layer
3 architecture represents the logical segmentation of networks and the creation of networks within
networks, or subnetworks (subnets). Each subnet is a separate broadcast domain. At layer 3, nodes
are identified by Internet Protocol (IP) addresses and links are identified by routes.

In the hierarchical network architecture, each access block can be designated as a separate IP
subnet. This system of layer 3 logical addressing makes it easier to write access control rules for
what traffic is allowed to flow between blocks or zones.

The network attack surface is all the points at which a threat actor could gain access to hosts and
services. It is helpful to use the layer model to analyze the potential attack surface:
    Layer 1/2 - allows unauthorized hosts to connect to wall ports or wireless networks and
    communicate with hosts within the same broadcast domain.
    
MAC Filtering and MAC Limiting:
    Configuring MAC Filtering means a switch port only permits certain MAC addresses to connect.
    This can be done by creating a list of valid MAC addresses or by specifying a limit to the
    number of permitted addresses.
    

