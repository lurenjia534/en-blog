---
title: What is GKI
categories: Android
tags:
- Android
- Kernel
- GKI
---

### Getting to the Point: What is GKI

GKI stands for Generic Kernel Image, also known as Android Common Kernels.

### What's Its Purpose?

The purpose of GKI is to address Android fragmentation. Manufacturers often modify the kernel source code and add device drivers to provide support for System-on-Chips (SoCs) and peripheral devices. However, these modifications can be extensive, leading to a situation where up to 50% of the code running on a device is out-of-tree code (not from the upstream Linux and AOSP common kernels).
A device kernel consists of the following parts:
<!--more-->
Upstream: Linux kernel from kernel.org
AOSP: Additional Android-specific patches for the AOSP common kernel
Vendor: Support and optimization patches from the SoC vendor for their devices
OEM/Device: Additional device drivers and customizations
Google's Generic Kernel Image is the next step in addressing Android fragmentation.

Google has been striving to reduce Android fragmentation as many OEMs want to customize their devices, which slows down the update process across various devices. Google's projects like Project Treble and Project Mainline aimed to streamline updates. However, fragmentation still persisted, especially around the Linux kernel used by OEMs. Google's solution is the Generic Kernel Image (GKI). The goal of GKI is to isolate the customizations made by SoC vendors and OEMs, enabling Google to directly push kernel updates to users. Devices launching with Android 12 and running Linux kernel version 5.10.43 or higher will need to follow certain guidelines related to GKI. The Google Pixel 6 series became the first phones to feature GKI. Google's ultimate aim is to reduce the "technical debt" of out-of-tree code on Android devices by 2023.

### Core Objective

The core objective of GKI (Generic Kernel Image) is to segregate the custom code of OEMs and SoC vendors from the core kernel and move them into loadable modules often referred to as "vendor modules." This enables Google to push kernel updates directly to end users without waiting for OEMs or SoC vendors to make modifications or customizations. This greatly simplifies the updating process, enhances the security of Android devices, and helps mitigate Android fragmentation.

The ultimate goal is to achieve a universally applicable Android kernel, similar to the universal nature of the x86 architecture, without the need for extensive backward porting or modifications. GKI aims to universalize the Android kernel, much like the concept of a universal kernel for x86 architecture. By doing so, OEM-specific customizations and drivers from device manufacturers and SoC vendors are isolated in loadable modules rather than being directly integrated into the core kernel.

This implies that if a device ships with kernel version 5.10, for instance, and a new version like 6.x is released in the future, users or manufacturers could potentially update to the new kernel version without significant customization work. This significantly streamlines the updating process, allowing Android devices to receive kernel updates more swiftly and easily, while also enhancing device security and performance.

### Technical Principles

Modular Design: GKI employs a modular design by isolating custom code of SoC vendors and OEMs from the core kernel and moving it into loadable modules, known as "vendor modules."

Kernel Module Interface (KMI): KMI is a crucial component of GKI, defining a stable interface between the core kernel and vendor modules. This means that as long as these interfaces remain stable, vendor modules can seamlessly collaborate with new versions of the core kernel.

Android Common Kernel (ACK): Google forks an "Android Common Kernel" (ACK) from the mainline Linux kernel and adds Android-specific patches to it. SoC vendors like Qualcomm, MediaTek, and Samsung then fork kernels tailored for their specific SoCs from the ACK and might add additional patches. GKI's goal is to isolate these vendor-specific patches in the vendor modules as much as possible, rather than directly integrating them into the core kernel.

Update Mechanism: Google is working towards delivering GKI updates through the Play Store, which means that future kernel updates can be directly delivered through the Play Store, akin to app updates.

Specifications and Guidelines: To ensure device manufacturers adhere to GKI principles, Google has established a set of specifications and guidelines for devices running Android 12 and later.

Reducing Out-of-Tree Code: Another objective of GKI is to reduce the presence of "out-of-tree" code, which refers to code not present in the mainline Linux or AOSP common kernels. This simplifies the process of merging upstream changes and enhances device security.

In a nutshell, GKI and vendors communicate through the Kernel Module Interface (KMI) to address the fragmentation issue. When fully implemented, the GKI kernel becomes universal, with all SOC and OEM code residing in the vendor modules, thereby resolving the fragmentation problem.

Role of Project Treble: Project Treble is Google's initiative to address Android fragmentation. By separating the OS framework from vendor implementations (such as HALs and device-specific Linux kernel branches), it makes it easier for Android OEMs to rebuild their OS on top of the latest AOSP framework.

Aim of Project Mainline: Project Mainline aims to simplify the update process for Android components. Google achieves this by remotely pushing updates for critical OS components via the Google Play Store, eliminating the need to wait for OEMs to apply patches.

### Other Kernel Related Topics

...To be continued.
