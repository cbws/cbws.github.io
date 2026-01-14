---
title: Service Description - Public Network 
---
# Public Network / Service Description
The Public Network service provides your machines with robust and reliable public internet connectivity. CBWS manages the underlying network infrastructure, including transit provider relationships, Internet Exchange (IX) peering, and core routing, to ensure optimal performance and availability.

This service can be used independently or in conjunction with our [Virtual Private Cloud (VPC) service](/vpc/description) to provide comprehensive connectivity solutions for your hosted infrastructure.

## Service Overview

This service equips your machines with access to the public internet, enabling them to send and receive traffic globally. We focus on providing high-quality bandwidth with diverse routing paths.

The Public Network service is supported in the following Availability Zones, hosted within facilities managed by our datacenter partners:

- **Region nl-ein**
    - nl-ein-1
    - nl-ein-2

## Key Features

* **Managed Public Connectivity:** CBWS handles all aspects of upstream internet connectivity, including BGP routing, peering agreements, and capacity management.
* **Resilient Infrastructure:** Our network is designed for high availability with redundant core components and multiple upstream providers.
* **Scalable Bandwidth Options:** Choose from various billing models and uplink capacities to match your specific needs.
* **Full Capacity Utilization:** CBWS ensures you can utilize the full provisioned capacity of your public network uplink.

## Service Level Agreement (SLA)

The Public Network service includes a 99.9% uptime Service Level Agreement (SLA) by default for network connectivity per Availability Zone. Currently, we do not offer a general SLA that covers services across multiple Availability Zones; SLAs are specific to the Availability Zone where the service is delivered.

For detailed terms, conditions, claim processes, and compensation related to this SLA, please refer to the [Service Level Agreement](/network/sla).

## Bandwidth Billing

We offer the following billing models for your public internet traffic:

* **Mbit/s (95th Percentile):** This model is based on your sustained bandwidth usage. We measure your inbound and outbound traffic separately every 5 minutes. At the end of the billing period, the top 5% of these measurements are discarded, and you are billed based on the next highest value (the 95th percentile). This model is ideal for bursty traffic patterns.
* **Flat Rate:** A fixed monthly fee for a committed bandwidth capacity. This provides predictable costs for consistent high-bandwidth usage.
* **TB Bandwidth Usage (Traffic Packs):** Pay based on the total amount of data transferred (in Terabytes) over the public network. Bandwidth packs are purchased beforehand, and overusage is calculated if the allowance is exceeded. This model is suitable for applications with predictable data transfer volumes.

## Uplinks

The uplink capacity differs depending on whether the service is for virtual or bare metal machines.

### Virtual machines

The maximum uplink capacity for a virtual machine is as advertised with the selected machine type. This capacity **is not** shared between public internet traffic and any [Virtual Private Cloud (VPC) service](/vpc/description) traffic.

### Bare metal machines

_Relevant for bare metal & colocation._

The following dedicated physical uplink capacities are available for connecting your physical machines to our network infrastructure:

* **1 Gbit/s:** Available at nl-ein-1
* **10 Gbit/s:** Available at nl-ein-1
* **25 Gbit/s:** Available at nl-ein-2

The choice of uplink type will typically depend on the machine or colocation package selected. For bare metal machines, Link Aggregation Control Protocol (LACP) is always deployed, bundling them into a single logical channel for increased throughput and redundancy. This total aggregated capacity **is** shared between public internet traffic and any [Virtual Private Cloud (VPC) service](/vpc/description) traffic.

## Additional Services

### IPv6 Subnet
An IPv6 subnet (/64 or as agreed) is provided by default with all Public Network uplinks, enabling IPv6 connectivity for your services.

### IPv4 Addresses
Individual IPv4 addresses can be provided for your Public Network uplink or for use with [our managed NAT gateway](/vpc/description/#nat-gateway) if required. For requests involving a significant number of IPv4 addresses, CBWS may ask for justification of their use, in line with RIPE policies.

### IPv4 Subnets
If your project requires a dedicated range of IPv4 addresses, IPv4 subnets (e.g., /29, /28) can be allocated to your Public Network uplink. Allocation of IPv4 subnets is subject to justification based on your use-case and RIPE policies.

### IP Announcement (BYOIP)
If you have your own Autonomous System Number (ASN) and IP address ranges (IPv4 or IPv6), CBWS can announce these from our network edge. This makes your own IP addresses usable over your Public Network connection with us.

## Combining with Virtual Private Cloud (VPC)

While this service provides public internet access, our [Virtual Private Cloud (VPC) service](/vpc/description) can be used simultaneously to create an isolated, high-speed network for communication *between* your machines. This allows public-facing services to run alongside secure, high-performance backend communication, with internal VPC traffic not incurring public bandwidth charges.
