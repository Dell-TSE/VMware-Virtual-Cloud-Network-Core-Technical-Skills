# Management, Control and Data Plane

## Introduction

Network devices include different components that work together to send and receive traffic.
As a network administrator, you must understand how these elements interact to provide network connectivity.

### Learner Objectives

- Identify the different layers of networking planes
- List the functions of each networking plane

## Networking Planes

Networks use the data forwarding process to carry user traffic from one device to another device. Networks include three layers or planes: management plane, control plane, and data plane.

Consider this analogy to understand the networking planes.

To travel between two cities that you have never visited:

- You open the navigation application on your smartphone and enter the name of the origin and destination cities.
- The application considers the current traffic and other criteria, such as tolls, and performs calculations to determine the best route between the two cities.
- After determining the route, you use your car to reach the destination.

In the analogy, your smartphone and the user interface of the navigation application are components in the management plane. The algorithm that calculates the best route between the two cities is a component in the control plane. Your car, which transports you to the destination, is a component in the data plane.

### Management, Control, and Data Planes

All networking devices operate in the management, control, and data planes. These planes coordinate with each other to identify the best possible path between devices.

#### Management Plane

The management plane plays an important role in securing a network device. The management plane receives requests. Any breach on this plane allows access to all data flowing through the device and might result in the manipulation of traffic.

The management plane performs the following functions:

- Users manage, configure, and monitor the network devices, such as switch or router, in the management plane.
- The network device usually provides a CLI or GUI for configuring the network and the device. The CLI or GUI operates in the management plane.

![Management+Plane](assets/Management+Plane.svg)

#### Control Plane

The control plane can be considered the brain of a network.

The control plane performs the following functions:

- The control plane calculates and determines the best path for a packet to navigate from one device to another device. After determining the best path, the control plane propagates this information to the data plane.
- The routing protocols, such as BGP (Border Gateway Protocol (BGP) is a dynamic routing protocol used to route traffic across the Internet.), OSPF (Open Shortest Path First (OSPF) is a nonproprietary link-state routing protocol typically used in the data center.), RIP (Routing Information Protocol (RIP) is one of the oldest distance-vector routing protocols, which employs the hop count as a routing metric.), primarily operate in this layer.

![Control+Plane](assets/Control+Plane.svg)

#### Data Plane

The data plane, also called the forwarding plane, can be considered the muscle of the network.

The data plane performs the following functions:

- The data plane forwards the user traffic between the networking devices, such as switches or routers.
- The data plane performs the fundamental function of a network, which is carrying the user traffic from one device to another device.

The control and management planes help the data plane to perform effective data forwarding.

![Data+Plane](assets/Data+Plane.svg)

## Summary

*In network devices, the management, control, and data planes work together to send traffic from one device to another.*
*As an administrator, you must understand the role of each plane to effectively configure and manage your networks.*

## Knowledge Check

### Functions of Networking Planes

What are the functions of the networking planes? Match the planes to their corresponding functions and click **Submit**.

| Planes           | Functions                                                    |
| ---------------- | ------------------------------------------------------------ |
| Control plane    | Calculates and determines the best path for a packet to navigate from one device to another |
| Management plane | Enables users to configure and monitor the network devices   |
| Data plane       | Forwards user traffic between the networking devices         |

