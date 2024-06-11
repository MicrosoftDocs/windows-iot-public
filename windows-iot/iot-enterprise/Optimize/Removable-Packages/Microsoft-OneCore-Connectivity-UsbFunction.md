---
title: Package - USB Function Driver
titleSuffix: Windows IoT Enterprise
author: TerryWarwick
ms.author: twarwick
ms.date: 05/22/2024
ms.topic: reference
ms.service: windows-iot
ms.subservice: iot
description: Removable Package Details for USB Function Driver
keywords: IoT Enterprise, removable packages, storage
---

# USB Function Driver

Applies to:  
✅ Windows 11 IoT Enterprise LTSC 2024  
⛔ Windows 10 IoT Enterprise LTSC 2021

## Package Description

Package: **Microsoft-OneCore-Connectivity-UsbFunction** </br>  UFX, UFX Synopsis Events. For more information, see [Overview of developing Windows drivers for USB function controllers](/windows-hardware/drivers/usbcon/developing-windows-drivers-for-usb-function-controllers) and [Overview of developing Windows applications for USB devices](/windows-hardware/drivers/usbcon/developing-windows-applications-that-communicate-with-a-usb-device).

> [!IMPORTANT]
>
> This feature is only supported on the Windows IoT Enterprise LTSC edition.  If you choose to remove any of this package from Windows IoT Enterprise, you must ensure that your solution does not rely on functionality of the removed package. You cannot restore the package without a full reinstall of Windows IoT Enterprise LTSC.  
> For more information, see [Removable Packages System Requirements](../Removable-Packages.md#system-requirements).

## Package Removal

1. To remove a specific package from the image type:

   ```powershell
   Dism.exe /Online /NoRestart /Disable-Feature /FeatureName:Microsoft-OneCore-Connectivity-UsbFunction /PackageName:@Package
   ````

   To remove a package from an offline image mounted at `c:\offline` type:

   ```powershell
   Dism.exe /Image:c:\offline  /Disable-Feature /FeatureName:Microsoft-OneCore-Connectivity-UsbFunction /PackageName:@Package
   ```

1. Optional: Use DISM /GetFeatureInfo to get the status of a removable package type:

   ```powershell
   Dism.exe /Online /Get-FeatureInfo /FeatureName:Microsoft-OneCore-Connectivity-UsbFunction /PackageName:@Package
   ````

## Package Details

### Package Size

| Release                             |   x64     |    ARM64    |
|-------------------------------------|:---------:|:-----------:|
| Windows 11 IoT Enterprise LTSC 2024 | 762 KB    | 646 KB      |

### File List

| File Name | Installed Location |
|-----------|--------------------|
| genericusbfn.inf | %windir%\system32\driverstore\filerepository\genericusbfn.inf_amd64_253b6957ba775622\genericusbfn.inf |
| ufxchipidea.inf | %windir%\system32\driverstore\filerepository\ufxchipidea.inf_amd64_1a8f9d49db4bf636\ufxchipidea.inf |
| ufxsynopsys.inf | %windir%\system32\driverstore\filerepository\ufxsynopsys.inf_amd64_4ed1fada2f2925e8\ufxsynopsys.inf |
| genericusbfn.sys | %windir%\system32\driverstore\filerepository\genericusbfn.inf_amd64_253b6957ba775622\genericusbfn.sys |
| ufx01000.sys | %windir%\system32\drivers\ufx01000.sys |
| ufxchipidea.sys | %windir%\system32\driverstore\filerepository\ufxchipidea.inf_amd64_1a8f9d49db4bf636\ufxchipidea.sys |
| ufxsynopsys.sys | %windir%\system32\drivers\ufxsynopsys.sys |

## Related Content

- [Removable Packages](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages)
- [Reduce Disk Footprint](/windows/iot/iot-enterprise/Optimize-Your-Device/Reduce-Disk-Footprint)
- [Device Optimization Overview](/windows/iot/iot-enterprise/Optimize-Your-Device/Overview)
