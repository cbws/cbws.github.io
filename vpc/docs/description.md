---
title: Service Description - Virtual Private Cloud 
---
# VPC / Service Description
The Virtual Private Cloud (VPC) service offers a secure, isolated network environment for dedicated inter-server communication within the CBWS Cloud infrastructure. This service complements our Public Network services, which furnish public internet connectivity.

This service can be used independently or in conjunction with our [Public Network service](/network/description) to provide comprehensive connectivity solutions for your hosted infrastructure.

## Service Overview
While our Public Network service facilitates your servers' connection to the public internet, the Virtual Private Cloud (VPC) service enables designated servers to communicate directly and securely over an isolated private network infrastructure. Each VPC can be configured to include one or more Private Networks. A Private Network is specific to a single Availability Zone. The VPC provides routing capabilities to enable communication between these distinct Private Networks across different Availability Zones within the same region, offering enhanced flexibility and resilience.

Traffic within your Private Networks, and traffic routed between them by the VPC, is segregated from public networks and other tenants. Furthermore, this private traffic is not subject to the bandwidth limitations or metered billing associated with the Public Network service.

The service is supported on virtual servers, as well as bare metal servers and with colocation services, in the following Availability Zones:

- **Region nl-ein**
    - nl-ein-1
    - nl-ein-2

## Key Features

1. **Isolated Network Segment**: Each Private Network within a VPC constitutes a distinct Layer 2 broadcast domain (VLAN) specific to an Availability Zone. This architecture ensures robust traffic segregation.
2. **Low Latency**: Direct server-to-server connectivity within a Private Network minimizes network hops and processing overhead. Communication routed by the VPC between Private Networks in different Availability Zones also benefits from optimized, low-latency paths.
3. **Unmetered Internal Traffic**: Data transfer between servers within the same Private Network (i.e., within the same Availability Zone) is unmetered. Furthermore, data transfer routed by the VPC between different Private Networks (i.e., across Availability Zones within the same region) also does not contribute to public bandwidth quotas (as defined by the Public Network service) and incurs no additional data transfer costs.
4. **Regional Redundancy and Resilience**: By enabling the creation of Private Networks in multiple Availability Zones within the same region, and providing routing between them, the VPC service facilitates the design and deployment of highly available and fault-tolerant application architectures. This allows services to withstand the failure of an individual Availability Zone.

## Service Level Agreement (SLA)

The VPC service includes a 99.9% uptime Service Level Agreement (SLA) by default for connectivity within each Private Network per Availability Zone, and for the VPC routing functionality between Private Networks in different Availability Zones within the same region. SLAs are specific to service components and the Availability Zone(s) where they are delivered; currently, we do not offer a single, overarching SLA covering all aspects of a multi-AZ VPC deployment under one measurement.

For detailed terms, conditions, claim processes, and compensation related to this SLA, please refer to the [Virtual Private Cloud (VPC) Service - Service Level Agreement](./vpc-sla.md).

## Implementation details

Upon provisioning, servers designated for a Virtual Private Cloud are configured with access to their specified Private Network(s) within the VPC.

- **Availability Zone connectivity (Private Networks)**: Within a single Availability Zone, each Private Network in your VPC provides Layer 2 connectivity. This allows for a flat network segment across your servers in that AZ as part of that Private Network.

- **Region connectivity (VPC Routing)**: CBWS provides an interconnected private high-capacity backbone between its Availability Zones within the same region. The VPC's routing capabilities utilize this backbone to facilitate communication between your Private Networks located in different Availability Zones, based on Layer 3 routing between these subnets (the Private Networks).

### Virtual servers

For virtual servers, a dedicated virtual network interface is provisioned and assigned to the server, granting access to the designated Private Network. The maximum bandwidth available to this interface corresponds to the advertised capacity of the selected flavor.

### Physical servers

_Relevant for bare metal & colocation._

By default, for physical servers using VPC, we typically deploy combined uplinks for the Public Network service and the Virtual Private Cloud. This consolidated approach allows the total uplink capacity to be shared dynamically between public internet traffic and private VPC traffic, optimizing bandwidth utilization. Specific configurations can be discussed.

## Additional Services

### NAT Gateway
CBWS offers a highly available Network Address Translation (NAT) Gateway service for your VPC. This managed service translates private IP addresses from within your VPC to one or more **dedicated public IP addresses**, enabling outbound internet connectivity for your resources. The NAT Gateway service also **supports port forwarding (DNAT)**, allowing specific inbound connections from the internet to designated private IP addresses and ports within your VPC.

This allows your instances within Private Networks to access the internet for updates, patches, or communication with external services, without requiring individual public IP addresses assigned directly to them. This enhances security by limiting direct inbound internet exposure and simplifies IP address management within your VPC. The NAT Gateway can be configured to serve multiple Private Networks within your VPC.

## Combining with Public Network

While this service provides private networking, our [Public Network service](/network/description) can be used simultaneously (e.g., via the NAT Gateway or by assigning public IPs directly to select resources) to allow controlled access to and from the public internet.