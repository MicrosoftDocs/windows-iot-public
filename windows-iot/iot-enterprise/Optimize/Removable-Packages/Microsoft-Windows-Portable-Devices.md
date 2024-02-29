---
title: Package - Windows Portable Devices
titleSuffix: Windows IoT Enterprise
author: TerryWarwick
ms.author: twarwick
ms.date: 02/13/2024
ms.topic: article
ms.service: windows-iot
ms.subservice: iot
description: Removable Package Details for Microsoft-Windows-Portable-Devices
keywords: IoT Enterprise, removable packages, storage
---

# Windows Portable Devices

Applies to:  
✅ Windows 11 IoT Enterprise LTSC 2024  
✅ Windows 10 IoT Enterprise LTSC 2021 (19044.1741 or later)  

## Package Description

Package: **Microsoft-Windows-Portable-Devices** </br> A component of the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture) providing connectivity to portable devices for [Windows Media Device Manager](/windows/win32/wmdm/windows-media-device-manager-architecture).

> [!IMPORTANT]
>
> This feature is only supported on the Windows IoT Entrprise LTSC edition.  If you choose to remove any of this package from Windows IoT Enterprise, you must ensure that your solution does not rely on functionality of the removed package. You cannot restore the package without a full reinstall of Windows IoT Enterprise LTSC.  
> For more information, see [Removable Packages System Requirements](../Removable-Packages.md#system-requirements).

## Package Removal

1. To remove a specific package from the image type:

   ```powershell
   Dism.exe /Online /NoRestart /Disable-Feature /FeatureName:Microsoft-Windows-Portable-Devices /PackageName:@Package
   ````

   To remove a package from an offline image mounted at `c:\offline` type:

   ```powershell
   Dism.exe /Image:c:\offline  /Disable-Feature /FeatureName:Microsoft-Windows-Portable-Devices /PackageName:@Package
   ```

1. Optional: Use DISM /GetFeatureInfo to get the status of a removable package type:

   ```powershell
   Dism.exe /Online /Get-FeatureInfo /FeatureName:Microsoft-Windows-Portable-Devices /PackageName:@Package
   ````

## Related Packages

These packages collectively provide the functionality represented by the [Media Feature Pack](/windows/win32/wmdm/windows-media-device-manager-architecture). There are dependencies between each of these packages. If you elect to remove a subset of these packages, you must thoroughly test your scenarios to ensure that your customers don't encounter an issue with missing dependencies.

- [Microsoft-Media-Foundation](Microsoft-Media-Foundation.md)
- [Microsoft-Windows-Media-Format](Microsoft-Windows-Media-Format.md)
- [Microsoft-Windows-Media-Streaming](Microsoft-Windows-Media-Streaming.md)
- [Microsoft-Windows-MediaPlayback-OC](Microsoft-Windows-MediaPlayback-OC.md)
- [Microsoft-Windows-Portable-Devices](Microsoft-Windows-Portable-Devices.md)
- [Microsoft-Windows-WebcamExperience](Microsoft-Windows-WebcamExperience.md)
- [Microsoft-Windows-WinSATMediaFiles](Microsoft-Windows-WinSATMediaFiles.md)

## Package Details

### Package Size

| Release                             |   x64     |    ARM64    |
|-------------------------------------|:---------:|:-----------:|
| Windows 11 IoT Enterprise LTSC 2024 | 6,830 KB  | 7,979 KB    |
| Windows 10 IoT Enterprise LTSC 2021 | 6,405 KB  |             |

### File List

| File Name                         | Installed Location |
|-----------------------------------|--------------------|
| bthmtpenum.mof                    | %windir%\system32\wbem\bthmtpenum.mof |
| bthmtpenum.sys                    | %windir%\system32\drivers\bthmtpenum.sys |
| bthmtpenum.inf                    | %windir%\inf\bthmtpenum.inf |
| c_wpd.inf                         | %windir%\inf\c_wpd.inf |
| wpdcomp.inf                       | %windir%\inf\wpdcomp.inf |
| wpdfs.inf                         | %windir%\inf\wpdfs.inf |
| wpdmtp.inf                        | %windir%\inf\wpdmtp.inf |
| wpdmtphw.inf                      | %windir%\inf\wpdmtphw.inf |
| portabledeviceapi.dll             | %windir%\system32\portabledeviceapi.dll |
| portabledeviceapi.mof             | %windir%\system32\wbem\portabledeviceapi.mof |
| portabledeviceclassextension.dll  | %windir%\system32\portabledeviceclassextension.dll |
| portabledeviceclassextension.mof  | %windir%\system32\wbem\portabledeviceclassextension.mof |
| portabledeviceconnectapi.dll      | %windir%\system32\portabledeviceconnectapi.dll |
| portabledeviceconnectapi.mof      | %windir%\system32\wbem\portabledeviceconnectapi.mof |
| portabledevicestatus.dll          | %windir%\system32\portabledevicestatus.dll |
| portabledevicestatus.dll.mun      | %windir%\systemresources\portabledevicestatus.dll.mun |
| portabledevicetypes.dll           | %windir%\system32\portabledevicetypes.dll |
| portabledevicetypes.mof           | %windir%\system32\wbem\portabledevicetypes.mof |
| portabledevicewiacompat.dll       | %windir%\system32\portabledevicewiacompat.dll |
| portabledevicewiacompat.mof       | %windir%\system32\wbem\portabledevicewiacompat.mof |
| sqmapi.dll                        | %programfiles%\windows portable devices\sqmapi.dll |
| wpd_ci.dll                        | %windir%\system32\wpd_ci.dll |
| wpd_ci.mof                        | %windir%\system32\wbem\wpd_ci.mof |
| wpdbusenum.dll                    | %windir%\system32\wpdbusenum.dll |
| wpdbusenum.mof                    | %windir%\system32\wbem\wpdbusenum.mof |
| wpdcomp.dll                       | %windir%\system32\drivers\umdf\wpdcomp.dll |
| wpdcomp.mof                       | %windir%\system32\wbem\wpdcomp.mof |
| wpdfs.dll                         | %windir%\system32\drivers\umdf\wpdfs.dll |
| wpdfs.mof                         | %windir%\system32\wbem\wpdfs.mof |
| wpdmtp.dll                        | %windir%\system32\wpdmtp.dll |
| wpdmtp.mof                        | %windir%\system32\wbem\wpdmtp.mof |
| wpdmtpbt.dll                      | %windir%\system32\wpdmtpbt.dll |
| wpdmtpdr.dll                      | %windir%\system32\drivers\umdf\wpdmtpdr.dll |
| wpdmtpip.dll                      | %windir%\system32\wpdmtpip.dll |
| wpdmtpus.dll                      | %windir%\system32\wpdmtpus.dll |
| wpdshext.dll                      | %windir%\system32\wpdshext.dll |
| wpdshext.dll.mun                  | %windir%\systemresources\wpdshext.dll.mun |
| wpdshext.mof                      | %windir%\system32\wbem\wpdshext.mof |
| wpdshextautoplay.exe              | %windir%\system32\wpdshextautoplay.exe |
| wpdshserviceobj.dll               | %windir%\system32\wpdshserviceobj.dll |
| wpdshserviceobj.mof               | %windir%\system32\wbem\wpdshserviceobj.mof |
| wpdsp.dll                         | %windir%\system32\wpdsp.dll |
| wpdsp.mof                         | %windir%\system32\wbem\wpdsp.mof |
| wpdupfltr.sys                     | %windir%\system32\drivers\wpdupfltr.sys |

## More Resources

- [Removable Packages](../Removable-Packages.md)
- [Device Optimization Overview](../Overview.md)
