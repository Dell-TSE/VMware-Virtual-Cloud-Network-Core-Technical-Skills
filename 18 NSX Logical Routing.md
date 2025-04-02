# NSX Logical Routing

## Learner Objectives

- Recognize the use cases for NSX logical routing
- Connect segments to a Tier-1 gateway and verify connectivity between different segments
- Connect a Tier-1 gateway to a Tier-0 gateway and verify external connectivity

## Introduction

*Your team at* [VMBeans](https://core-vmware.bravais.com/api/dynamic/documentVersions/3576/files/70661/c4cdb738-c65e-45f3-96ff-280ea2ebed4a.html) *is working diligently on ensure that the new web servers run efficiently. You are supporting this effort by ensuring that the web servers can communicate with the application servers and the database, and that the users can access these services through the Internet.*

*As a network administrator, you must connect the workloads to Tier-1 and Tier-0 gateways in VMware NSX® to accomplish these goals.*

## Use Case for Logical Routing

---

The software development team at VMBeans wants to ensure that the two new web servers can communicate with the application server and the database so that the coffee orders are successfully processed and stored.

Also, the users of the coffee delivery service need to access the two new web servers through the Internet.

---

You can use the VMware NSX-T™ Data Center logical routing capabilities to address these requirements. You can use a Tier-1 gateway to connect the web servers to the application and database servers, and a Tier-0 gateway to ensure that the web servers can be accessed through the Internet.

Tier-1 gateways are typically used to connect virtual machines and containers running on different networks or segments, while Tier-0 gateways are used to provide connectivity to the external networks and the Internet.

![UseCase](assets/UseCase.svg)

## Hands-On Practice

### Simulation Overview

The web servers, application server, and database server that support the VMBeans coffee delivery service are currently connected to different segments.

As a junior network administrator, you must ensure that the servers of the three-tier application can communicate with each other. You must also enable users to access the coffee delivery webpage through the Internet.

In this simulation, you perform the following tasks:

- Connect segments to a Tier-1 gateway and verify connectivity between different segments
- Connect a Tier-1 gateway to a Tier-0 gateway and verify the external connectivity

### Simulation: Connecting Segments to a Tier-1 Gateway and Verifying Connectivity Between Segments

In this simulation you will log in to the NSX UI, navigate the inventory to locate the preconfigured Tier-1 Gateway, and connect the Web-Segment, App-Segment, and the DB-Segment to the Tier-1 Gateway.

Then, from the vSphere Client, you will open a Web Console to T1-Web-01 and ping T1-App-01 and T1-DB-01.

#### Task 1

In this task you verify the configuration of the preconfigured Tier-1 gateway.

1. Click the **Networking** tab at top of NSX UI.

2. From the left menu, click **Connectivity>Tier-1 Gateways.**

3. Verify the details of the Tier-1 Gateway:

   - ***Tier-1 Gateway Name***: T1-GW-01
   - ***#Linked Segments***: 0
   - ***Status***: Success

   When ready click anywhere on screen to resume the simulation.

#### Task 2

In this task, you connect the Web-Segment, App-Segment, and the DB-Segment to the Tier-1 Gateway.

1. From the left menu, click **Segments.**
2. Click the **double arrow** at the top of left menu to collapse the side bar.
3. Click the **three vertical elipse** icon at the beginning of the ***App-Segment*** line.
4. Click **Edit.**
5. Click the **Connectivity** drop down menu. 
6. From the menu, click **T1-GW-01**.
7. Click **SAVE**.
8. Click **CLOSE EDITING**.
9. Click the **three vertical elipse** icon at the beginning of the ***DB-Segment*** line.
10. Click **Edit.**
11. Click the **Connectivity** drop down menu. 
12. From the menu, click **T1-GW-01**.
13. Click **SAVE**.
14. Click **CLOSE EDITING**.
15. Click the **three vertical elipse** icon at the beginning of the ***Web-Segment*** line.
16. Click **Edit.**
17. Click the **Connectivity** drop down menu. 
18. From the menu, click **T1-GW-01**.
19. Click **SAVE**.
20. Click **CLOSE EDITING**.

#### Task 3

In this task, you ping T1-App-01 and T1-DB-01 from T1-Web-01 to verify network connectivity between VMs connected to different segments.

1. Click the **vSphere** tab in the web browser to open the vSphere Client UI.
2. In vCenter Server inventory, click the **T1-Web-01** virtual machine.
3. Verify the IP address of the T1-Web-01 virtual machine is 172.16.10.11, then click **Launch Web Console**.
4. **Press any key** to ping the T1-App-01 (172.16.20.11) from T1-Web-01.
5. Verify that the ping is successful, then **press any key** to ping the T1-DB-01 (172.16.30.11) virtual machine from T1-Web-01.
   This ping is also sucessful.

The simulation is now complete.

### Simulation: Connecting a Tier-1 Gateway to a Tier-0 Gateway and Verifying the External Connectivity

In this simulation you will log in to the NSX UI, navigate the inventory to locate the preconfigured Tier-0 Gateway, verify its successful deployment, connect T1-GW-01 to T0-GW-01, and ping T1-Web-01, T1-App-01, and T1-DB-01 to verify connectivity.

1. **Press any key** to confirm, using ping, that T1-Web-01 is not accesible from an external network. 

2. Click into the **NSX UI** browser tab.

3. Click the **Networking** tab at top of NSX UI.

4. From the left menu, click **Connectivity>Tier-0 Gateways.**

5. Review the Tier-0 Gateway details:

   - ***Tier-0 Gateway Name***: T0-GW-01
   - ***Linked Tier-1 Gateways***: 0
   - ***Status:*** Success

   When ready, click anywhere on screen to resume the simulation.

6. From the left menu, click **Tier-1 Gateways.**

7. Review the Tier-1 Gateway details:

   - ***Tier-1 Gateway Name***: T1-GW-01
   - ***Linked Tier-0 Gateway***: Not Set
   - ***#Linked Segments***: 3
   - ***Status***: Success

   When ready, click the number,

    

   3

   , of Linked Segments. 

8. Confirm that the ***App, DB*** and **Web** segments are connected to the Tier-1 Gateway, then click **CLOSE**.

9. Click the **three vertical elipse** icon at the beginning of the ***T1-GW-01*** line.

10. Click **Edit**.

11. Click the **Linked Tier-0 Gateway** drop down menu labeled *Select Tier-0 Gate.*

12. Click **T0-GW-01.**

13. Click **SAVE.**

14. Click **CLOSE EDITING.**

15. From the left menu, click **Tier-0 Gateways.**

16. Click the number, **1**, of Linked Tier-1 Gateways. 

17. Verify that the Tier-0 Gateway is linked to the T1-GW-01 Tier-1 Gateway, and then click **CLOSE**. 

18. Click the **Command Prompt** icon on the window task bar.

19. **Press any key** to confirm, using ping, external connectivity to T1-Web-01 (172.16.10.11).

20. **Press any key** to confirm external connectivity to T1-App-01 (172.16.20.11).

21. **Press any key** to confirm external connectivity to T1-DB-01 (172.16.30.11).

The simulation is now complete.

## Summary

NSX Logical Routing

*NSX-T Data Center uses Tier-1 and Tier-0 gateways to connect different networks and to connect your workloads to the Internet.*

*You can also connect your virtual machines and containers to Tier-1 and Tier-0 gateways and verify successful routing connectivity.*

## Knowledge Check

### Identifying the Use Cases for NSX-T Data Center Logical Routing

What are the uses cases for NSX-T Data Center logical routing?
Select the two options that best answer the question and click Submit.

- [ ] Provides intrinsic security for VMs connected to different segments.
- [x] Provide external connectivity to VMs and containers.
- [ ] Provides layer 2 connectivity between VMs and microservices.
- [x] Provide connectivity between VMs or containers connected to different segments.

### Use Case for Logical Routing

A team of software developers recently deployed a three-tier application that includes web servers, application servers, and database servers. These servers are currently connected to different segments.The junior network administrator must ensure that the servers of the three-tier application can communicate with each other. Users must also be able to access the three-tier application from the external network. A multitier deployment must be used.What are the steps that the administrator must perform to complete this task?

Select the two options that best answer the question and click **Submit**.

- [ ] Connect the three segments to a Tier-0 gateway from the NSX UI.

- [ ] Connect the three segments to the external router from the NSX UI.

- [x] Connect the three segments to a Tier-1 gateway from the NSX UI.

- [ ] Connect the Tier-1 gateway to the external router from the NSX UI.

- [x] Connect the Tier-1 gateway to the Tier-0 gateway from the NSX UI.