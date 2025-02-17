
# **[OCI Cross Tenancy Remote Peering Connection configuration](#)**
## **An OCI Open LZ [Addon](#) to setup the cross tenancy remote peering conection uisng IaC**

&nbsp; 

**Table of Contents**

- [Overview](#Overview)</br>
- [OCI Private DNS resources](#OCI-Private-DNS-resources)</br>
- [VCN DNS Resolver processing order](#VCN-DNS-Resolver-processing-order)</br>
- [Single-Region: Private DNS configuration view](#1-Single-Region-Private-DNS-configuration-view)</br>
  - [Single-Region: DNS query animation](#11-Single-Region-DNS-query-animation)</br>
- [Multi-Region: Private DNS configuration view](#2-Multi-Region-Private-DNS-configuration-view)</br>
  - [Multi-Region: DNS query animation](#21-Multi-Region-DNS-query-animation)

&nbsp;

## **Overview**
This configuration enables to establish connectivity between two regions in same tenancy and across multiple tenancies, managed by a central network team. It includes all necessary RPC configurations, such as policy creation, RPC setup, and connection establishment. This approach ensures consistency, simplifies administration, and eliminates the complexity of managing RPC across multiple OCI tenancies.

This document provides configuration views for the following use cases:
- Single-Tenancy-RPC: Establishes a remote peering connection between two regions within a single tenancy.
- Multi-Tenancy-RPC: Establishes a remote peering connection between the same or different regions across multiple tenancies.


&nbsp;

### OCI Private DNS resources

| Resource | Description |
| - | - |
| [IAM Policies](https://docs.oracle.com/en-us/iaas/Content/Identity/Concepts/policies.htm) | A set of policies is required to establish connectivity between two tenancies. These policies authorize and admit connectivity from different tenancies, ensuring secure and controlled access to networking resources. |
| [Remote Peering Connection (RPC)](https://docs.oracle.com/en-us/iaas/Content/Network/Tasks/drg-rpc-create.htm#drg-rpc-create) | A Remote Peering Connection (RPC) must be created in both tenancies to establish connectivity between them. This involves configuring a dynamic routing gateway (DRG) in each tenancy and setting up the necessary peerings. |


&nbsp;

### OCI X Tenancy RPC Setup
The VCN DNS resolver processes queries in the priority order presented below. It attempts to resolve each query by sequentially checking the configured options. 
