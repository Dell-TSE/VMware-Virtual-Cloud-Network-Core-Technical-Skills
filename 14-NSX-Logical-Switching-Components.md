# NSX Logical Switching Components

## Introduction

The team is convinced that virtualizing the network switches is the ideal solution for [VMBeans](https://core-vmware.bravais.com/api/dynamic/documentVersions/3572/files/70597/c4cdb738-c65e-45f3-96ff-280ea2ebed4a.html) to release new services instantly.

VMBeans has many data centers spread across the country. As a network administrator, you configure L2 connectivity for all your virtual machines and containers regardless of their physical location. To accomplish this task, you must identify the components of NSX logical switching.

### Learner Objectives

- Describe the­ components and functions of the NSX-T Data Center segments
- Identify the differences between the types of transport zones and segments

## Logical Switching Components

In NSX-T Data Center, segments connect virtual machines and containers regardless of their physical location and the type of hypervisor they are running on.

![image-20211215001440157](assets/image-20211215001440157.png)

- Virtual machines: You can connect virtual machines to a segment regardless of their physical location and the type of hypervisor they are running on.

- Containers: NSX-T Data Center segments provide connectivity for containerized applications. NSX-T Data Center provides the networking layer for vSphere with VMware Tanzu.

- Segment profiles include layer 2 networking configuration details. Segment profiles can be applied at a port level or at a segment level.

  You can configure multiple types of segment profiles such as Quality of Service (QoS), IP Discovery, SpoofGuard, Switch Security, and MAC Management.

- Segment ports: A segment contains multiple segment ports. Entities such as routers, VMs, or containers are connected to a segment through the segment ports.

- The NSX-T Data Center logical switches are called segments:

  - Segments separate networks and provide layer 2 connectivity to their attached VMs and containers.
  - VMs and containers can communicate with each other if they are connected to the same segment.
  - Each segment has a virtual network identifier (VNI), like a VLAN ID. However, unlike VLANs, VNIs scale beyond the limits of VLAN IDs.

- The virtual distributed switch managed by NSX (N-VDS) is module-deployed in all transport nodes during the NSX-T Data Center preparation, which provides layer 2 functionality:

  - In vSphere 7 environments, ESXi hosts can use both N-VDS and VDS for layer 2 forwarding.
  - KVM and bare-metal hosts support only N-VDS.

- Uplinks are logical interfaces on the N-VDS/VDS. Uplinks are used to the connect the host physical NICs to provide external connectivity.

## Types of Segments and Transport Zone

A transport zone defines the scope of a segment or the numbers of transport nodes (VMware ESXi™ hosts, KVM (Kernel-based Virtual Machine (KVM) is a virtualization module in Linux that allows the kernel to function as a hypervisor.) hosts, bare-metal servers, and VMware NSX® Edge™ nodes) across which it expands. A segment belongs to either a VLAN or an overlay transport zone.

![AboutTransportZones_1](assets/AboutTransportZones_1.svg)

### VLAN Transport Zone

The VLAN transport provides the following benefits:

- Is used to establish connectivity to external networks
- Carries VLAN or 802.1Q tagged traffic

### Overlay Transport Zone

The overlay transport zone provides the following benefits:

- Is used for communication between transport nodes
- Carries the Geneve-encapsulated traffic

## Summary

NSX Logical Switching Components

*As a network administrator, you must understand the logical switching components and the interaction between them to forward traffic. Then you can efficiently configure layer 2 connectivity in your data center.*

## Knowledge Check

### NSX Switching Components and Functionality

What are the functions of the NSX switching components?
Match the NSX switching components to their corresponding functions. Then click **Submit**.

| Components      | Features                                                     |
| --------------- | ------------------------------------------------------------ |
| Segment profile | Defines configuration details for layer 2 networking.        |
| Uplink          | The logical interface is used for external connectivity.     |
| Segment port    | Connects routers, virtual machines, and containers to a segment. |
| N-VDS/VDS       | The module provides the layer 2 forwarding functionality.    |

### Transport Zones and Segments

Which statements about overlay transport zones are true?
Select the two options that best answer the question and click **Submit**.

- [x] Carry the Geneve-encapsulated traffic

- [ ] Carry VLAN or 802.1Q tagged traffic

- [ ] Used to establish connectivity to external networks

- [x] Used for communication between transport nodes