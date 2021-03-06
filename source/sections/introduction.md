# Introduction

Odyssey Science Innovations, LLC, doing business as Provata Health ("Provata Health") is committed to ensuring the confidentiality, privacy, integrity, and availability of all electronic protected health information (ePHI) it receives, maintains, processes and/or transmits on behalf of its Customers. Provata Health strives to maintain compliance, proactively address information security, mitigate risk for its Customers, and assure known breaches are completely and effectively communicated in a timely manner. The following documents address core policies used by Provata Health to maintain compliance and assure the proper protections of infrastructure used to store, process, and transmit ePHI for Provata Health Customers.

Provata Health services include the provision of a secure and compliant cloud-based digital health platform. 

## Software as a Service (SaaS)

SaaS Customers utilize Provata Health's hosted web-based platform and applications (colletively, the "Provata Health Platform"). Provata Health makes every effort to reduce the risk of unauthorized disclosure, access, and/or breach of PaaS Customer data through network (firewalls, dedicated IP spaces, etc) and server settings (encryption at rest and in transit, OSSEC throughout the Platform, etc). Applications are compliant API-driven services that are offered as part of the Provata Health Platform. There may be third party add-on services available as part of the Provata Health Platform. These 3rd party, or Partner, Services will be fully reviewed by Provata Health to assure they do not have a negative impact on Provata Health's information security and compliance posture.

## Compliance Inheritance

Provata Health signs business associate agreements (BAAs) with Covered Entities and with its subcontractors, partners, vendors, and any other service providers that may receive, provide, use, transmit, or otherwise have access to PHI. These BAAs outline each party's obligations, as well as liability in the case of a breach. In providing infrastructure and managing security configurations that are a part of the technology requirements that exist in HIPAA and HITRUST, as well as future compliance frameworks, Provata Health manages various aspects of compliance for Customers. In doing so, Provata Health helps Customers achieve and maintain compliance, as well as mitigates Customers risk.

Certain aspects of compliance cannot be inherited. Because of this, Provata Health Customers, in order to achieve full compliance or HITRUST Certification, must implement certain organizational policies. These policies and aspects of compliance fall outside of the services and obligations of Provata Health.

Below are mappings of HIPAA Rules to Provata Health controls and a mapping of what Rules are inherited by Customers, both PaaS Customers and Add-on Customers.

## Provata Health Organizational Concepts

The physical infrastructure environment is hosted at [Amazon Web Services](https://aws.amazon.com/) (AWS). The network components and supporting network infrastructure are contained within the AWS infrastructure and managed by AWS. Provata Health does not have physical access into the network components. The Provata Health environment consists of Cisco firewalls, Apache and nginx web servers, Dropwizard Java application servers, Percona and PostgreSQL database servers, Logstash logging servers, Linux Ubuntu monitoring servers, Salt configuration management server, OSSEC IDS services, Docker containers, and developer tools servers running on Linux Ubuntu.

Within the Provata Health Platform on AWS, all data transmission is encrypted and all hard drives are encrypted so data at rest is also encrypted; this applies to all servers - those hosting Docker containers, databases, APIs, log servers, etc. Provata Health assumes all data *may* contain ePHI, and provides appropriate protections based on that assumption.

The data and network segmentation mechanism differs depending on the primitives offered by the underlying cloud provider infrastructure:

* Within AWS, hosted load balancers segment data across dedicated Virtual Private Clouds.

The result of segmentation strategies employed by Provata Health effectively create RFC 1918, or dedicated, private segmented and separated networks and IP spaces, for each PaaS Customer and for Platform Add-ons.

Additionally, IPtables is used on each each server for logical segmentation. IPtables is configured to restrict access to only justified ports and protocols. Provata Health has implemented strict logical access controls so that only authorized personnel are given access to the internal management servers. The environment is configured so that data is transmitted from the load balancers to the application servers over an SSL encrypted session.

In the case of Platform Add-ons, once the data is received from the application server, a series of Application Programming Interface (API) calls is made to the database servers where the ePHI resides. The ePHI is separated into PostgreSQL and Percona databases through programming logic built, so that access to one database server will not present you with the full ePHI spectrum.

The bastion host, Apache web server, Dropwizard application servers are externally facing and accessible via the Internet. The database servers, where the ePHI resides, are located on the internal Provata Health network and can only be accessed directly over an SSH connection through the bastion host. The access to the internal database is restricted to a limited number of personnel and strictly controlled to only those personnel with a business justified reason. Remote access to the internal servers is not accessible except through the load balancers and bastion host.

All Platform Add-ons and operating systems are tested end-to-end for usability, security and impact prior to deployment to production.

## Version Control

Policies were last updated July 13th, 2016.
