# NSX-T Data Center Architecture

## Introduction

*As* VMBeans *increases the number of services provided to its clients, additional applications must be added and connected to the network.*

*As a network administrator, you must ensure that connectivity exists between the applications in your data center. To accomplish this task, you must understand the VMware NSX-T™ Data Center architecture and validate that all components are working as expected.*

### Learner Objectives

- Describe the­ NSX-T Data Center architecture
- Use the NSX-T Data Center user interface to validate its components

## NSX-T Data Center Architecture

In the NSX-T Data Center architecture:

- The management and control planes reside in a single virtual appliance called NSX Manager.
- The data plane includes a group of ESXi hosts, KVM hosts, bare-metal servers, and NSX Edge nodes that are responsible for forwarding the traffic. These servers and edges configured to participate in the NSX network are called transport nodes.

![image-20211213191040157](assets/image-20211213191040157.png)

### Management Plane

The management plane performs the following functions:

- Provides the REST API and web-based UI interface for all user configurations
  - REST API: Users can use an API to programmatically access the underlying platform capabilities and features. A REST API is an API that uses HTTP requests to interact with the platform.
- Provides a centralized location for configuring networking and security
- Publishes the configuration to the control plane
- Installs and prepares the data plane components

### Control Plane

The control plane performs the following functions:

- Receives the network and security configuration from the management plane and helps to realize it in the data plane
- Determines which path to use to send the traffic for logical switching, routing, and distributed firewall
- Disseminates topology changes reported by the data plane components, such as a host or network link down

### Data Plane

The data plane performs the following functions:

- Forwards traffic based on the instructions received from the control plane
- Maintains the status of physical links and manages failover
- Maintains packet-level statistics

## Use Case for NSX-T Data Center

Review the case study of an NSX-T Data Center architecture.

VMBeans recently expanded its business to offer a door delivery service for its coffee products. To support this new service, VMBeans runs a virtualized three-tier application that includes web servers, application servers, and a database.

As a junior network administrator at VMBeans, you must help the networking team to connect and secure all these servers to ensure that the webpage for the coffee orders runs smoothly and it is always accessible to users.

You create a virtual switch to connect the web servers for the webpage used for the coffee orders:

- Use the NSX user interface to create and configure your switch.

  You interact with the NSX management plane.

- After you submit the configuration from the NSX UI, the control plane views your configuration and sends it to the appropriate transport nodes (ESXi, KVM, and NSX Edge nodes) .

  This step does not need intervention.

- The transport nodes receive the configuration for the virtual switch that you created from the NSX UI. This virtual switch sends traffic between the web applications that are connected to it.

  This step takes place at the data plane.

## Hands-On Practice

### Simulation Overview

A senior network administrator in your team recently deployed a new NSX-T Data Center environment. You must verify that all NSX components were successfully deployed and are currently working as expected from the NSX UI.

In this simulation, you perform the following tasks:

- Verify the configuration and status of a pre-deployed NSX Manager instance
- Verify the status of ESXi hosts configured as transport nodes
- Verify the status of KVM hosts configured as transport nodes
- Verify the configuration and status of a pre-deployed NSX Edge cluster and nodes

### Simulation: Verifying the Configuration and Status of a Predeployed NSX Manager Instance

In this simulation you will log in to the NSX UI, navigate the interface to locate a predeployed NSX Manager, and check its configuration details and status. 

1. Click the **Username** box, the username will be populated for you.
2. Click the **Password** box, the password will be populated for you.
3. Click the **LOG IN** button to log into NSX UI.
4. On the NSX Manager Homepage, click the **System** tab at top of the page.
   You are directed to the System Overview section.
5. Once in the System Overview section, from the left panel, click **Configuration > Appliances**.
   Observe the status of the cluster is STABLE and that this cluster contains a single appliance with IP address 172.20.10.41.
6. Click the **VIEW DETAILS** link on the NSX appliance card.
   Observe the OPERATIONAL STATUS column indicates all services are UP and that the APPLIANCE DETAILS column shows the Version is 3.0

The simulation is now complete.

### Simulation: Verifying the Configuration and Status of a Predeployed NSX Manager Instance

In this simulation you will log in to the NSX UI, confirm the Compute Cluster nodes have been prepared as Transport Nodes and the verify status of an ESXi prepared Transport nodes.

1. Click the **LOG IN** button to log into NSX UI.

2. Click the **System** tab at the top of the page.

3. Click **Configuration>Fabric** in the left menu to expand the sub menu.

4. From the Fabric sub menu, click **Nodes**.
   The Host Transport Nodes page is displayed

5. Click the **Managed by** drop down located at the top of the Hosts Transport Nodes page.

6. From the drop down menu, click **sa-vcsa-01.vclass.local**.

7. Click the **double arrow** at the top of the left menu to collapse the side bar.

