# vSphere Standard Switches

After completing this lesson, you will be able to meet the following objectives:

- Identify characteristics of vSphere standard switches
- View components and properties of a standard switch configuration

## Introduction

Over time, the networking strategy of [VMBeans](https://core-vmware.bravais.com/api/dynamic/documentVersions/3564/files/70459/c4cdb738-c65e-45f3-96ff-280ea2ebed4a.html) changes. At first, the company used a single standard switch that connected all its virtual machines and ESXi hosts to the network. But after expansion and growth, the company must reevaluate its strategy and decide whether to create separate networks for new departments.

As a new member of the administration team, you must understand how standard switches work so that you can help meet the networking requirements for the additional departments at VMBeans.

## How vSphere Standard Switches Work

### vSphere Standard Switch

A vSphere standard switch is a virtual switch that provides virtual networking for an ESXi host and its virtual machines.

A standard switch is associated with a single ESXi host. For example, if you have three hosts that require network connectivity, then you must create a standard switch on each host.

<img src="06%20vSphere%20Standard%20Switches.assets/StandardSwitch_WhatIs.png" alt="StandardSwitch_WhatIs" style="zoom:50%;" />

#### Single Standard Switches: Managing Traffic

A single standard switch can be used for both VM and ESXi system traffic. The physical NICs are shared by all port groups.

In this example, different networks share the bandwidth provided by the standard switch. The standard switch manages VM traffic from the Accounting network, VM traffic from the Sales network, ESXi management network traffic, and iSCSI storage network traffic. The uplink ports pass all traffic through to the physical NICs.

<img src="06%20vSphere%20Standard%20Switches.assets/StandardSwitch_SharedNetwork.svg" alt="StandardSwitch_SharedNetwork" style="zoom: 33%;" />

### Isolating Networks

You can use standard switches to isolate different types of network traffic from each other. Why might you want to isolate networks? Consider the following reasons:

- Improve network performance: Each network has its own dedicated bandwidth and does not have to share bandwidth with other networks.
- Help prevent unauthorized monitoring or network interference by other VMs.

You can isolate networks by using either multiple standard switches or VLANs.

#### Multiple Standard Switches

You can create a separate standard switch for each of your VM port groups and VMkernel ports.

Each standard switch has its own physical NICs. Traffic from each virtual network (port group) is physically separated by each standard switch.

The downside of having separate standard switches is that the ESXi host must have enough physical NICs to support the configuration, which can be costly.

For example, with four standard switches that have two uplink ports each, the ESXi host requires eight physical NICs.

Also, an ESXi host has limits to the number of physical NICs that it can support.

![StandardSwitch_MultipleSwitches](06%20vSphere%20Standard%20Switches.assets/StandardSwitch_MultipleSwitches.svg)

#### VLANs

Instead of using separate standard switches to isolate networks, you can use a single standard switch and isolate networks using VLANs.

A VLAN (virtual LAN) is a subgroup of a physical network. VLANs can logically group VMs, systems, and devices into separate virtual networks, regardless of where they are located in the physical network.

A VLAN has a VLAN ID, which is a number that uniquely identifies the VLAN. Virtual switches and physical switches use the VLAN ID to route packets to the correct network.

Each port group on a virtual switch can be configured to use VLANs.

In this example, VM port groups and VMkernel port groups are configured to be members of specific VLANs.

Why use a single standard switch with VLANs instead of multiple standard switches to isolate networks? When ready, click here for possible reasons.

#### Why Use VLANs?

In addition to improving network performance and providing additional security, VLANs do not require that you add new cabling or make significant physical changes to the network infrastructure.

VLANs must be planned and configured in your physical and virtual network infrastructure before they can be used. Therefore, if your data center already has an existing VLAN configuration in place, then you might prefer to use VLANs instead of multiple standard switches to isolate your networks.

![StandardSwitch_VLANs](06%20vSphere%20Standard%20Switches.assets/StandardSwitch_VLANs.svg)

## Viewing Standard Switch Configurations

As a new member of the VMBeans administrators' team, you must become familiar with the standard switches that is configured in the vSphere environment. How many standard switches are configured? What are the VM port groups on each standard switch? Which VMs are attached to each port group? On which switch are the VMkernel ports configured? How many uplinks does the standard switch have?

The topology diagram (The topology diagram provides a visual representation of the adapters and port groups connected to the standard switch.) provides you with this information.

Explore the topology diagram for a standard switch located on the ESXi host called sa-esxi-01.vclass.local to help answer these questions.

### Topology Diagram

![image-20211213095145741](06%20vSphere%20Standard%20Switches.assets/image-20211213095145741.png)

- Standard Switch: Name of the standard switch, which uses the naming convention vSwitch followed by a number (starting at 0), for example, vSwitch0, vSwitch1, vSwitch2, and so on.

- Port group name: Accounting

  This port group contains virtual machines on the Accounting network. In this example, the port group contains four VMs, indicated by the number in parentheses.

- Port group name: IP Storage

  This port group contains a VMkernel port for handling IP storage traffic, for example, traffic between the ESXi host and the iSCSI storage array on which its VMs are located.

  VMkernel ports use the naming convention vmk followed by a number, starting at 0.

  The VMkernel port is named vmk1 (vmk0 is already used) and has an IP address of 172.20.10.61.

- Port group name: Management Network

  This port group contains a VMkernel port for handling management traffic for the ESXi host sa-esxi-01.vclass.local.

  vCenter Server uses this network to communicate with this ESXi host. Other ESXi hosts can also communicate with this ESXi host using this network.

  The VMkernel port is named vmk0 and has an IP address of 172.20.10.51.

- Port group name: Sales

  This port group contains virtual machines on the Sales network. It contains two virtual machines, indicated by the number in parentheses. The names of the virtual machines are also shown.

- Data path:
  This part of the diagram shows whether a virtual machine is connected to the physical network. The diagram also identifies the physical adapters that carry the data.

  The orange line shows that the Photon-10 VM is connected to the physical network using the vmnic4 uplink adapter on sa-esxi-01.vclass.local.

- Uplinks:
  Names of the physical (uplink) adapters, which use the naming convention vmnic followed by a number (starting at 0).

  This switch has three uplink adapters: vmnic0, vmnic1, and vmnic4.

### Standard Switch Properties

From the topology diagram, you can view the properties of the standard switch,  port groups, VMkernel ports, and uplink ports. You might check these properties when connectivity problems occur.

![2021-12-13_10-07-33](06%20vSphere%20Standard%20Switches.assets/2021-12-13_10-07-33.png)

#### Standard Switch

The MTU is the maximum transmission unit of a network packet. The default is 1,500 bytes.

By increasing the MTU value, you increase the amount of data transmitted in a single network packet. A larger MTU size improves networking efficiency.

![StandardSwitch_Properties_vSwitch0](06%20vSphere%20Standard%20Switches.assets/StandardSwitch_Properties_vSwitch0.png)

#### Port Group

The VLAN ID indicates the VLAN that the port group is associated with. If the field is blank, no VLAN is used.

![StandardSwitch_Properties_Production](06%20vSphere%20Standard%20Switches.assets/StandardSwitch_Properties_Production.png)

#### VMkernel

TCP/IP stack refers to the networking layer in the VMkernel. The VMkernel TCP/IP stack provides networking for the ESXi host. Most of the time, the Default stack is used, which is a general-purpose stack that handles all types of ESXi system traffic. Other stacks are vSphere vMotion, Provisioning, and Custom.

Enabled services identifies the types of network traffic that this VMkernel port handles. Types of traffic are Management, vSphere vMotion, vSphere Fault Tolerance, vSphere Replication, and vSAN.

IPv4 settings provide IP address information that the VMkernel port uses to communicate over the network.

![StandardSwitch_Properties_vmk0](06%20vSphere%20Standard%20Switches.assets/StandardSwitch_Properties_vmk0.png)

#### Uplink

Status tells you whether the physical adapter is connected or disconnected.

![StandardSwitch_Properties_vmnic0](06%20vSphere%20Standard%20Switches.assets/StandardSwitch_Properties_vmnic0.png)

For more information about standard switch properties, see [vSphere Networking](https://docs.vmware.com/en/VMware-vSphere/7.0/com.vmware.vsphere.networking.doc/GUID-35B40B0B-0C13-43B2-BC85-18C9C91BE2D4.html).

### Hands-On Practice

#### Simulation Overview

When a user at VMBeans cannot access a production VM called Win10-02, you use the topology diagram to determine whether Win10-02 is connected to the external (physical) network. You also use the diagram to identify the physical adapter that carries the VM's data.

In this simulation, your objective is to verify that a VM is connected to the external network.

#### Simulation: Verifying That a VM Is Connected to the External Network

In the following simulation you will verify that a VM is connected to the external network.

1. In the left navigation pane Hosts and Clusters inventory view, select Win10-02. View the Summary window and view the Host field. Win10-02 is hosted on sa-esxi-01.vclass.local.
2. In the left navigation pane, select sa-esxi-01.vclass.local.
3. In the main window, click the Configure tab.
4. In the middle navigation pane, under Networking, select Virtual switches. The topology diagram is displayed.
5. Click the scroll channel to move down until you see Standard Switch:  vSwitch1.
6. To expand the panel, select the arrow next to Standard Switch: vSwitch1.The Production port group is located on vSwitch1.
7. Click the scroll channel to move down until you see the Production port group.
8. To show the VMs connected to this port group, in the main window, select the arrow next to Virtual Machines.
9. In the main window, select Win10-02.
10. Verify that the diagram has an orange line that connects Win10-02 to a physical adapter. In this instance, it connects to vmnic3. The orange line shows that Win10-02 connects to the external network through the vmnic3 NIC. Click the ellipsis (...) next to vmnic3 to view the status of the vmnic3 physical adapter.
11. Click View Settings and verify that the status of vmnic3 is Connected. A Connected status indicates that the connection between vmnic3 and the physical network is good.

This completes the simulation.

## Summary

*Because the VMBeans data center has an existing VLAN infrastructure, the administration team considers isolating networks using VLANs.*

*As a new member of the VMBeans administration team, you recognize the value of using the standard switch topology diagram. It helps you identify the components and properties of a standard switch configuration and check network connectivity of virtual machines.*

## Knowledge Check

### About Standard Switches

Which statements accurately describe standard switches? Select all options that apply. Then click **Submit**.

- [ ] A standard switch is a virtual switch that is managed by vCenter Server for all the ESXi hosts.
- [ ] A standard switch differs from a virtual switch because standard switches contain VMkernel ports.
- [x] A standard switch is a virtual switch that is configured for a single ESXi host.
- [x] An ESXi host can contain one or more standard switches.

### Standard Switch Naming Conventions

Which naming convention does each component use? Match each example name to the appropriate networking component. Then click **Submit**.

| Naming conventions | Components      |
| ------------------ | --------------- |
| vmnic0             | Uplink adapter  |
| vSwitch0           | Standard switch |
| vmk0               | VMkernel port   |

### Standard Switch Properties

Which properties apply to the networking components? For each property, select the appropriate component or components. Then click **Submit**.

| Properties              | Standard Switch | Port Group | VMkernel Port | Uplink Adapter |
| ----------------------- | :-------------: | :--------: | :-----------: | :------------: |
| IPv4 settings           |                 |            |       x       |                |
| VLAN ID                 |                 |     x      |               |                |
| TCP/IP stack            |                 |            |       x       |                |
| Physical adapter status |                 |            |               |       x        |
| MTU                     |        x        |            |               |                |

