# Micro-Segmentation

## Learner Objectives

- Describe micro-segmentation
- Identify the use cases for micro-segmentation
- List  the benefits of micro-segmentation

## Introduction

[VMBeans](https://core-vmware.bravais.com/api/dynamic/documentVersions/3654/files/72263/c4cdb738-c65e-45f3-96ff-280ea2ebed4a.html) *is successful at modernizing its data centers. However, VMBeans has not devoted enough attention to its security, and it has recently experienced a security breach in one of the data centers.*

*As a security administrator, you must recommend a strategy to prevent such situations in the future. To build security controls in the company’s modern data centers, you must understand the VMware NSX® micro-segmentation and its benefits.*

## Traditional Data Center Security

The landscape of the modern data center is changing at a phenomenal speed. Workloads were rapidly migrated from physical to virtualized to software-defined data centers. Today, you must adapt to multicloud environments, mobile devices, and new architectures such as microservices and containers.

These advances are not without risks because security often becomes an afterthought. Securing and managing all these moving pieces by using traditional security approaches is becoming increasingly complex. A strong defense is not enough only at the perimeter. Modern attacks might target your internal infrastructure by compromising one of your virtual machines and spreading through your data center.

You need an approach to protect all the traffic in the data center and to consistently protect its changing components.

NSX micro-segmentation resolves the security challenges of the modern data center.

![Security-silos-nsx](assets/Security-silos-nsx.svg)

## About Micro-Segmentation

NSX Micro-Segmentation addresses the challenges of traditional data center security.

While traditional data center security policies are applied to the infrastructure, NSX micro-segmentation establishes a security perimeter around each VM or container workload with dynamically defined policies. NSX micro-segmentation allows security administrators to build security controls for each individual workload based on its application requirements.

### Traditional Data Center Security

Traditional data centers pose many security challenges:

- Traditional security policies align with the environment rather than with applications. The security is typically placed at the perimeter of the data center and not in the applications.
- Shared services, such as DNS and Active Directory services, can traverse the application tier boundaries without being checked.
- Traditional segmentation does not prevent lateral communication between workloads in a tier. For example, all virtual machines or containers in the web services tier can freely communicate with each other.
- Attackers can move freely around the data center and access valuable data, after penetrating the environment.

![TraditionalDataCenterSecurity](assets/TraditionalDataCenterSecurity.svg)

### NSX Micro-Segmentation

Micro-segmentation provides several functions and benefits:

- Logically divides the data center into distinct security segments at the individual virtual machine and container level
- Limits lateral movement in the data center
- Minimizes risks and the effect of security breaches
- Uses the existing networking infrastructure

![Micro-SegmentationinNSX-TDataCenter](assets/Micro-SegmentationinNSX-TDataCenter.svg)

## Summary

NSX Micro-Segmentation

*NSX micro-segmentation establishes a security perimeter around each VM.*  *Security administrators can build security controls for each individual workload based on its application requirements.*

## Knowledge Check

### Micro-Segmentation: Benefits and Use Cases

What are the benefits of NSX micro-segmentation?
Select the two options that best answer the question and click **Submit**.

- [ ] Secures the perimeter of the data center
- [ ] Increases lateral movement within the data center
- [x] Leverages the existing network infrastructure
- [x] Limits lateral movement within the data center
- [ ] Allows shared services to traverse tier boundaries

### Micro-Segmentation Security Perimeter

NSX micro-segmentation establishes a security perimeter around each _____?

Select the missing word:

- [ ] Network
- [ ] Datacenter
- [ ] Hypervisor
- [x] VM