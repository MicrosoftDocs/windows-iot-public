---
title: How to set up a Device for Real-Time Performance
author: TerryWarwick
ms.author: twarwick
ms.date: 03/30/2023
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Soft Real-Time Device set-up on Windows 10 IoT Enterprise
keywords: IoT Enterprise, Soft Real-Time
---

# How to set up a Device for Real-Time Performance

This guide walks you through how to set up your device for real-time performance.

> [!NOTE]
>
> The only way to use this feature is with an application and device custom-built for a specific purpose. The mapping of processor core assignments in the application threads must match the physical device cores and their configuration for real-time versus standard workloads.  

1. Disable idle states with `powercfg.exe`
1. Reference the [Security guidelines for system services](/windows-server/security/windows-services/security-guidelines-for-disabling-system-services-in-windows-server) to disable the following services:

   1. SysMain (Superfetch)
   1. DPS (Diagnostic Policy Service)
   1. Audiosrv (Windows Audio)

1. Disable Windows Update using [this guidance](/windows/privacy/manage-connections-from-windows-operating-system-components-to-microsoft-services#bkmk-wu).

   > [!NOTE]
   >
   > This will open up your device to vulnerabilities as security patches will not go through. That said, it is necessary as the Windows Update agent does not respect CPU core isolation. We recommend having a plan to ensure device security and install updates during times when the device can be taken down for maintenance

   >[!TIP]
   >
   > A good example of managing updates during downtime can be found in the UWF documentation: [Service UWF-protected devices](/windows-hardware/customize/enterprise/service-uwf-protected-devices) If you are using UWF and Soft Real-time then this process should take care of the OS update need for both features at the same time.

1. Set the [WindowsIoT CSP](#what-is-the-windowsiot-csp) for real-time performance.
1. Configure RSS to migrate ISRs/DPCs to CPU0

   > [!NOTE]
   > This is hardware dependent and can only be done if the NIC supports RSS

1. **Optional:** [Disable threaded DPCs](/windows-hardware/drivers/kernel/introduction-to-threaded-dpcs) for debugging
1. **Optional:** Deploying a custom DPC pinning driver for certain hardware interrupts by following [this guidance](/windows-hardware/drivers/kernel/guidelines-for-writing-dpc-routines).

## Performing this Configuration from the Command Line

This configures the device while powered on. To ensure that the device maintains soft-RT performance, you should configure the machine to run these commands as a script every time the machine powers on using [this guidance](https://aka.ms/SRT-GPS).

1. Run these two commands in a cmd prompt. This disables CPU idle states, where a CPU with no instructions to run will enter a power-saving state. This is undesirable in real-time scenarios as idle CPUs have a delay in starting to execute new instructions:

   ```console
   powercfg.exe /setacvalueindex SCHEME_CURRENT SUB_PROCESSOR IdleDisable 1
   powercfg.exe /setactive SCHEME_CURRENT
   ```

2. Run these three commands in a cmd prompt to disable DPS:

   ```console
   sc query dps
   sc stop dps
   sc config dps start=disabled
   ```

3. Run these three commands in a cmd prompt to disable Audiosrv:

   ```console
   sc query Audiosrv
   sc stop Audiosrv
   sc config Audiosrv start=disabled
   ```

4. Run these three commands in a cmd prompt to disable SysMain:

   ```console
   sc query SysMain
   sc stop SysMain
   sc config SysMain start=disabled
   ```

5. Run these three commands in a cmd prompt to disable Windows Update:

   ```console
   sc query wuauserv
   sc stop wuauserv
   sc config wuauserv start=disabled
   ```

6. Run this command to disable threaded DPCs

   ```console
   reg add "HKLM\System\CurrentControlSet\Control\Session Manager\kernel" /v ThreadDpcEnable /t REG_DWORD /f /d 0
   ```

## Ensuring the Device Stays Set up for Real-Time

Before you deploy a real-time device to a production environment, there's other setup needed to ensure the device can receive updates and maintain real-time performance:

- Set up a script that can reenable Windows Update, install updates, and turn off Windows Update once again
- Set up checks to ensure that on-device services remain disabled

## What is the WindowsIoT CSP?

The `WindowsIoT CSP` is used to configure Windows IoT devices. Currently the only functionality available in this CSP is to configure a device for Soft Real-Time performance. This isn't the only work that needs to be done in order to use soft real-time with a device. You must also perform the previous six steps. Using this CSP to set soft real-time cores without also performing this extra configuration work results in system malfunction and requires reimaging to recover.

The hierarchy of this CSP is as follows:

```txt
WindowsIoT
   SoftRealTimeProperties
      SetRTCores
```

A value greater than 0 and less than the total number of cores on the device must be provided to the SetRTCores parameter. Feel free to set this CSP using whatever tool your organization uses to configure their devices or use the steps below to use the MDM Bridge.

### Use MDM Bridge WMI Provider to Configure the WindowsIoT CSP

This CSP configures the system for real-time performance. You need to provide the number of CPU cores to allocate to real-time tasks, with the rest being allocated for running system or standard user tasks. A numerical value must be provided in the SetRTCores node. This is the number of CPU Cores dedicated to real-time workloads. Valid numeric values must be at least 1 and less than the number of physical cores in the CPU.  

Environments that use Windows Management Instrumentation (WMI) can use the MDM Bridge WMI Provider to accomplish this. Here's an example to set the RealTime configuration with three real-time cores:

1. Download the [psexec tool](/sysinternals/downloads/psexec).
1. Run an administrative command prompt.
1. In the command prompt, launch PowerShell under system account `psexec.exe -s -i powershell.exe`
1. Execute the following script:

   ```console
   $nameSpaceName="root\cimv2\mdm\dmmap"
   $className="MDM_WindowsIoT_SoftRealTimeProperties01"
   $obj = Get-CimInstance -Namespace $namespaceName -ClassName $className
   Add-Type -AssemblyName System.Web
   Set-CimInstance -CimInstance $obj
   $obj.SetRTCores = 3
   Set-CimInstance -CimInstance $obj
   ```

1. Restart the machine to activate the change.

>[!TIP]
>
> You can use the same script for whatever number of real-time cores you need to have, just replacing the 3 in the second-to-last line with the appropriate number. This will reserve cores starting with the highest core and going downwards. So reserving 3 cores on a 4 core CPU will reserve cores 3, 2, and 1 and leave core 0 for system and non-real-time tasks. Please note that there's no guarantee that the real-time cores are going to remain highest, since the real-time core indices will remain fixed if increasing the CPU core count afterwards.

Next: [Develop a Soft Real-Time Application](/windows/iot/iot-enterprise/soft-real-time/soft-real-time-application)
