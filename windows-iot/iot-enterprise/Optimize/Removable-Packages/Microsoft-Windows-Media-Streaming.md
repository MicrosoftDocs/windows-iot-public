---
title: Package - Windows Media Streaming
titleSuffix: Windows IoT Enterprise
author: twarwick
ms.author: twarwick
ms.date: 01/31/2024
ms.topic: article
ms.service: windows-iot
ms.subservice: iot
description: Removable Package Details for Microsoft-Windows-Media-Streaming
keywords: IoT Enterprise, removable packages, storage
---

# windows Media Streaming

| Applies to                          |  Version            |
|:------------------------------------|:--------------------|
| Windows 10 IoT Enterprise LTSC 2021 | 19044.1741 or later |

## Description

A component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) providing support for [Windows Media Streaming](/windows/win32/mediastreaming/media-streaming-api-portal).

**Package Name:**  Microsoft-Windows-Media-Streaming

**Size:** Approximately 6,644 KB

> [!IMPORTANT]
>
> This feature is only supported on the Windows IoT Entrprise LTSC edition.  If you choose to remove any of this package from Windows IoT Enterprise, you must ensure that your solution does not rely on functionality of the removed package. You cannot restore the package without a full reinstall of Windows IoT Enterprise LTSC.  
> For more information, see [Removable Packages System Requirements](../Removable-Packages.md#system-requirements).

## Package Removal

1. To remove a specific package from the image type:

   ```powershell
   Dism.exe /Online /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-Media-Streaming /PackageName:@Package
   ````

   To remove a package from an offline image mounted at `c:\offline` type:

   ```powershell
   Dism.exe /Image:c:\offline  /Disable-Feature /FeatureName:Microsoft-Windows-Media-Streaming /PackageName:@Package
   ```

1. Optional: Use DISM /GetFeatureInfo to get the status of a removable package type:

   ```powershell
   Dism.exe /Online /Get-FeatureInfo /FeatureName:Microsoft-Windows-Media-Streaming /PackageName:@Package
   ````

## Related Packages

These packages collectively provide the functionality represented by the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture).  There are dependencies between each of these packages.  If you elect to remove a subset of these packages, it is recommended that you thoroughly test your scenarios to ensure that your customers do not encounter the interaction between the packages you retain and the packages that you remove.

- [Microsoft-Media-Foundation](Microsoft-Media-Foundation.md)
- [Microsoft-Windows-Media-Format](Microsoft-Windows-Media-Format.md)
- [Microsoft-Windows-Media-Streaming](Microsoft-Windows-Media-Streaming.md)
- [Microsoft-Windows-MediaPlayback-OC](Microsoft-Windows-MediaPlayback-OC.md)
- [Microsoft-Windows-Portable-Devices](Microsoft-Windows-Portable-Devices.md)
- [Microsoft-Windows-WebcamExperience](Microsoft-Windows-WebcamExperience.md)
- [Microsoft-Windows-WinSATMediaFiles](Microsoft-Windows-WinSATMediaFiles.md)

## File List

| File Name                         | Installed Location |
|-----------------------------------|--------------------|
| castingshellext.dll               | %windir%\system32\castingshellext.dll |
| dlnashext.dll                     | %windir%\system32\dlnashext.dll |
| dmrserver.dll                     | %windir%\system32\dmrserver.dll |
| mdeserver.exe                     | %windir%\system32\mdeserver.exe |
| playtoreceiver.dll                | %windir%\system32\playtoreceiver.dll |
| windows.media.streaming.dll       | %windir%\system32\windows.media.streaming.dll |
| windows.media.streaming.ps.dll    | %windir%\system32\windows.media.streaming.ps.dll |
| winmde.dll                        | %windir%\system32\winmde.dll |
| wmpdmc.exe                        | %windir%\system32\wmpdmc.exe |
| wmpdui.dll                        | %windir%\system32\wmpdui.dll |

## More Resources

- [Removable Packages](../Removable-Packages.md)
- [Device Optimization Overview](../Overview.md)
