---
title: XHibernate Once/Resume Many (HORM)
author: TerryWarwick
ms.author: twarwick
ms.date: 03/09/2023
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Learn about the Hibernate Once/Resume Many (HORM) Feature in Windows IoT Enterprise.
keywords: Lockdown, HORM
---

# XHibernate Once/Resume Many (HORM)

A device with HORM enabled can quickly be turned off or shut down, and then restarted into the previously defined state, even in the event of a sudden power loss.

## Configure HORM

You can use the [Hibernate Once/Resume Many (HORM)](/windows-hardware/customize/enterprise/hibernate-once-resume-many-horm-) feature with [Unified Write Filter (UWF)](Unified-Write-Filter.md) to start your device in a previously defined state. When HORM is enabled, your system always resumes and restarts from the last saved hibernation file (hiberfil.sys).

## UWF configuration

UWF must be enabled before you can enable or disable HORM. UWF must be configured in the following ways to protect the hibernation file from becoming invalid:

* All fixed volumes that are mounted on the system must be protected with UWF.
* Your system must not have any file, folder, or registry exclusions configured for UWF.
* The UWF overlay must be configured to use RAM mode. HORM does not support disk-backed overlays.

UWF does not filter hibernation files from being written to disk. If you want to protect the previously defined state state of your device, lock down any functionality that can modify the hibernation file. For example, disable hibernation, hybrid sleep, and fast startup on your device for standard user accounts so that the saved hibernation file is not overwritten when entering sleep, hibernate, or shutdown state.

To disable hybrid sleep and fast startup on your device, follow [these steps](/windows-hardware/customize/enterprise/hibernate-once-resume-many-horm-#how-to-disable-hybrid-sleep).

To configure the UWF with HORM, check out this [guide](/windows-hardware/customize/enterprise/hibernate-once-resume-many-horm-#configure-horm).
