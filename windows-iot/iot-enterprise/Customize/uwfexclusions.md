---
title: Common write filter exclusions
description: Common write filter exclusions
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: cbae7b49-23b0-4232-91d7-b61b2adc8cd5
author: TerryWarwick
ms.author: twarwick
ms.prod: windows-iot
ms.technology: iot
ms.date: 10/02/2018
ms.topic: article


---
# Write filter exclusions

You can add specific files or folders on a protected volume to a file exclusion list to exclude those files and folders from being filtered by UWF. When a file or folder is in the exclusion list for a volume, all writes to that file or folder bypass UWF filtering, and are written directly to the protected volume and persist after the device restarts.

You must use an administrator account to add or remove file or folder exclusions during run time, and you must restart the device for new exclusions to take effect.

> [!IMPORTANT]
> Don't add exclusions for the following:
>
> - \Windows\System32\config\DEFAULT
> - \Windows\System32\config\SAM
> - \Windows\System32\config\SECURITY
> - \Windows\System32\config\SOFTWARE
> - \Windows\System32\config\SYSTEM
> - \Users\<User Name>\NTUSER.DAT
> - \Windows\BOOTSTAT.DAT
> - %System Drive%\EFI\Microsoft\Boot\BOOTSTAT.DAT
> - %System Drive%\Boot\BOOTSTAT.DAT
>
> Also, don't add exclusions for the following:
>
> - The volume root. For example, C: or D:.
> - The `\Windows` folder on the system volume.
> - The `\Windows\System32` folder on the system volume.
> - The `\Windows\System32\Drivers` folder on the system volume.
> - Paging files.
>
> Adding an exclusion for any of these items is unsupported and may lead to unpredictable results.
> It's OK to exclude subdirectories and files under these locations.
>
> Folders need to exist prior to adding them to the exclusion list.
>

You cannot rename or move a file or folder from a protected location to an unprotected location, or vice versa. When write filters are active and you attempt to delete an excluded file or folder in Windows Explorer, the system attempts to move the file or folder to the Recycle Bin. This causes an error, because you cannot move files that are not filtered to a location that is write filter protected.

To work around this, you can disable the Recycle Bin. Alternatively, the user can press Ctrl+Shift and then left-click on the file to directly delete the excluded file, bypassing the Recycle Bin, or the user can delete the excluded file directly from a command prompt. You must restart the device for new exclusions to take effect.

## Virtual Hard Disk (VHD) file exclusions

When you deploy a Windows 10 Enterprise image with UWF on a VHD boot disk, you can protect the volume that contains the VHD file by adding a file exclusion for the VHD file before enabling UWF and protecting the volume.

To add a file exclusion for the VHD file at an administrator command prompt:

```cmd
uwfmgr.exe file add-exclusion <drive containing VHD file>:\<path to VHD file>\<VHD file name>.vhd
```

For example:

```cmd
uwfmgr.exe file add-exclusion E:\VHD\test.vhd
```

## Registry exclusions

You can add specific registry keys to an exclusion list to exclude those keys from being filtered by UWF. When a registry key is in the exclusion list, all writes to that registry key bypass UWF filtering and are written directly to the registry and persist after the device restarts.

You must use an administrator account to add or remove registry exclusions during run time, and you must restart the device for new exclusions to take effect.

If you exclude a registry key, all its subkeys are also excluded from filtering. You can exclude registry subkeys only under the following registry keys:

- `HKEY\LOCAL\MACHINE\BCD00000000`
- `HKEY\LOCAL\MACHINE\SYSTEM`
- `HKEY\LOCAL\MACHINE\SOFTWARE`
- `HKEY\LOCAL\MACHINE\SAM`
- `HKEY\LOCAL\MACHINE\SECURITY`
- `HKEY\LOCAL\MACHINE\COMPONENTS`

> [!IMPORTANT]
> Don't add exclusions for the following:
>
> - `HKLM\SECURITY\Policy\Secrets\$MACHINE.ACC`

> [!NOTE]
> UWF automatically excludes certain registry keys from being filtered. These registry keys are primarily related to UWF configuration settings and cannot be removed from the exclusion list.

