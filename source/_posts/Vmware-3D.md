---
title: "VMware 3D"
date: 2024-2-27
categories: ["Vmware", "virtual machine"]
tags: ["Vmware", "3D acceleration", "Arch Linux"]
---

## Essay

Essay

After installing Arch, I found that VMware's 3D acceleration was not enabled.

However, in Settings - Hardware - Display - 3D Graphics - Accelerate 3D Graphics, it was already checked.

Then I came across this [Enable 3D HW acceleration on VMWare Workstation 10 on Ubuntu 14.04](https://askubuntu.com/questions/537787/enable-3d-hw-acceleration-on-vmware-workstation-10-on-ubuntu-14-04) solution.

It just required adding a line of configuration.

Open

```shell
vim ~/.vmware/preferences
```

Add

```shell
mks.gl.allowBlacklistedDrivers = "TRUE"
```

But what truly amazed me is that this answer is already **nine years old**.

From Ubuntu 14.04 LTS - vmware-workstation-10 to the current Ubuntu 22.04 LTS - vmware-workstation-17, it **still works**.
