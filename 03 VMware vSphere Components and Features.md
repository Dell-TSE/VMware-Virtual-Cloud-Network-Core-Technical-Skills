# VMware vSphere Components and Features

## Introduction

VMBeans *uses VMware vSphere® to virtualize all the applications that are used to support their online coffee delivery service.*

*As a new administrator, you must minimize application downtime and maximize resource utilization. To make the most of your data center, you must be familiar with the components and main features of vSphere.*

VMBeans is a coffee company with a large network of retail stores, roasteries, warehouses, and a vibrant online presence. VMBeans recently expanded its business to offer a door delivery service for its coffee products, so that users can enjoy a good roast from the comfort of their home.

To support this new service, VMBeans runs a virtualized three-tier application that includes web servers, application servers, and a database. Customers can purchase all products online through the VMBeans website at www.vmbeans.com.

### Learner Objectives

- Identify the functions of the components in a vSphere environment
- Describe the vSphere features and their benefits

## vSphere Components

You can use the vSphere platform and tools to the manage physical resources, such as CPU, storage, and networking, which support the virtual infrastructure.

This virtual infrastructure includes the following core components for running virtual machines:

- VMware ESXi™: You create and run VMs on this hypervisor (The software that extracts the computer's hardware and presents it as virtual hardware to VMs is called hypervisor.).
- VMware vCenter Server®: You use this service to centrally administer the connected ESXi hosts.

In addition to these two core components, the vSphere virtual infrastructure includes several components that perform different functions.

### Role of vSphere Components

![image-20211209083002773](03%20VMware%20vSphere%20Components%20and%20Features.assets/image-20211209083002773.png)

- The vSphere Client is a graphical interface for administering vCenter Server. It is the visual part of the software where you view and interact with the buttons and controls.

  Through the vSphere Client, you connect to vCenter Server to manage ESXi hosts and other components of the vSphere environment.

  You can use the vSphere Client from a browser on any computer that is connected to the same network as vCenter Server.

- The vCenter Server software component manages multiple ESXi hosts and their physical resources. vCenter Server also manages virtual machines, virtual networks, and storage.

  vCenter Server is deployed as a virtual appliance (A virtual appliance is a type of VM that is preconfigured with an OS and an application that performs a specific task.) that runs on an ESXi host. vCenter Server is preconfigured to manage the entire vSphere environment.

- A virtual machine or VM is a software representation of a physical computer and its components.

  Like a physical computer, each VM runs an operating system and one or more applications.

- The ESXi software runs on a host. The ESXi host creates and runs VMs that are independent of one another.

  When you install the ESXi software on a server, ESXi controls the underlying resources of the server and divides the hardware for running multiple guest operating systems.

  You can run an individual ESXi host, which is also called a standalone host. You can also use vCenter Server to collectively manage several ESXi hosts.

- A physical network includes machines that are interconnected through physical devices, such as switches and cables, so that they can send data to and receive data from each other.

  In a virtual network, the VMs that run on a physical host connect logically to each other by using virtual network devices.

  A vSphere network can also connect virtual machines to physical machines.

- vSphere uses different types of physical storage devices to present to VMs as the virtualized storage hardware:

  - Storage devices that are connected through a network
  - Storage devices that are directly attached to ESXi hosts

## vSphere Features

Migrating from a physical infrastructure to a virtual infrastructure provides numerous benefits. After migrating to vSphere, several key features are available to you.

### vSphere vMotion

Virtual machines can be moved or migrated from one host to another host with zero downtime by using the VMware vSphere® vMotion® feature. If a physical host must be shut down for maintenance or upgrade, all virtual machines running on that host can be migrated to other hosts. This method ensures that no downtime occurs for maintenance operations.

![vSphere-vMotion](03%20VMware%20vSphere%20Components%20and%20Features.assets/vSphere-vMotion.svg)

### vSphere HA

When you use the VMware vSphere® High Availability feature, a physical server failure does not stop your business. Virtual machines on the failed host are automatically started on other hosts. This feature minimizes the downtime, which is experienced by a physical server failure, to 1 or 2 minutes.

![vsphere-ha](03%20VMware%20vSphere%20Components%20and%20Features.assets/vsphere-ha.svg)

### vSphere DRS

Virtual servers that require heavy server resources can be moved automatically to hosts that have available capacity by using the VMware vSphere® Distributed Resource Scheduler™ feature. This feature ensures that all virtual servers can work at 100 percent capacity and access the resources that they need despite the loads of other virtual machines.

![vsphere-drs](03%20VMware%20vSphere%20Components%20and%20Features.assets/vsphere-drs.svg)

## Summary

*As an administrator, you use various vSphere components in a virtual environment. You also use the vSphere features, such vSphere vMotion, vSphere HA, and vSphere DRS, to minimize downtime and ensure the optimal use of resources.*

## Knowledge Check

### Core Components of vSphere

Which components are core to running a vSphere infrastructure? Select all options that apply and click **Submit**.

- [x] ESXi
- [ ] Virtual machines
- [ ] vSphere storage
- [ ] vSphere networking
- [x] vCenter Server

### Main Features of vSphere

What function does each component perform in a vSphere environment?

| Features        | Purpose                                                     |
| --------------- | ----------------------------------------------------------- |
| vSphere HA      | Automatically restarts virtual machines on a failed host    |
| vSphere vMotion | Moves virtual machines from host to host with zero downtime |
| vSphere DRS     | Automatically balances virtual machines across hosts        |