8. On the Hosts Transport Nodes page, click **SA-Compute-01(2)** to expand the nodes in the cluster.

9. Review the information presented about the transport hosts in the cluster. 

   - Two ESXi Transport Nodes are listed, sa-esxi-04 and sa-esxi-05.
   - Verify that the ***NSX Configuration\*** of both nodes is Success, the ***NSX Version*** is 3.0 and that the ***Node Status*** is Up.

   When ready, click anywhere on screen to resume the simulation.

10. Click the **information icon** located under the Node Status column of host sa-esxi-04.

11. Review the information presented on the Transport Node Status information box.

    - Verify that ***Manager Connectivity*** is Up.
    - Verify that ***Controller Connectivity*** is Up.

    Click the 

    MORE INFO

     link to view additional information about the node.

12. Review the information present on the Monitor tab, then click the **Overview** tab.

13. Click the **X** located at the top right of the page to close this display.

### Simulation: Verifying the Status of KVM Hosts That Are Configured as Transport Nodes

In this simulation you will log in to the NSX UI, navigate the interface to locate the KVM hosts which have been prepared as Transport Nodes, and view their status.

1. Click the **LOG IN** button to log into NSX UI.

2. Click the **System** tab at the top of the page.

3. From the left menu, click **Nodes**.
   The Host Transport Nodes page is displayed

4. Click the **Managed by** drop down located at the top of the Hosts Transport Nodes page.

5. From the drop down menu, click **Standalone Hosts**.

6. Click the **double arrow** at the top of the left menu to collapse the side bar.

7. Review the information presented on the Hosts Transport Nodes page.

   - Two nodes of ***OS Type*** Ubuntu KVM are listed: sa-kvm-01 and sa-kvm-02.
   - Verify that the ***NSX Configuration State*** of both nodes is Success, the ***NSX Version*** is 3.0 and that the ***Node Status*** is Up.

   When ready, click anywhere on screen to resume the simulation. 

8. Click the **information** **icon** located under the Node Status column of host sa-kvm-02. 

9. Review the information presented on the Transport Node Status information box.

   - Verify that ***Manager Connectivity*** is Up.
   - Verify that ***Controller Connectivity*** is Up.

   Click the

    

   MORE INFO

    

   link to view additional information about the node.

10. Review the information present on the Monitor tab, then click the **Overview** tab.

11. Click the **X** located at the top right of the page to close this display.

### Simulation: Verifying the Configuration and Status of a Predeployed NSX Edge Cluster and Nodes

In this simulation you will log in to the NSX UI, navigate the interface to locate the Edge nodes, view their status, check their connectivity with the Management and Control Planes and verify they are members of the Edge cluster.

1. Click the **LOG IN** button to log into NSX UI.

2. Click the **System** tab at the top of the page.

3. From the left menu, click **Fabric>Nodes** to open the Host Transport Nodes page.

4. Click the **Edge Transport Nodes** tab at the top of the page.

5. Collapse the left side bar by clicking the **double arrow** at the top of the left menu.

6. Review the information presented on the Edge Transport Nodes page.

   - Two nodes are listed: sa-nsxedge-01 and sa-nsxedge-02.
   - Verify that the ***Configuration State*** of both nodes is Success, the ***NSX Version*** is 3.0 and that the ***Node Status*** is Up.

   When ready, click anywhere on the screen to resume the simulation.

7. Click the **Information icon** located under the Node Status column of host sa-nsxedge-01.

8. Verify that both Manager Connectity and Controller Connectivity are Up, then click the **MORE INFO** link.

9. Review the information displayed on the Monitor tab, then click the **Overview** tab. 

10. Click the **X** located at the top right of the page to close this display. 

11. Click the **Edge Clusters** tab.

12. Under the Edge Transport Nodes column, click the number **2**.
    Confirm that the sa-nsxedge-01 and sa-nsxedge-02 transport nodes are members of the Edge-Cluster-01.

The simulation is now complete.

## Summary

NSX-T Data Center Architecture

The architecture of NSX-T Data Center includes the management, control, and data planes. As an administrator, you must understand the role of each plane and validate that its components are working as expected.

## Knowledge Check

### NSX Planes and Functionality

What are the functions of the NSX planes?
Match the NSX planes to their corresponding functions. Then click Submit.

| Planes           | Functions                                                    |
| ---------------- | ------------------------------------------------------------ |
| Control Plane    | Receives the network and security configuration from the management plane and helps to realize it in the data plane |
| Management Plane | Provides the REST API and web-based UI interface for all user configurations |
| Data Plane       | Forwards traffic based on the instructions received from the control plane |

### Data Plane

Which components reside in the data plane of NSX-T Data Center?
Select the three options that apply and click Submit.

- [x] NSX Edge nodes

- [x] KVM hosts

- [ ] vCenter Server

- [ ] NSX Manager

- [x] Bare-metal servers
