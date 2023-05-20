---
title: Refresh IoT Enterprise Installation Media
author: TerryWarwick
ms.author: twarwick
ms.date: 05/19/2023
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Refresh Windows IoT Enterprise Instalation media
keywords: IoT Enterprise, Installation
---

# Refresh IoT Enterprise Installation Media

In this article, you set up your media refresh environment and gather all prerequisites that are required to update both the WinPE environment and the main operating system, install drivers

## Prepare Media Servicing Environment

1. Start PowerShell with Administrator privileges.
   We use this instance of PowerShell for the end to end process of servicing the installation media to apply updates and, if needed, incorporate required drivers that aren't part of the Windows installation media  
    1. Select **Start**
    1. Type PowerShell
    1. Right-click **Windows PowerShell**
    1. Select **Run as administrator**

1. Create **MediaRefresh** folder to store the files needed for servicing the installation media, using the PowerShell command New-Item.

    ```Powershell
    New_Item -Path "c:\" -Name "MediaRefresh" -ItemType "directory"
    ```

### Copy files from original media

1. Create an **ISO** folder under **MediaRefresh** along with both an **In** and **Out** child folders.  The **In** folder to store a copy of the files from the original installation media. As you proceed through this article, the updated installation files are written to the **Out** folder.

    ```Powershell
    New-Item -Path "c:\MediaRefresh" -Name "ISO" -ItemType "directory"
    New-Item -Path "c:\MediaRefresh\ISO" -Name "In" -ItemType "directory"
    New-Item -Path "c:\MediaRefresh\ISO" -Name "Out" -ItemTYpe "directory"
    ```

1. Complete the following steps of this section based on the type of your original media.  
   **ISO file:** Complete steps 3, 4 and 5.  
   **Physical DVD:** Complete step 4.

1. Mount the Windows IoT Enterprise installation ISO and display the mounted drive letter.

   ```Powershell
   Mount-DiskImage -ImagePath <full path to ISO file> | Get-Volume
   ```

   Make note of the DriveLetter as we'll need to use it in the next step.

1. Copy files from the original installation media to both ```c:\MediaRefresh\ISO\In``` and ```c:\MediaRefresh\ISO\Out``` folders using Robocopy. You'll update The files in the ```Out``` folder.  The ```In``` folder is used as a backup in case you need to overwrite the files in the ```Out``` folder to start over without remounting the ISO.

   ```powershell
   robocopy <DriveLetter>:\ c:\MediaRefresh\ISO\Out /e
   robocopy <DriveLetter>:\ c:\MediaRefresh\ISO\In /e
   ```

1. Dismount the Windows IoT Enterprise installation ISO using [Dismount-Diskimage](/powershell/module/storage/dismount-diskimage)

   ```powershell
   Dismount -ImagePath <full path to ISO file>  
   ```

### Gather servicing packages

1. Create a **packages** folder under **MediaRefresh** which will be used to store Windows update packages that will apply the current servicing packages

    ```Powershell
    New_Item -Path "c:\MediaRefresh" -Name "packages" -ItemType "directory"
    ```

