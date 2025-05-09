# VPC Service Description
The Virtual Private Cloud (VPC) service offers a secure, isolated network environment for dedicated inter-server communication within the CBWS Cloud infrastructure. This service complements our Public Networking services, which furnish public internet connectivity.

This service can be used independently or in conjunction with our [Public Network service](/network/description) to provide comprehensive connectivity solutions for your hosted infrastructure.

# Service overview
While our Public Networking service facilitates your servers' connection to the public internet, the Virtual Private Cloud (VPC) service enables designated servers to communicate directly and securely over an isolated private network infrastructure. Each VPC can be configured to include one or more Private Networks. A Private Network is specific to a single Availability Zone. The VPC provides routing capabilities to enable communication between these distinct Private Networks across different Availability Zones within the same region, offering enhanced flexibility and resilience.

Traffic within your Private Networks, and traffic routed between them by the VPC, is segregated from public networks and other tenants. Furthermore, this private traffic is not subject to the bandwidth limitations or metered billing associated with the Public Networking service.

The service is supported on virtual servers, as well as bare metal, colocation and racks in the following Availability Zones:

- **Region nl-ein**
    - nl-ein-1
    - nl-ein-2

# Key technical features

1. **Isolated Network Segment**: Each Private Network within a VPC constitutes a distinct Layer 2 broadcast domain (VLAN) specific to an Availability Zone. This architecture ensures robust traffic segregation.
2. **Low Latency**: Direct server-to-server connectivity within a Private Network minimizes network hops and processing overhead. Communication routed by the VPC between Private Networks in different Availability Zones also benefits from optimized, low-latency paths.
3. **Unmetered Internal Traffic**: Data transfer between servers within the same Private Network (i.e., within the same Availability Zone) is unmetered. Furthermore, data transfer routed by the VPC between different Private Networks (i.e., across Availability Zones within the same region) also does not contribute to public bandwidth quotas (as defined by the Public Networking service) and incurs no additional data transfer costs.
4. **Regional Redundancy and Resilience**: By enabling the creation of Private Networks in multiple Availability Zones within the same region, and providing :routing between them, the VPC service facilitates the design and deployment of highly available and fault-tolerant application architectures. This allows services to withstand the failure of an individual Availability Zone.

# Implementation details

Upon provisioning, servers designated for a Virtual Private Cloud are configured with access to their specified Private Network(s) within the VPC.

- **Availability Zone connectivity**: Within a single Availability Zone, the VPC service provides Layer 2 connectivity for each Private Network. This allows for a flat network segment across your servers in that AZ as part of that Private Network.

- **Region connectivity**: CBWS provides an interconnected private high capacity backbone between its Availability Zones within the same region. This backbone, _in conjunction with the VPC's routing capabilities_, facilitates communication between Private Networks located in different Availability Zones, based on Layer 3 routing between these subnets (the Private Networks).

## Virtual servers

For virtual servers, a dedicated virtual network interface is provisioned and assigned to the server, granting access to the designated Private Network. The maximum bandwidth available to this interface corresponds to the advertised capacity of the selected flavor.

## Physical servers

_Relevant for bare metal & colocation._

By default, for physical servers, we deploy combined uplinks for the Public Networking service and the Virtual Private Cloud. This consolidated approach allows the total uplink capacity to be shared dynamically between public internet traffic and private VPC traffic, optimizing bandwidth utilization.
