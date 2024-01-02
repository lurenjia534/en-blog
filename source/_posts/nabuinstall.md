---
title: How to Install AOSP ROM on Xiaomi Mi Pad 5
data: 2023-09-30
categories: ROM
tags:
    - ROM
    - Xiaomi
    - Xiaomi Mi Pad 5
---

## Prerequisites

- MIUI 14 firmware or MIUI 14 ROM
- Back up all apps, images, videos, contacts, etc. to cloud or external storage
- Latest [platform-tools](https://developer.android.com/tools/releases/platform-tools)
- Unlocked bootloader and [Arrow Recovery](https://sourceforge.net/projects/kubersharma001/files/nabu/ArrowOS-Recovery/)
<!--more-->

## Flashing Arrow Recovery

Ensure that you have booted into Fastboot mode.

### *For Windows cmd Users*

```bash
    fastboot -w # This will wipe and restore all data partitions on the device
```

#### **Flash boot.img and vendor_boot.img from Windows cmd**

```bash
    fastboot flash boot boot.img # Flash boot.img
    fastboot flash vendor_boot vendor_boot.img # Flash vendor_boot.img
```

### *For Powershell Users*

```bash
    .\fastboot.exe -w # This will wipe and restore all data partitions on the device
```

#### **Flash boot.img and vendor_boot.img from Windows Powershell**

```bash
    .\fastboot.exe flash boot boot.img # Flash boot.img
    .\fastboot.exe flash vendor_boot vendor_boot.img # Flash vendor_boot.img
```

## Reboot into Arrow Recovery and Verify Proper Connection to Recovery

*Note: There is an issue with the recovery of Xiaomi Pad 5 not being able to present the UI panel, but recovery works normally.*

For Windows cmd users:

```bash
    fastboot reboot recovery # Tells your device to reboot to recovery
```

For Windows Powershell users:

```bash
    .\fastboot.exe reboot recovery # Tells your device to reboot to recovery
```

### Verify Connection

For Windows cmd users:

```bash
    adb devices # This should display your device connection
```

For Windows Powershell users:

```bash
    .\adb.exe devices # This should display your device connection
```

## Flash the ROM

Now that you have successfully flashed the recovery:

### Reboot to Sideload mode

For Windows cmd users:

```bash
    adb reboot sideload # This should reboot to sideload
```

For Windows Powershell users:

```bash
    .\adb.exe reboot sideload # This should reboot to sideload
```

### ADB Sideload ROM

For Windows cmd users:

```bash
    adb sideload romfile.zip # Flash the ROM via sideload
```

For Windows Powershell users:

```bash
    .\adb.exe sideload romfile.zip # Flash the ROM via sideload
```

### Wipe Data and Reboot, then Enjoy

For Windows cmd users:

```bash
    adb shell # Enters the shell mode of the device
    recovery --wipe_data # Wipes data in shell mode
    adb reboot # Reboots to system
```

For Windows Powershell users:

```bash
    .\adb.exe shell # Enters the shell mode of the device
    recovery --wipe_data # Wipes data in shell mode
    .\adb.exe reboot # Reboots to system
```
