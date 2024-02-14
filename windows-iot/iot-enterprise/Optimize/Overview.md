---
title: Device Optimization Overview
titleSuffix: Windows IoT Enterprise
author: TerryWarwick
ms.author: twarwick
ms.date: 01/12/2024
ms.topic: article
ms.service: windows-iot
ms.subservice: iot
description: Windows IoT Enterprise Device Optimization Overview
keywords: IoT Enterprise, Overview, Optimization
---

# Device Optimization Overview

> [!WARNING]
> THIS IS AN IN-PROGRESS ROUGH DRAFT. The wording and feature list may change before publishing.

Applies to:  
✅ Windows 11 IoT Enterprise  
✅ Windows 10 IoT Enterprise  
✅ Windows 10 IoT Enterprise LTSC 2021  

Windows IoT Enterprise provides several features to help device makers create highly curated, fixed-function, specialized devices. In some cases, this includes optimization of storage and memory consumption. This article provides an overview of the optimization features available for Windows IoT Enterprise.

## Building an Optimized Device

Windows IoT Enterprise optimizations provide multiple approaches to tailor specialized device deployments by reducing storage and memory requirements of the operating system.  While Windows IoT Enterprise can use many optimization methods that are available to other editions of Windows, Windows IoT Enterprise has extra optimization methods designed for fixed-function specialized devices.

## Optimization features available to Windows IoT Enterprise

The features listed in this table have instructions written specific to Windows IoT Enterprise.

| Feature            | Description |
|--------------------|-------------|
| [Removable Packages](Removable-Packages.md)       | In addition to Features on Demand and Legacy Optional Components, Windows IoT Enterprise LTSC enables removal of more feature packages. |
| [Enable/Disable Services](Services.md)  | The Windows operating system includes many system services that are configured to start automatically, start manually or are disabled by default. Some services might not be required for specific fixed function devices and can be disabled, freeing up memory. |
| [Compact OS](CompactOS.md)  | Compact OS compresses the files for the entire operating system and lets you run it from the compressed files  to save disk space.  For more information, see [Compact command-line utility](/windows-server/administration/windows-commands/compact).</br>**Note:** Best to use with solid-state drives to compensate for performance impact. |
| [Soft Real-Time](../Soft-Real-Time/Soft-Real-Time.md) | When running a program, a normal operating system gives deterministic results but allows for a nondeterministic time to complete a task. In a real-time operating system both the results of program execution and the time taken to get those results are (at least partially) deterministic. |

## More optimization features available in Windows

The features listed in this table are available to Windows IoT Enterprise in addition to other editions, including Windows Professional and Windows Enterprise.

| Feature            | Description |
|--------------------|-------------|
| [Features On Demand](/windows-hardware/manufacture/desktop/features-on-demand-v2--capabilities) | Features on Demand (FODs) are Windows features that can be added at any time, such as [language packs](/windows-hardware/manufacture/desktop/features-on-demand-language-fod), network drivers, networking tools and wireless display. See also [Available Features on Demand](/windows-hardware/manufacture/desktop/features-on-demand-non-language-fod). |
| [Languages](/windows-hardware/manufacture/desktop/features-on-demand-language-fod)  | Many display languages and language features are also delivered as Features on Demand. You can save disk space by choosing not to include some language components in your image.|
| [Legacy Optional Features](/windows-hardware/manufacture/desktop/enable-or-disable-windows-features-using-dism) | Prior to the introduction of Features on Demand, Optional Features were offered through Control Panel - Turn Windows Features On or Off and many are still managed in this way. |
| [Add and Remove Drivers](/windows-hardware/manufacture/desktop/add-and-remove-drivers-to-an-offline-windows-image) | Remove unnecessary drivers.  |
| [Applications](https://support.microsoft.com/windows/uninstall-or-remove-apps-and-programs-in-windows-4b55f974-2cc6-2d2b-d092-5905080eaf98)       | Each application installed on the device after Windows is installed consumes storage for binaries, user data, logs, and updates. Removing unnecessary applications can free up storage for other purposes. |
| [Reserved Storage](/windows-hardware/manufacture/desktop/dism-storage-reserve)   | Windows reserves a portion of storage space on your device for use by temporary files, caches, and other files. When your device is low on space, Windows clears reserved storage so it can be used for other processes, like a Windows update. Reserved storage is configured as `disabled by default` on Windows IoT Enterprise, whereas it's `enabled by default` on other editions of Windows.  This setting can be changed at any time to optimize delivery of servicing updates. |
| [Hibernation](/windows/win32/power/system-power-states)       | Hibernation was designed for mobile computers and might not be available for all PCs. Hibernation uses a hibernation file to provide a fast startup experience. For more information, see [How to enable or disable hibernation](/troubleshoot/windows-client/deployment/disable-and-re-enable-hibernation). |
| [Page Files](/troubleshoot/windows-client/performance/introduction-to-the-page-file)        | Windows designates a section of the hard drive as virtual memory known as the page file, or more specifically, as pagefile.sys. Page Files supplement the computer’s Random Access Memory (RAM) to improve performance for frequently used programs and data. For more information, see [How to determine the appropriate page file size](/troubleshoot/windows-client/performance/how-to-determine-the-appropriate-page-file-size-for-64-bit-versions-of-windows) and [How can I change the size of a page file?](https://devblogs.microsoft.com/scripting/how-can-i-change-the-size-of-a-page-file/) </br>**Note:** Review [Peak system commit charge](/troubleshoot/windows-client/performance/how-to-determine-the-appropriate-page-file-size-for-64-bit-versions-of-windows) before disabling the pagefile. |
| [Single-Instancing](/windows-hardware/manufacture/desktop/compact-os#single-instancing-of-provisioning-packages)  | After DISM captures the non-system files to a compressed provisioning package, DISM adds pointers on the drive to the new compressed provisioning package, and removes the original files. As a result, the files are still visible to the system, but take up less space on the drive. For more information, see [DISM /Apply-CustomDataImage](/windows-hardware/manufacture/desktop/dism-provisioning-package-command-line-options#apply-customdataimage) </br>**Note:** Best to use with solid-state drives to compensate for performance impact. |
| [Component Store](/windows-hardware/manufacture/desktop/manage-the-component-store)    | The Windows Component Store is used to support the functions needed for the customization and updating of Windows. Previous versions of some components are kept on the system for a while, allowing you to roll back if necessary. For more information, see [Clean Up the WinSxS Folder](/windows-hardware/manufacture/desktop/clean-up-the-winsxs-folder). |
