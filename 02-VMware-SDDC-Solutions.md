# VMware SDDC Solutions

After completing this lesson, you will be able to meet the following objectives:

- Identify VMware solutions that integrate with vSphere in SDDC

## Introduction

VMBeans is adopting a software-defined data center to virtualize its compute, network, and storage resources. The SDDC accelerates VMBeans' journey to the private cloud so that it can offer on-demand IT services to its employees and customers.

As a new administrator, you are tasked with assisting with the implementation of the SDDC. To successfully do this, you become familiar with VMware’s solutions.

## VMware Solutions and the SDDC

### Integrating Solutions at the SDDC Layers

At VMBeans, vSphere integrates with each layer of the SDDC infrastructure.
Which VMware solutions integrate with vSphere in each layer of the SDDC? What problems do the solutions solve?

![VMware_SDDC](assets/VMware_SDDC.svg)

#### Physical

At VMBeans, the physical infrastructure team manages the physical servers, storage, and networking devices.

The team selects tested and approved hardware vendors from the VMware Compatibility Guide.

You work closely with the physical infrastructure team because they manage the physical resources such as the hosts, storage, and network on which vSphere runs.

#### Virtual Infrastructure

At VMBeans, the virtual infrastructure is managed by integrating three VMware solutions:

- vSphere manages multiple ESXi hosts and virtual machines (VMs) through vCenter Server.
- vSAN integrates with vSphere to manage the physical storage disks of ESXi hosts as a single virtual storage device for VMs.
- NSX Data Center provides the software-defined networking resources for managing connectivity between all SDDC layers.

#### Cloud Management

Using cloud management, VMBeans offers an online catalog of services for employees and customers. These services include applications, monitoring, storage, identity management, and many more.

You are both a consumer and a provider of cloud services:

- Consumer: When you request storage space for VMs, you use the service catalog to place the request.
- Provider: When you deploy new VMs to run applications for other departments of VMBeans.

#### Service Management and Automation

VMBeans automates and monitors the entire portfolio of services and operations of its private cloud by integrating vRealize Automation with the service catalog and with vRealize Operations.

So what happens when you make a catalog request for more storage space?

- The vRealize Automation system checks custom roles, policies, and approval flows that are predefined by the cloud team.
- vRealize Automation approves the request without any manual intervention.
- You begin to consume the additional storage space for your VMs.
- With vRealize Operations, the cloud team proactively monitors the usage of storage space to forecast when new storage space is required.

#### Business Continuity

In its business continuity plan, the team at VMBeans includes solutions for data protection and disaster recovery of critical management components of the SDDC.

As an administrator, these solutions help you to protect the vSphere components, for example:

- To ensure that a data center continues operating during an anticipated storm, the team uses Site Recovery Manager to move the data center to a remote location, unaffected by the storm.
- With vSphere Replication, the team creates replicas of business-critical VMs. If a VM's data becomes corrupted, you can recover it by using a replica.

#### Security

VMware AppDefense and VMware Carbon Black provide security to the workloads running on your data centers.

These solutions are powered by machine learning to understand the state and behavior of business-critical applications and monitor them to detect suspicious behavior and prevent attacks in real time.

For example, AppDefense uses ESXi for monitoring guest VM application behavior.

If the application does not behave as expected or shows malicious behavior, the system can suspend or shut down the VM to prevent possible spread of the problem to other parts of the infrastructure.

## Summary

Several VMware solutions integrate with vSphere to help manage the VMBeans' SDDC. Knowing which solutions to integrate and use is key to maintaining a well-performing SDDC.

## Knowledge Check

### An SDDC Defined by VMware

What solutions does each layer of an SDDC integrate with?

| Layers                            | Solutions                                     |
| --------------------------------- | --------------------------------------------- |
| Business Continuity               | Site Recovery Manager and vSphere Replication |
| Service management and automation | vRealize Operations and vRealize Automation   |
| Virtual infrastructure            | vSphere, NSX Data Center, and vSAN            |
| Security                          | VMware AppDefense and VMware Carbon Black     |
