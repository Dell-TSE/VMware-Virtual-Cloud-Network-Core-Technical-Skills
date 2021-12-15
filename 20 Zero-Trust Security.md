# Zero-Trust Security

## Learner Objectives

- Implement the Zero-Trust approach for security by using micro-segmentation

## Introduction

[VMBeans](https://core-vmware.bravais.com/api/dynamic/documentVersions/3657/files/72282/c4cdb738-c65e-45f3-96ff-280ea2ebed4a.html) *is ready to enforce tight security measures in its data centers.*

*You must implement a Zero-Trust security strategy where all traffic is verified. You must understand the micro-segmentation process to implement a Zero-Trust strategy to protect your company’s network.*

## About the Zero-Trust Approach for Security

Conventional security models assume that all users and components in an organization's network can be trusted.

The Zero-Trust model assumes the opposite: trust nothing and verify everything.

This architecture addresses the increased sophistication of network attacks and insider threats that frequently exploit the conventional approach to only secure the perimeter.

## Using Micro-Segmentation to Implement a Zero-Trust Approach

Micro-segmentation helps to build a Zero-Trust approach to security by defining a security perimeter around each application. This method prevents an attacker from moving in the data center.

### Step 1: Identify the application boundaries.

To build the zero-trust security data center, determine the VMs that contain an application and the network traffic that is necessary for the application to function.

![EnforcingtheZero-TrustSecurityModelofMicro-Segmentation_1](20%20Zero-Trust%20Security.assets/EnforcingtheZero-TrustSecurityModelofMicro-Segmentation_1.svg)

### Step 2: Create micro-segments.

When you understand an application’s composition and necessary network traffic, you can create micro-segmentation policies to restrict unnecessary network traffic. This step immediately reduces the attack surface of the application by restricting the application to only communicating with the resources that it absolutely needs.

![EnforcingtheZero-TrustSecurityModelofMicro-Segmentation_2](20%20Zero-Trust%20Security.assets/EnforcingtheZero-TrustSecurityModelofMicro-Segmentation_2.svg)

### Step 3: Secure through context.

Use security policies to establish how the virtual machines and containers should behave, including the processes that should be running and how the OS should be configured. This step secures the traffic and the context of the application.

![EnforcingtheZero-TrustSecurityModelofMicro-Segmentation_3](20%20Zero-Trust%20Security.assets/EnforcingtheZero-TrustSecurityModelofMicro-Segmentation_3.svg)

## Summary

Zero-Trust Security

*As a security administrator, you must understand how micro-segmentation helps implement a Zero-Trust security architecture, where nothing is trusted by default.*

## Knowledge Check

### Implementing a Zero-Trust model

What is the order of the steps to implement the Zero-Trust model?
Drag and drop the steps in the correct order.

1. Identify the application boundaries.
2. Create micro-segments.
3. Secure through context.

### Zero-Trust Security

Which NSX technology helps the security administrator to implement a Zero-Trust security architecture?
Select the option that best answers the question and click **Submit**.

- [x] Micro-segmentation
- [ ] Microservices
- [ ] Perimeter firewall
- [ ] Gateway firewall