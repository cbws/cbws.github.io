---
title: Service Description - DNS 
---
# DNS / Service Description

The CBWS DNS service provides a highly available, managed, and distributed Domain Name System (DNS) cluster to ensure your domains and applications are quickly and reliably reachable from anywhere in the world. 

By leveraging a distributed architecture, we manage the underlying complexity of DNS propagation, redundancy, and security, allowing you to focus on building your applications.

## Service Overview

Our managed DNS service distributes your DNS records across a redundant cluster of authoritative name servers. This architecture ensures high availability, extremely low query latency, and robust protection against localized network failures or infrastructure outages.


The DNS service is integrated seamlessly with the broader CBWS ecosystem, making it easy to manage your domain routing alongside your Virtual Private Clouds, Public Networks, and compute instances.

## Key Features

* **Distributed & Redundant Cluster:** Your DNS zones are replicated across a distributed cluster, ensuring that if one node fails, others seamlessly pick up the query load without interruption.
* **High Availability & Reliability:** Designed from the ground up to prevent single points of failure, ensuring your applications remain discoverable. 
* **Minimal Data Loss (RPO)**: Thanks to our replicated and highly redundant setup, we strive for almost no data loss. In the unlikely worst-case scenario, our Recovery Point Objective (RPO) is a maximum of 24 hours, and any potential loss is strictly limited to DNS records and zone configurations.
* **Rapid Recovery (RTO):** Our Recovery Time Objective (RTO) is strictly aligned with our 99.9% uptime guarantee, ensuring any service restoration happens within the allowed downtime window.

## Service Level Agreement (SLA)

The DNS service includes a 99.9% uptime Service Level Agreement (SLA) for DNS query resolution. For detailed terms, conditions, claim processes, and compensation related to this SLA, please refer to the [Service Level Agreement](/dns/sla).

## Getting Started

You can manage your DNS zones and records directly via the CBWS DNS portal, request access via email (support@cbws.nl).