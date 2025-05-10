---
title: Service Level Agreement - Colocation 
---
# Colocation / SLA

This document outlines the Service Level Agreement (SLA) specific to the CBWS Colocation service. This SLA is effective from the delivery date of the Colocation service and remains in effect as long as the service is supplied by CBWS to the customer.

This SLA specifically covers the availability of Power and Cooling provided as part of the Colocation service.

## Availability Target

CBWS commits to the following availability targets for the core infrastructure components of the Colocation service, calculated by CBWS on a calendar month basis (considering the total number of minutes in that month) based on measurements provided by our datacenter partner:

* **Power Availability:** 99.99% uptime, measured per rack in which the customer's allocated rack space resides.
* **Cooling Availability:** 99.99% uptime, measured per data hall or designated cooling zone within the Availability Zone.

### SLA Prerequisites for Power Availability
To be eligible for the Power Availability SLA, customer equipment **must** be correctly connected to, and able to draw power from, **both** the A and B power feeds provided by CBWS. This requires customer equipment to have redundant power supplies. If equipment is not demonstrably connected to and utilizing both A and B power feeds, the Power Availability SLA will not apply.

## Downtime Measurement

Downtime measurement for both Power and Cooling is based on data from the monitoring systems operated by our datacenter partner at the facility, which is then verified by CBWS.

* **Power Downtime:** Power Downtime, for SLA purposes, is registered if there is a simultaneous loss of electrical power on **both** the A and B power feeds to the customer's allocated rack space. This applies to failures affecting the power delivery up to the customer's outlets, unless such failures are covered by an exclusion in this SLA. Each minute of such verified downtime contributes to the monthly Power Availability calculation per rack.
* **Cooling Downtime:** Cooling Downtime is registered if the ambient temperature or other critical environmental parameters within the data hall area housing the customer's rack deviate from the agreed operational range (as specified in service documentation or industry standards for data centers) for a sustained period, unless such deviations are covered by an exclusion in this SLA. Each minute of such verified deviation contributes to the monthly Cooling Availability calculation per hall/zone.

## SLA Claim Process

* **Customer Responsibility:** Customers are responsible for monitoring their own equipment and identifying potential downtime for Power or Cooling that may qualify for an SLA claim. CBWS does not proactively issue SLA credits or report on general SLA adherence for individual customer services.
* **Initiating a Claim:** To make an SLA claim related to Power or Cooling availability, the customer must open a support ticket with CBWS through the official support channels (e.g., by emailing support@cbws.nl).
* **Claim Deadline:** The support ticket detailing the experienced downtime (including specific component affected - Power or Cooling, times, affected equipment, and services) must be submitted **after** the calendar month in which the downtime occurred, and no later than **14 calendar days following the end of that month**. Claims submitted outside this period will not be eligible for remedies under this SLA.
* **Verification:** All SLA claims will be verified against CBWS's records and the monitoring data provided by our datacenter partner.

## Remedies for Non-Achievement

In the event the 99.99% availability target for either Power or Cooling (as measured per rack or per hall/zone respectively) is not met in a given calendar month for the Colocation service in an Availability Zone, customers are entitled to Service Credits as detailed below.

Additionally, CBWS addresses service improvement as follows:

1.  **Reason For Outage (RFO):** Following a verified SLA breach, CBWS may provide the customer with a Reason For Outage (RFO) statement detailing the cause of the service unavailability. This RFO will outline a plan to improve service stability and prevent future occurrences.
2.  **Service Credits (Compensation):**
    * **Eligibility:** If the Power Availability (per rack) or Cooling Availability (per hall/zone) for the Colocation service experiences a total downtime exceeding 0.01% of the total minutes in a calendar month (meaning the 99.99% uptime target for that specific component was not met), the customer is eligible to request service credits.
    * **Credit Amount:** Eligible compensation is 10% of the monthly fees paid for the specifically affected Colocation service (i.e., the fee for the rack space/unit impacted by the failure of the specific component) in the impacted AZ for that month, with a maximum at €1,000.00 per month.
    * **Application of Credits:** Approved service credits will be applied on the customer's next monthly invoice, deducting from the total amount payable for the services.
    * Service credits are the sole and exclusive monetary remedy for any failure by CBWS to meet the availability targets for Power or Cooling.

## Exclusions

This SLA for the Colocation service (Power and Cooling) does not apply to any unavailability, suspension, or termination of service performance for these components:

* That results from a suspension described in the CBWS Terms of Service.
* Caused by factors outside of CBWS's or its datacenter partner's reasonable control, including any force majeure event.
* That results from any actions or inactions of the customer or any third party acting on the customer's behalf, including but not limited to:
    * Failure to connect equipment to both A and B power feeds as per the "SLA Prerequisites for Power Availability".
    * Customer equipment exceeding allocated power draw limits or causing electrical faults.
    * Misconfiguration or failure of customer-owned equipment (servers, internal PDUs, etc.), including failure of customer's redundant power supplies when one power feed remains active.
    * Customer-induced obstructions to airflow or other actions adversely impacting the local operating environment.
* That results from any scheduled maintenance communicated in advance by CBWS or its datacenter partner.
* Power interruptions affecting single-corded customer equipment, as such equipment cannot natively meet the Power Availability SLA prerequisite requiring connection to both A and B power feeds.

### Customer Support
Support requests can be made via:

* **Email:** support@cbws.nl
* **Phone:** +31 (0)85 743 0374

Operating hours are Monday to Friday, 09:00 - 17:00 (CET/CEST). Email requests are responded to within 24 hours of receipt during these times (this reaction time is an effort obligation). Phone support is available during operating hours.

## Concluding Terms

These terms define the Service Level Agreement specifically for Power and Cooling aspects of the CBWS Colocation service. The general CBWS Terms of Service also apply to the use of all CBWS services and govern aspects not explicitly covered in this SLA.