For more information about common registry exclusions, see [Common write filter exclusions](uwfexclusions.md).

## Common write-filter exclusions

Some services and features write information to a device’s persistent volume, and expect that information to be present across device restarts. You may need to configure your write filter to allow for specific file and registry exclusions in order for these services and features to work correctly.

This topic lists registry and file exclusions that can help enable some common services and features to work correctly when write filters are enabled.

If you are running any antivirus or security software in addition to UWF, please consult with your antivirus vendor for advice on how to configure their solution in a UWF environment. You may need to add a UWF exclusion for the signature or update folder.

### Customer Experience Improvement Program (CEIP)

When you choose to participate in the CEIP, your computer or device automatically sends information to Microsoft about how you use certain products. Information from your computer or device is combined with other CEIP data to help Microsoft solve problems and to improve the products and features customers use most often.

CEIP data is stored in files that have a .sqm file name extension. To make sure that the CEIP data in the .sqm files is available on a device that has write filters enabled, you can add file and folder exclusions for the .sqm files and folders.

To locate the .sqm files and folders on your device, search for .sqm files by using File Explorer. Alternately, at a command prompt with administrator rights at the root of the drive, type the following command to obtain a list of .sqm files on the device:

```powershell
dir *.sqm /s
```

Add file and folder exclusions as required for any .sqm files located on your device.

Add registry exclusions for the following registry keys:

- `HKEY_LOCAL_MACHINE\Software\Policies\Microsoft\SQMClient\Windows\CEIPEnable`
- `HKEY_LOCAL_MACHINE\Software\Microsoft\SQMClient\Windows\CEIPEnable`
- `HKEY_LOCAL_MACHINE\Software\Microsoft\SQMClient\UploadDisableFlag`

### Background Intelligent Transfer Service (BITS)

Background Intelligent Transfer Service (BITS) downloads or uploads files between a client and server and provides progress information related to the transfers.

Add file exclusions for the following folders and files:

- `%ALLUSERSPROFILE%*\Microsoft\Network\Downloader`

Add registry exclusions for the following registry keys:

- `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\BITS\StateIndex`

### Windows Explorer

When write filters are active and you attempt to delete an excluded file or folder in Windows Explorer, the system attempts to move the file or folder to the Recycle Bin. This causes an error, because you cannot move files that are not filtered to a location that is write filter protected.

To work around this, you can disable the Recycle Bin. Alternatively, the user can press Ctrl+Shift and then left-click on the file to directly delete the excluded file, bypassing the Recycle Bin, or the user can delete the excluded file directly from a command prompt.

### Networks

When you use write filters on your device, you can add file and registry exclusions to enable your device to join wired and wireless networks. The following file and registry exclusions may be required on your device.

Client Group Policy Object (GPO) registry keys:

- Wireless: `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\Wireless\GPTWirelessPolicy`
- Wired: `HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\WiredL2\GP_Policy`

GPO policy files:

- Wireless: `C:\Windows\wlansvc\Policies`
- Wired: `C:\Windows\dot2svc\Policies`

Interface profile registry keys:

- Wireless: `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\wlansvc`
- Wired: `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\dot3svc`

Interface policy file:

- Wireless: `C:\ProgramData\Microsoft\wlansvc\Profiles\Interfaces\{***&lt;Interface GUID&gt;***}\{***&lt;Profile GUID&gt;***}.xml`
- Wired: `C:\ProgramData\Microsoft\dot3svc\Profiles\Interfaces\{***&lt;Interface GUID&gt;***}\{***&lt;Profile GUID&gt;***}.xml`

Services registry keys:

- Wireless: `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\Wlansvc`
- Wireless: `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\WwanSvc`
- Wired: `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\services\dot3svc`

> [!IMPORTANT]
> Folders need to exist prior to adding them to the exclusion list.
>

### Daylight saving time (DST)

You can add the following registry exclusions to persist daylight saving time (DST) settings on your device.

- `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Time Zones`
- `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\TimeZoneInformation`

## Related topics

- [Unified Write Filter](unified-write-filter.md)
- [Service UWF-protected devices](service-uwf-protected-devices.md)
- [Unified Write Filter WMI provider reference](uwf-wmi-provider-reference.md)