1. Download any cumulative updates and their dependencies that you wish to incorporate into your updated installation media and place the Microsoft Servicing Update (MSU) files into this folder. The table below will help you locate updates for your specific version.

   | Release | Version |  Update History | Windows Update Catalog |
   | --- | --- | --- | --- |
   | Windows&nbsp;10&nbsp;IoT&nbsp;Enterprise&nbsp;LTSC&nbsp;2021 |  19044 | [Show&nbsp;update&nbsp;history](https://support.microsoft.com/topic/windows-10-update-history-857b8ccb-71e4-49e5-b3f6-7073197d98fb)  | [Show&nbsp;x64&nbsp;updates](https://www.catalog.update.microsoft.com/Search.aspx?q=-Dynamic%20Cumulative%20Update%20for%20Windows%2010%20Version%2021H2%20for%20x64) [Show&nbsp;Arm64&nbsp;updates](https://www.catalog.update.microsoft.com/Search.aspx?q=-Dynamic%20Cumulative%20Update%20for%20Windows%2010%20Version%2021H2%20for%20Arm64) |
   | Windows&nbsp;10&nbsp;IoT&nbsp;Enterprise&nbsp;LTSC&nbsp;2019 |   17763 | [Show&nbsp;update&nbsp;history](https://support.microsoft.com/topic/windows-10-and-windows-server-2019-update-history-725fc2e1-4443-6831-a5ca-51ff5cbcb059) | [Show&nbsp;x64&nbsp;updates](https://www.catalog.update.microsoft.com/Search.aspx?q=-Dynamic%20Cumulative%20Update%20for%20Windows%2010%20Version%201809%20for%20x64) [Show&nbsp;Arm64&nbsp;updates](https://www.catalog.update.microsoft.com/Search.aspx?q=-Dynamic%20Cumulative%20Update%20for%20Windows%2010%20Version%201809%20for%20Arm64) |
   | Windows&nbsp;10&nbsp;IoT&nbsp;Enterprise&nbsp;LTSC&nbsp;2016 |   14393 | [Show&nbsp;update&nbsp;history](https://support.microsoft.com/topic/windows-10-and-windows-server-2016-update-history-4acfbc84-a290-1b54-536a-1c0430e9f3fd) | [Show&nbsp;x64&nbsp;updates](https://www.catalog.update.microsoft.com/Search.aspx?q=-Dynamic%20Cumulative%20Update%20for%20Windows%2010%20version%201607%20for%20x64) [Show&nbsp;x86&nbsp;updates](https://www.catalog.update.microsoft.com/Search.aspx?q=-Dynamic%20Cumulative%20Update%20for%20Windows%2010%20version%201607%20for%20x86) |
   | Windows&nbsp;10&nbsp;IoT&nbsp;Enterprise&nbsp;LTSC&nbsp;2015 |   10240 |  [Show&nbsp;update&nbsp;history](https://support.microsoft.com/topic/windows-10-update-history-93345c32-4ae1-6d1c-f885-6c0b718adf3b)              | [Show&nbsp;x64&nbsp;updates](https://www.catalog.update.microsoft.com/Search.aspx?q=-Dynamic%20Cumulative%20Update%20for%20Windows%2010%20version%201507%20for%20x64) [Show&nbsp;x86&nbsp;updates](https://www.catalog.update.microsoft.com/Search.aspx?q=-Dynamic%20Cumulative%20Update%20for%20Windows%2010%20version%201507%20for%20x64) |

### Gather third party drivers

1. Create a **drivers** folder for third party drivers to be added to the OS image.

    ```Powershell
    New_Item -Path "c:\MediaRefresh" -Name "drivers" -ItemType "directory"
    ```

1. Copy the drivers that are required for your device into the *c:/MediaRefresh/drivers* folder. Drivers may be stored in separate folders but it isn't necessary.

### Gather configuration scripts

1. Create a **scripts** folder to store scripts that will be executed during setup to complete installation and configuration of components that need additional configuration.

    ```Powershell
    New_Item -Path "c:\MediaRefresh" -Name "drivers" -ItemType "directory"
    ```

   For more information, see [Add a Custom Script to Windows Setup](/windows-hardware/manufacture/desktop/add-a-custom-script-to-windows-setup)

## Update Windows Preinstallation Environment (WinPE)

The Windows Preinstallation Environment (WinPE) is contained within ```boot.wim``` on the original installation media under the ```\sources``` folder.  In this section, we'll walk through the process of updating the ```boot.wim``` with the latest cumulative servicing update and incorporate third party drivers if needed into the WinPE environment using the [Media Servicing Environment](#prepare-media-servicing-environment) set up earlier.

### Prerequisites for Updating WinPE

| Directory | Contents |
| --- | --- |
| c:\mediarefresh\ | No file contents|
| c:\mediarefresh\iso\in | Copy of original installation media |
| c:\mediarefresh\iso\out | Copy of original installation media |
| c:\mediarefresh\packages | Microsoft Servicing Update (MSU) files from Microsoft Update Catalog |
| c:\mediarefresh\drivers | Third party drivers |

### Mount Windows Preinstall Environment (WinPE) boot.wim

```powershell
New-Item -Path "c:\mediarefresh\" -Name "Mounted" -ItemType "directory"
Mount-WindowsImage -ImagePath "c:\mediarefresh\iso\out\sources\boot.wim" -Index 2 -Path "c:\mediarefresh\Mounted"
```

```powershell
Add-WindowsDriver -Path "c:\mediarefresh\Mounted" -Driver "c:\mediarefresh\drivers" -Recurse -ForceUnsigned
```

```powershell
Add-WindowsPackage -Path "c:\mediarefresh\mounted" -PackagePath "c:\mediarefresh\packages" 
```

REM note if error 0x800f0823 occurs on the previous command, try running it a second time

```powershell
Copy-Item "c:\mediarefresh\mounted\sources\setup.exe" -Destination "c:\mediarefresh\iso\out\sources\setup.exe"
```

```powershell
Dismount-WindowsImage -path "c:\mediarefresh\mounted" -save
Remove-item c:\mediarefresh\mounted
```

## Update Windows IoT Enterprise

The Windows IoT Enterprise image is contained within ```install.wim``` on the original installation media under the ```\sources``` folder.  In this section we'll walk through the process of updating the ```install.wim``` with the latest cumulative servicing update and incorporate third party drivers if needed by the target device using the [Media Servicing Environment](#prepare-media-servicing-environment) set up earlier.

### Prerequisites for updating Windows IoT Enterprise

| Directory | Contents |
| --- | --- |
| c:\mediarefresh | no file contents|
| c:\mediarefresh\iso\in | Copy of original installation media |
| c:\mediarefresh\iso\out | Copy of original installation media |
| c:\mediarefresh\packages | Microsoft Servicing Update (MSU) files from Microsoft Update Catalog |
| c:\mediarefresh\drivers | Third party drivers |

### Mount install.wim to update operating system image

```powershell
New-Item -Path "c:\mediarefresh\" -Name "Mounted" -ItemType "directory"
Mount-WindowsImage -ImagePath "c:\mediarefresh\iso\out\install.wim" -Index 2 -Path "c:\mediarefresh\mounted"
```

### Inject third party drivers

```powershell
Add-WindowsDriver -Path "c:\mediarefresh\mounted" -Driver "c:\mediarefresh\drivers" -Recurse -ForceUnsigned
```

### Inject setupcomplete.cmd

```powershell
New-Item -Path "c:\mediarefresh\mounted\windows\setup\" -Name "Scripts" -ItemType "directory"
Copy-Item "c:\mediarefresh\scripts\*.cmd" -Destination "c:\mediarefresh\mounted\windows\setup\scripts"
```

### Apply servicing packages

```powershell
Add-WindowsPackage -Path "c:\mediarefresh\mounted" -PackagePath "c:\mediareresh\packages" 
```

### Save and dismount updated install.wim

```powershell
Dismount-WindowsImage -path "c:\mediarefresh\mounted" -save
Remove-item c:\mediarefresh\mounted
```

### Split WIM to support FAT32 file system

```powershell
Split-WindowsImage -ImagePath "c:\mediarefresh\iso\out\sources\install.wim" -SplitImagePath "c:\mediarefresh\iso\out\sources\install.swm" -FileSize 4000 -CheckIntegrity
```

### Remove Install.wim

```powershell
Remove-item c:\mediarefresh\mounted\install.wim
```

## Other Resources

* [Update Windows installation media with Dynamic Update](/windows/deployment/update/media-dynamic-update)
* [Windows boot and installation overview](/windows-hardware/manufacture/desktop/boot-and-install-windows)
