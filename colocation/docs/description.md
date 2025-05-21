---
title: Service Description - Colocation
---
# Colocation / Service Description
The Colocation service provides a secure and reliable environment for customers to house their own physical server hardware. Customers can lease space in units within CBWS's shared, enterprise-grade colocation racks located in data center facilities operated by our trusted datacenter partners.

## Service Overview

This service allows you to deploy your servers and equipment in facilities offering robust power, cooling, and physical security. CBWS manages your colocation service within these high-quality data centers operated by our partners. It's an ideal solution for businesses requiring control over their hardware while leveraging purpose-built data center infrastructure.

The Colocation service is supported in the following Availability Zones, hosted within facilities managed by our datacenter partners:

- **Region nl-ein**
    - nl-ein-1 (NorthC Eindhoven 1)

## Key Features

* **Rack Space:** Secure space provided in Rack Units (U) within shared CBWS colocation cabinets. Customers lease space on a per-U basis according to their requirements.
* **Power:** Redundant A and B power feeds supplied to the rack, part of the partner-operated data center facility, designed for connection to customer equipment with dual power supplies.
* **Cooling:** Precision environmental control systems maintain optimal temperature and humidity for server operation within the partner-operated data center facility.
* **Physical Security:** The data center facilities, operated by our datacenter partners, feature 24/7 security personnel, CCTV surveillance, and multi-layered access controls.
* **Connectivity Options:** The Colocation service can be combined with CBWS networking services like [Public Network service](/network/description) and [Virtual Private Cloud (VPC) service](./vpc.md) to provide connectivity for your equipment (these are separate services with their own terms).
* **Remote Hands Support:** CBWS offers Remote Hands services for on-site assistance with your equipment (see details below).
* **Management Uplink:** CBWS offers a free, included, management uplink for your iDrac / iLo / IPMI secured with a VPN.

## Service Level Agreement (SLA)

The Colocation service for Power and Cooling is covered by a specific Service Level Agreement, which includes a 99.99% uptime target for these components.

For full details on these uptime targets, claim processes, remedies, and specific conditions, please refer to the [Service Level Agreement](/colocation/sla).

## Facility Access

* **24/7 Availability:** Customers can request access to their colocated equipment 24 hours a day, 7 days a week.
* **Supervised Access:** All access to the data center floor and colocation racks is supervised for security purposes, adhering to the procedures of both CBWS and our datacenter partners.
* **Access Protocol:**
    * Access should preferably be scheduled by making an appointment with CBWS personnel during standard business hours. CBWS will coordinate this access with the datacenter partner.
    * For urgent access outside business hours or when CBWS personnel are not immediately available, access can be arranged and will be supervised by the on-site data center security officers (personnel of our datacenter partner), following established security procedures. Valid identification and prior authorization, coordinated via CBWS, are required.

## Additional Services

### Remote Hands
CBWS offers Remote Hands services to assist with tasks on your colocated equipment. This service is available at a fee.

* **Services Typically Include:** Common tasks such as power cycling equipment, checking physical port status or LED indicators, connecting or disconnecting pre-labelled cables, reporting on visual observations, and other basic manual interventions as agreed upon.
* **Options and Scheduling:**
    * **Planned Remote Hands:** Must be scheduled in advance with CBWS during standard office hours (Monday to Friday, 09:00 - 17:00 CET/CEST).
    * **Emergency Remote Hands (during CBWS office hours):** Available during standard CBWS office hours (Monday to Friday, 09:00 - 17:00 CET/CEST).
    * **Emergency Remote Hands (outside CBWS office hours)**

To request Remote Hands services, please contact CBWS support. All work is performed under your specific direction and responsibility.

### Management Uplink
CBWS offers a **free** management uplink for your iDrac / iLo / IPMI interface. This connection provides a way to manage your server out-of-band, even if your server or main network connection is down or misconfigured. It's especially useful for initial setup, troubleshooting, or remote power cycling.

This uplink connects to a separate, private management network, which is different from your main network connections. You can securely access this management network by connecting to our VPN. We will provide you with the necessary IP address to pre-configure your server's management interface as part of the hardware requirements.

Please note that we **do not** guarantee uptime or network speed (throughput) for this management uplink. It is meant for basic management tasks, not for transferring large amounts of data. Also, your management uplink **does not** have access to the Public Network.

## Responsibilities

### Customer

* Provisioning, installation, and maintenance of their own server hardware, software, and any internal cabling within their allocated rack space.
* Ensuring their equipment is compatible with standard 19-inch racks and suitable for a data center environment, airflow is front-to-back and proper rails are provided.
* Adherence to CBWS policies and the specific facility policies of our datacenter partners.
* For SLA validity on power, connecting equipment with redundant power supplies to both A and B power feeds is required.

### CBWS

* Providing the agreed-upon rack space for customer equipment.
* Ensuring the delivery of power and cooling to the customer's allocated space, as provided by our datacenter partners, according to the service agreement and SLA.
* Coordinating with datacenter partners to uphold the physical security of the data center facility environment where CBWS racks are located.
* Serving as the primary point of contact for service-related inquiries, including the coordination of facility access and remote hands.
* Managing the SLA for the Colocation service components (Power and Cooling) as delivered through our datacenter partners.

## Hardware Requirements

To ensure your equipment works well with our Colocation service and for some parts of the service (like the Power SLA) to apply, your hardware must meet these requirements:

1. Your equipment must have two power supplies for backup (redundant PSUs) and be able to use both. If it doesn't, we cannot provide the Power SLA.
2. Your equipment needs two network ports set up to work together using LACP. 
3. Your equipment must have a way to manage it remote (like iDrac, iLo, IPMI, or a similar add-in card like Sipeed NanoKVM PCIE).
4. You must provide good quality sliding rails for your equipment that work smoothly.
5. Your equipment must have a motherboard that supports a standard monitor connection (VGA) and have at least two standard USB ports (Type-A).

Before the appointment to colocate the hardware, please ensure:

1. The IPv4 and IPv6 addresses is configured on the public interface, and this public interface is configured with LACP.
2. The IPv4 address is configured on the management interface.
3. Make sure you can log into your equipment without **needing internet access**, just in case. 
    - It's a good idea to test this by unplugging the internet cable before you bring it to the data center. 

## Power Right

Our data center partner uses a "**Power Right including Power Consumption**" model for electricity. This means you are not charged based on how many kilowatt-hours (kWh) of electricity you use. Instead, you pay for a specific amount of power capacity (for example, per watt or kilowatt).

This power capacity includes your actual power use. So, if you are given a "Power Right" for 115 watts, you can use that 115 watts fully for the entire month without extra charges for kWh usage. Your power usage is pooled per data center. If at any moment you use more power than what you have committed to, we will get in touch to discuss changing your contract.

Power prices are adjusted once a year in January based on current market rates.