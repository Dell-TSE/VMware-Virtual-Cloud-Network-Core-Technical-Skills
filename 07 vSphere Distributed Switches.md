# vSphere Distributed Switches

## Introduction

[VMBeans](https://core-vmware.bravais.com/api/dynamic/documentVersions/3651/files/72259/c4cdb738-c65e-45f3-96ff-280ea2ebed4a.html) *is a fast-growing company. Not too long ago, it had just 2 ESXi hosts and 10 virtual machines in its data center. Now the vSphere administration team is responsible for more than 20 ESXi hosts and more than 200 VMs.*

*Because of its continuing growth, the company moves from standard switches to distributed switches. Your goal is to understand why: What are the benefits of distributed switches? And what does a distributed switch configuration look like?*

### Learner Objectives

- Describe the benefits of vSphere distributed switches
- Compare distributed and standard switches
- View a distributed switch configuration in the vSphere Client

## About vSphere Distributed Switches

### Benefits of Distributed Switches

![DistributedSwitch_WhatIs2](07%20vSphere%20Distributed%20Switches.assets/DistributedSwitch_WhatIs2.svg)

vSphere Distributed Switch is a virtual switch that provides virtual networking for all ESXi hosts in a data center.

Whereas a standard switch is owned and managed by a single ESXi host, a distributed switch is owned and managed by vCenter Server.

A distributed switch provides the following benefits:

- Virtual machines maintain a consistent network configuration as they migrate between hosts in the data center.
- Administrators have a central point of control for creating, administering, and monitoring the virtual networks.

### Distributed Switches and Standard Switches: Features

Distributed switches and standard switches are similiar in that they both provide basic virtual switch functionality.

Distributed switches provide additional features that administrators can use to monitor and manage their virtual networks.

| Feature                                                      | Standard Switch | Distributed Switch |
| :----------------------------------------------------------- | :-------------: | :----------------: |
| VLAN support. (VLANs (virtual LANs) logically group VMs, systems, and devices into separate virtual networks, regardless of where they are located in the physical network. Administrators create VLANs to isolate networks, resulting in improved network performance and security for each network.) |        ✓        |         ✓          |
| Security policy (You can use the virtual switch security policy to protect VMs against impersonation and interception attacks on the network.) |        ✓        |         ✓          |
| NIC teaming and failover policy (The NIC teaming and failover policy is used to create a NIC team (multiple physical NICs grouped together) on the virtual switch. A NIC team provides network redundancy and load-balancing functionality.) |        ✓        |         ✓          |
| Traffic shaping policy (The traffic shaping policy is a virtual switch mechanism for placing limits on the amount of bandwidth VMs can use for inbound and outbound traffic.) for outbound traffic |        ✓        |         ✓          |
| Traffic shaping policy for inbound traffic                   |                 |         ✓          |
| NetFlow (NetFlow is a network analysis tool for monitoring the network and viewing VM traffic that flows through a distributed switch. Network administrators use NetFlow for detecting potential security risks, and for determining the source of network security attacks.) |                 |         ✓          |
| Port mirroring (Port mirroring duplicates network packets from a source port to a destination port that is used for networking monitoring. Network administrators use port mirroring to analyze network packets when troubleshooting network problems.) |                 |         ✓          |
| Network I/O Control (Network I/O Control can be used to allocate network bandwidth to business-critical applications and to resolve situations where several types of traffic, including virtual machine traffic, compete for network bandwidth.) |                 |         ✓          |

## Distributed Switch Architecture

In the distributed switch architecture, the virtual networking configuration is managed by vCenter Server:

- The port group and VMkernel port configuration is automatically pushed down to all connected ESXi hosts.
- Each ESXi host is responsible for managing their own uplink adapters and for forwarding packets from VMs to their destinations.

![DistributedSwitch_Architecture](07%20vSphere%20Distributed%20Switches.assets/DistributedSwitch_Architecture.png)

## Viewing a Distributed Switch Configuration

### Viewing a Distributed Switch Configuration

You can view details about the configuration of a distributed switch in the vSphere Client.

You select the distributed switch in the Networking view of the navigation pane.

![2021-12-13_10-19-42](07%20vSphere%20Distributed%20Switches.assets/2021-12-13_10-19-42.png)

The **Summary** tab shows switch details and supported features of the distributed switch.

![2021-12-13_10-20-20](07%20vSphere%20Distributed%20Switches.assets/2021-12-13_10-20-20.png)

The **Hosts** tab shows the names and status of the hosts that are currently connected to the distributed switch.

![2021-12-13_10-20-43](07%20vSphere%20Distributed%20Switches.assets/2021-12-13_10-20-43.png)

### Viewing the Distributed Switch Topology

The topology diagram provides useful information for troubleshooting networking problems.

To view the topology of a distributed switch, you select the **Configure** tab. The topology diagram provides a visual representation of the port groups, VMkernel ports, and uplink adapters connected to the distributed switch.

Explore this example topology of a distributed switch called dvs-SA-Datacenter to find information about its components.

![image-20211213102145650](07%20vSphere%20Distributed%20Switches.assets/image-20211213102145650.png)

- pg-SA-Management:
  is the port group for ESXi management traffic.

  Three VMkernel ports are defined, one for each ESXi host connected to the distributed switch.

- pg-SA-Production:
  is the port group for virtual machine production traffic.

  Three virtual machines are connected to this port group.

- pg-SA-vMotion:
  is used for vSphere vMotion traffic.

  vSphere vMotion is used to move powered-on virtual machines from one host to another.

- pg-vSAN-L2:
  is used for vSAN traffic.

  vSAN uses direct-attached storage on the ESXi hosts in a vSphere cluster to create a single storage pool for virtual machines to be stored.

- Data path:

  This part of the diagram shows whether a virtual machine is connected to the physical network. The diagram also identifies the physical adapters that carry the data.

  An orange line shows that the Photon-01 VM is connected to the physical network using the vmnic0, vmnic1, and vmnic4 uplink adapters on sa-esxi-06.vclass.local.

- dvs-SA-Datacente-DVUplinks-1030: Uplinks Port Group.
  This port group is automatically named by vCenter Server and contains the uplink adapters to be used on each of the ESXi hosts.

### Demonstration: Identifying a VM Uplink Adapters

Let's say you are troubleshooting a networking problem with a VM called Linux02. You check the VM's networking configuration but do not find a problem. You start investigating other areas, one of which is the connection from the VM to the physical adapter.

You use the distributed switch topology diagram to identify the physical adapter that Linux02 uses to connect to the physical network.

Play the video to find out how to identify the adapter.

## Summary

*With distributed switches, the VMBeans administration team can easily scale their network to meet requirements as the company continues to expand.*

## Knowledge Check

### Distributed Switches

Which statement accurately describes distributed switches? Select the option that best answers the question. Then click **Submit**.

- [ ] Each ESXi host can have only one distributed switch configured at any time.
- [ ] A standard switch differs from a distributed switch because standard switches contain VMkernel ports.
- [ ] A distributed switch is a virtual switch that is configured for a single ESXi host.
- [x] A distributed switch is a virtual switch that is managed by vCenter Server for all ESXi hosts.

### Distributed Switches and Standard Switches

Which features apply to distributed and standard switches?

|            Features             | Standard Switch | Distributed Switch |
| :-----------------------------: | :-------------: | :----------------: |
| NIC teaming and failover policy |        x        |         x          |
|             NetFlow             |                 |         x          |
|          VLAN support           |        x        |         x          |
|         Port mirroring          |                 |         x          |
|       Network I/O Control       |                 |         x          |

### Viewing Distributed Switch Information

 View the topology diagram and match the distributed switch component with the correct description. Then click **Submit**.

![image-20211213103152807](07%20vSphere%20Distributed%20Switches.assets/image-20211213103152807.png)

| Components       | Descriptions                                        |
| ---------------- | --------------------------------------------------- |
| Photon-02        | Virtual machine                                     |
| vmk0             | VMkernel port                                       |
| vmnic1           | NIC assigned as Uplink 2 on sa-esxi-04.vclass.local |
| pg-SA-Management | VMkernel port group                                 |
| pg-SA-Production | Virtual machine port group                          |

