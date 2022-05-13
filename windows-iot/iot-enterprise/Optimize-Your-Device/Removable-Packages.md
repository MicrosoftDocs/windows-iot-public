---
title: Removable Packages
author: rsameser
ms.author: riameser
ms.date: 5/11/2022
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Windows IoT Enterprise feature to assist with reducing disk footprint
keywords: IoT Enterprise, removable packages, storage
---

# Removable Packages
The removable packages feature enables Windows IoT Enterprise device builders to use DISM to permanently remove specific optional packages that may not be needed for the OEM’s device use case, such as printer drivers and fonts. These packages are explicitly tagged as 'OEM removable' by Microsoft and ensure that feature OS updates do not restore the removed packages. This helps OEMs optimize their device and reduce their overall disk footprint.

Note: This is an exclusive feature for OEMs using the Windows IoT Enterprise LTSC 2021. Since this feature was not included in the base 2021 LTSC image, please apply the latest LCU package to enable this functionality.

We recommend using removable packages in combination with other [disk size reduction features] available on Windows IoT Enterprise. Windows IoT OEMs are responsible for testing configurations for their devices prior to deployment.

## Types of Packages
This feature explicitly marks packages as 'removable' if they have limited use case in IoT device scenarios and minimal dependencies on system functionality. The removable optional package tags on Windows IoT Enterprise LTSC will also be applied to the Media Foundation Packages (matching NSKU).

To see the full list of the packages available to be removed, download the [PowerShell script] and run the following command:


```powershell
.\RemoveOnIoTEnterpriseS.ps1 -List
```

To display each unit of the removable packages vertically, use the following query:

```powershell
.\RemoveOnIoTEnterpriseS.ps1 -List | ft -Wrap -Property Name, @{Expression={$_.Packages -join "'r'n"};Name="Packages"}
```

## How to Remove Packages Offline
1. Mount EnterpriseS WIM or VHD.

```powershell
dism.exe /Mount-Image /ImageFile: 20257.1.201106-1554.fe_release_CLIENT_ENTERPRISES_OEM_x64FRE_en-us.vhd /Index:1 /MountDir:offline
```

2. Set Edition to IoTEnterpriseS.

```powershell
dism.exe /Image:offline /Set-Edition:IoTEnterpriseS
```

3. Make other offline image customizations as needed, such as uninstalling FoDs.

4. Run [RemoveOnIoTEnterpriseS.PS1] in offline mode to remove a removal unit of your choice, and answer when prompted for confirmation to proceed. Use the removal unit name to indicate which set you want to remove.

'''powershell
Set-ExecutionPolicy -ExecutionPolicy Unrestricted

$VerbosePreference = "Continue"

RemoveOnIoTEnterpriseS.ps1 -offlineImageFolderPath .\offline\ -RemoveUnit IIS
'''

5. Offline WinSxS cleanup

```powershell
dism.exe /Image:offline /Cleanup-Image /StartComponentCleanup
```

6. Commit and Unmount  

```powershell
dism.exe /unmount-image /MountDir:offline /Commit
```

### How to remove all supported packages at once - offline
Use '-List' command piped to foreach in which '-RemoveUnit' command with '-suppressPrompts' is executed.

```powershell
RemoveOnIoTEnterpriseS.ps1 -List | foreach { .\RemoveOnIoTEnterpriseS.ps1 -offlineImageFolderPath .\offline\ -suppressPrompts -RemoveUnit $_.Name }
```

## How to remove packages online
1. Install the Windows IoT Enterprise LTSC 2021 via Setup or boot up VHD.

2. At OOBE, enter Audit Mode. Please visit here to learn how to enter Audit Mode.

3. Make other image customizations as needed.

4. Set Edition to IoTEnterpriseS.
```powershell
dism -online /Set-Edition:IoTEnterpriseS /AcceptEula  
```

4. Run RemoveOnIoTEnterpriseS.PS1 in online mode to remove a removal unit of your choice, and answer when prompted for confirmation to proceed. Use the removal unit name to indicate which set you want to remove.

```powershell
Set-ExecutionPolicy -ExecutionPolicy Unrestricted

$VerbosePreference = "Continue"

RemoveOnIoTEnterpriseS.ps1 -isOnline -RemoveUnit IIS

5. Reboot your device  

6. WinSxS cleanup

```powershell
dism.exe /Online /Cleanup-Image /StartComponentCleanup
```

7. Test your application scenarios on this image

8. Capture the generalized image via Sysprep. Please visit here to learn to generalize from Audit Mode.

## How to remove all supported packages at once - online
Use '-List' command piped to foreach in which '-RemoveUnit' command with '-suppressPrompts' is executed.

```powershell
RemoveOnIoTEnterpriseS.ps1 -List | foreach { .\RemoveOnIoTEnterpriseS.ps1 -isOnline -suppressPrompts -RemoveUnit $_.Name }
