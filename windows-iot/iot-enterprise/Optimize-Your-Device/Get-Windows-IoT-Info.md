---
title: Get Windows IoT Enterprise Edition, Version and Build
author: twarwick
ms.author: twarwick
ms.date: 12/7/2022
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Windows IoT Enterprise edition, version and build
keywords: IoT Enterprise, removable packages, storage
---

# Get Windows IoT Enterprise Edition, Version and Build

| Long Name                      | Short Name     | ID (Dec) | ID (Hex) |
|--------------------------------|----------------|----------|----------|
| Windows 10 IoT Enterprise      | IoTEnterprise  |  188     |
| Windows 10 IoT Enterprise LTSC | IoTEnterpriseS |  191     |

## Usign PowerShell

1. Click *Start*, type *PowerShell*, right-click *Windows PowerShell*, and then click *Run as administrator*.  We will use this session of PowerShell throughout this topic.
>
1. Use the Powershell command [Get-WindowsEdition](https://learn.microsoft.com/powershell/module/dism/get-windowsedition) to verify your edition.  
>>```powershell
>>Get-WindowsEdition -Online
>>```
>>This command displays the name of the current edition of the running Windows operating system.
>>```powershell
>>Get-WindowsEdition -Path "c:\offline"
>>```
>>This command displays the name of the edition for the mounted Windows image at c:\offline.
>
>### 1.3. Check your Windows build version with PowerShell
>>
>>```powershell
>>(Get-CimInstance Win32_OperatingSystem).Version + "." + (Get-ItemProperty -Path 'HKLM:\SOFTWARE\Microsoft\Windows NT\CurrentVersion').ubr
>>```
>>This command displays the build version and update build revision.  

## Using Command Shell
### Option 1: ver.exe
```cmd
ver
```


### Option 2: winver.exe
```cmd
winver
```
## Using User Interface



## Using an Offline Image
>Checking the version of an offline image is beyond the scope of this topic however if your offline image is Windows 10 IoT Enterprise LTSC 2021 you will need to install [KB5014023](https://support.microsoft.com/topic/june-2-2022-kb5014023-os-builds-19042-1741-19043-1741-and-19044-1741-preview-65ac6a5d-439a-4e88-b431-a5e2d4e2516a) or a more recent cumulative update to ensure your image satisfies the minimum build requirement of 19044.1741 or later.  [Add Updates to a Windows image](https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/servicing-the-image-with-windows-updates-sxs) will guide you through this process.