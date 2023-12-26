---
title: "Build Android use Shell"
date: 2023-12-27
categories: ["Android", "Smartphones"]
tags: ["ROM", "Open-source"]
---

## Build fastboot Rom shell

```bash
    mka updatepackage # this will all threads build fastboot rom
```

## Build recovery Rom shell

```bash
    mka bacon -j$(nproc --all) # -jx is number of thread   ,$(nproc --all) is all thread
```

## flash rom

if fastboot rom

```bash
    fastboot -w # clean data and cache
    fastboot update <rom.zip> # flash
```

if recovery rom

```bash
    fastboot reboot recovery # reboot to recovery
    adb sideload <rom.zip> # sideload rom
```

