---
title: Service Level Agreement - DNS 
---
# DNS / SLA

This document outlines the Service Level Agreement (SLA) specific to the CBWS managed DNS service. This SLA is effective from the delivery date of the DNS service and remains in effect as long as the service is supplied by CBWS to the customer.

## Availability Target

* CBWS commits to providing the DNS service with **99.9% uptime** for DNS query resolution.
* This availability is measured by CBWS on a calendar month basis, considering the total number of minutes in that month.

## Recovery Objectives

* **Recovery Point Objective (RPO):** Due to the heavily redundant, distributed nature of our DNS cluster setup, our RPO is designed to ensure almost no data loss under normal operating conditions. In a worst-case disaster scenario, the maximum potential data loss is up to 24 hours, and this is exclusively restricted to DNS records.
* **Recovery Time Objective (RTO):** Our RTO is strictly based on maintaining our 99.9% uptime commitment, meaning total permitted downtime for recovery operations will not exceed approximately 43.8 minutes in a standard 30-day billing month.

## Downtime Measurement

* CBWS measures DNS service availability by continuously monitoring DNS query responses from multiple external and internal vantage points against our distributed name server cluster.
* Downtime is registered if there is a verified total loss of DNS query resolution across the entire cluster due to a failure solely within CBWS's managed infrastructure. Downtime begins when CBWS confirms such a service interruption (or is reasonably made aware of one by a customer) and ends when DNS query resolution is restored. Each minute of such verified downtime contributes to the monthly calculation.

## SLA Claim Process

* **Customer Responsibility:** Customers are responsible for monitoring their own services and identifying potential downtime that may qualify for an SLA claim. CBWS does not proactively issue SLA credits or report on general SLA adherence for individual customer services.
* **Initiating a Claim:** To make an SLA claim related to service availability, the customer must open a support ticket with CBWS through the official support channels (e.g., by emailing support@cbws.nl).
* **Claim Deadline:** The support ticket detailing the experienced downtime must be submitted **after** the calendar month in which the downtime occurred, and no later than **14 calendar days following the end of that month**. Claims submitted outside this period will not be eligible for remedies under this SLA.
* **Verification:** All SLA claims will be verified against CBWS's monitoring data and service logs.

## Remedies for Non-Achievement

In the event the 99.9% availability target for the DNS service is not met in a given calendar month, customers may be entitled to the following remedies:

1.  **Reason For Outage (RFO):** CBWS may provide the customer with a Reason For Outage (RFO) statement detailing the cause of the service unavailability. This RFO will outline a plan to improve service stability and prevent future occurrences.
2.  **Service Credits (Compensation):**
    * **Eligibility:** If the DNS service experiences a total downtime exceeding 0.1% of the total minutes in a calendar month (meaning the 99.9% uptime target was not met), the customer is eligible to request service credits.
    * **Credit Amount:** Eligible compensation is 10% of the monthly fees paid for the specifically affected DNS service for that month, with a maximum at €1,000.00 per month.
    * **Application of Credits:** Approved service credits will be applied on the customer's next monthly invoice, deducting from the total amount payable for the services.
    * Service credits are the sole and exclusive monetary remedy for any failure by CBWS to meet the availability target.

## Exclusions

This SLA for the DNS service does not apply to any unavailability, suspension, or termination of service performance:

* That results from a suspension described in the CBWS Terms of Service.
* Caused by factors outside of CBWS's reasonable control, including any force majeure event, or widespread Internet routing issues beyond the CBWS network edge.
* That results from any actions or inactions of the customer, such as misconfigured DNS records, invalid zone files, or accidental deletion of records by the customer.
* That results from any scheduled maintenance communicated in advance by CBWS.
* That results from customer-initiated security measures or abuse mitigation actions.

## Concluding Terms

These terms define the Service Level Agreement specifically for the CBWS DNS service. The general CBWS Terms of Service also apply to the use of all CBWS services and govern aspects not explicitly covered in this SLA.

### Customer Support
Support requests can be made via:

* **Email:** support@cbws.nl
* **Phone:** +31 (0)85 743 0374

Operating hours are Monday to Friday, 09:00 - 17:00 (CET/CEST). Email requests are responded to within 24 hours of receipt during these times (this reaction time is an effort obligation). Phone support is available during operating hours.