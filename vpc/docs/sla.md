---
title: Service Level Agreement - Virtual Private Cloud 
---
# VPC / SLA

This document outlines the Service Level Agreement (SLA) specific to the CBWS Virtual Private Cloud (VPC) service. This SLA is effective from the delivery date of the VPC service and remains in effect as long as the service is supplied by CBWS to the customer.

## Availability Target

* CBWS commits to providing the VPC service with **99.9% uptime** per Availability Zone (AZ).
* This availability is measured by CBWS on a calendar month basis, considering the total number of minutes in that month.

## Downtime Measurement

* CBWS measures VPC service availability by continuously monitoring connectivity between various critical internal points within its network infrastructure essential for delivering the VPC service. This internal monitoring is performed every minute from multiple perspectives within the CBWS network.
* Downtime is registered if there is a verified loss of network connectivity for a customer's VPC (e.g., between resources within the same VPC in an AZ, or between the VPC and other directly interconnected CBWS services within the same AZ as per service agreement), due to a failure solely within CBWS's network infrastructure supporting the VPC. Downtime begins when CBWS confirms such a service interruption (or is reasonably made aware of one by a customer) and ends when the affected VPC connectivity is restored. Each minute of such verified downtime contributes to the monthly calculation.

## SLA Claim Process

* **Customer Responsibility:** Customers are responsible for monitoring their own services and identifying potential downtime that may qualify for an SLA claim. CBWS does not proactively issue SLA credits or report on general SLA adherence for individual customer services.
* **Initiating a Claim:** To make an SLA claim related to VPC service availability, the customer must open a support ticket with CBWS through the official support channels (e.g., by emailing support@cbws.nl).
* **Claim Deadline:** The support ticket detailing the experienced downtime must be submitted **after** the calendar month in which the downtime occurred, and no later than **14 calendar days following the end of that month**. Claims submitted outside this period will not be eligible for remedies under this SLA.
* **Verification:** All SLA claims will be verified against CBWS's internal monitoring data and service logs.

## Remedies for Non-Achievement

In the event the 99.9% availability target for the VPC service is not met in a given calendar month, customers may be entitled to the following remedies:

1.  **Reason For Outage (RFO):** CBWS may provide the customer with a Reason For Outage (RFO) statement detailing the cause of the service unavailability. This RFO will outline a plan to improve service stability and prevent future occurrences.
2.  **Service Credits (Compensation):**
    * **Eligibility:** If the VPC service in a specific Availability Zone experiences a total downtime exceeding 0.1% of the total minutes in a calendar month (meaning the 99.9% uptime target was not met), the customer is eligible to request service credits.
    * **Credit Amount:** Eligible compensation is 10% of the monthly fees paid for the specifically affected VPC service in the impacted AZ for that month, with a maximum at €1,000.00 per month.
    * **Application of Credits:** Approved service credits will be applied on the customer's next monthly invoice, deducting from the total amount payable for the services.
    * Service credits are the sole and exclusive monetary remedy for any failure by CBWS to meet the availability target.

## Exclusions

This SLA for the VPC service does not apply to any unavailability, suspension, or termination of service performance:

* That results from a suspension described in the CBWS Terms of Service.
* Caused by factors outside of CBWS's reasonable control, including any force majeure event.
* That results from any actions or inactions of the customer or any third party acting on the customer's behalf (e.g., misconfiguration of network ACLs, security groups, or routing within the VPC by the customer).
* That results from the customer's applications, operating systems, software, or other technology, and/or third-party equipment, software, or other technology not within CBWS's direct control (e.g., issues within customer-managed virtual machines or appliances).
* That results from any scheduled maintenance communicated in advance by CBWS.
* That results from customer-initiated security measures, traffic filtering, or abuse mitigation actions.

## Concluding Terms

These terms define the Service Level Agreement specifically for the CBWS Virtual Private Cloud (VPC) service. The general CBWS Terms of Service also apply to the use of all CBWS services and govern aspects not explicitly covered in this SLA.

### Customer Support
Support requests can be made via:   

* **Email:** support@cbws.nl
* **Phone:** +31 (0)85 743 0374

Operating hours are Monday to Friday, 09:00 - 17:00 (CET/CEST). Email requests are responded to within 24 hours of receipt during these times (this reaction time is an effort obligation). Phone support is available during operating hours.