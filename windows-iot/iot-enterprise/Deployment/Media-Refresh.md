---
title: Refresh IoT Enterprise Installation Media
author: TerryWarwick
ms.author: twarwick
ms.date: 10/20/2023
ms.topic: article
ms.service: windows-iot
ms.subservice: iot
description: Refresh Windows IoT Enterprise Installation media
keywords: IoT Enterprise, Installation
---

# Refresh IoT Enterprise Installation Media

In this article, you set up your media refresh environment and gather all prerequisites that are required to update both the WinPE environment and the main operating system, install drivers

## Prepare Media Servicing Environment

1. **Start PowerShell with Administrator privileges.**  
   We use this instance of PowerShell for the end to end process of servicing the installation media to apply updates and, if needed, incorporate required drivers that aren't part of the Windows installation media  
    - Select **Start**
    - Type PowerShell
    - Right-click **Windows PowerShell**
    - Select **Run as administrator**

1. **Create folders to store files during media servicing**  
   Use the PowerShell command [New_Item](/powershell/module/microsoft.powershell.management/new-item#example-2-create-a-directory) to create the following folders on your technician PC to store files needed during media servicing.

   **c:\MediaRefresh**: Parent folder for storing files during media servicing.  
   **c:\MediaRefresh\Out**: Copy of the original media updated during servicing.  
   **c:\MediaRefresh\Packages\LCU**: Latest Cumulative Update
   **c:\MediaRefresh\Packages\SSU**: Servicing Stack Update if necessary  
   **c:\MediaRefresh\Drivers**: Third-party drivers.  
   **c:\MediaRefresh\Scripts**: Custom install scripts.
   **c:\MediaRefresh\WIM**: Working directory for updating boot.wim and install.wim

   ```Powershell
   md c:\MediaRefresh\Drivers
   md c:\MediaRefresh\Out
   md c:\MediaRefresh\Packages\LCU
   md c:\MediaRefresh\Packages\SSU
   md c:\MediaRefresh\Scripts
   md c:\MediaRefresh\WIM
   ```

1. **Copy files from original media**  
  Copy all files from the original installation media to `c:\MediaRefresh\Out`.

   1. Proceed to step `b.` if you have physical media,  otherwise you must first mount the Windows IoT Enterprise installation ISO using [Mount-DiskImage](/powershell/module/storage/mount-diskimage) and display the resulting mounted drive letter using [Get-Volume](/powershell/module/storage/get-volume).

      ```Powershell
      Mount-DiskImage -ImagePath <ISO Path> | Get-Volume
      ```

      Where `<ISO Path>` is a fully qualified path to your ISO

      Make note of the DriveLetter as we'll need to use it in the next step.

   1. Copy files from the original installation media denoted here by `<DriveLetter>` to  `c:\MediaRefresh\Out` folder using [Robocopy](https://social.technet.microsoft.com/wiki/contents/articles/52831.robocopy-complete-reference.aspx).

      ```powershell
      robocopy <DriveLetter>:\ c:\MediaRefresh\Out /Copy:DT /e
      ```

      Where `<DriveLetter>` is the drive letter associated with the mounted ISO file

   1. Move boot.wim and install.wim from `c:\MediaRefresh\Out\Sources` to `c:\MediaRefresh\WIM` folder, the working folder for updating the WIM files, using [Robocopy](https://social.technet.microsoft.com/wiki/contents/articles/52831.robocopy-complete-reference.aspx).

      ```powershell
      robocopy c:\mediarefresh\out\sources c:\MediaRefresh\WIM *.wim /Mov
      ```

   1. Proceed to next step if you didn't mount an ISO for the previous command, otherwise you must first dismount the Windows IoT Enterprise installation ISO using [Dismount-Diskimage](/powershell/module/storage/dismount-diskimage)

      ```powershell
      Dismount-DiskImage -ImagePath <ISO Path>  
      ```

      Where `<ISO Path>` is a fully qualified path to your ISO file.

1. **Gather servicing packages**  

   Download the latest cumulative Microsoft Servicing Update (MSU) file to the `c:\MediaRefresh\Packages\LCU` folder.

   If a Servicing Stack Update (MSU) dependency is required, download it to `c:\MediaRefresh\Packages\SSU` folder. Use the following table to help you locate updates for your specific version of Windows IoT Enterprise.

   | Release | Version |  Update History | Update Catalog |
   | --- | --- | --- | --- |
   | Windows&nbsp;10&nbsp;IoT&nbsp;Enterprise&nbsp;LTSC&nbsp;2021 |  19044 | [Show&nbsp;update&nbsp;history](https://support.microsoft.com/topic/windows-10-update-history-857b8ccb-71e4-49e5-b3f6-7073197d98fb)  | [Show&nbsp;x64&nbsp;updates](https://www.catalog.update.microsoft.com/Search.aspx?q=-Dynamic%20Cumulative%20Update%20for%20Windows%2010%20Version%2021H2%20for%20x64) </br> [Show&nbsp;ARM64&nbsp;updates](https://www.catalog.update.microsoft.com/Search.aspx?q=-Dynamic%20Cumulative%20Update%20for%20Windows%2010%20Version%2021H2%20for%20Arm64) |
   | Windows&nbsp;10&nbsp;IoT&nbsp;Enterprise&nbsp;LTSC&nbsp;2019 |   17763 | [Show&nbsp;update&nbsp;history](https://support.microsoft.com/topic/windows-10-and-windows-server-2019-update-history-725fc2e1-4443-6831-a5ca-51ff5cbcb059) | [Show&nbsp;x64&nbsp;updates](https://www.catalog.update.microsoft.com/Search.aspx?q=-Dynamic%20Cumulative%20Update%20for%20Windows%2010%20Version%201809%20for%20x64) </br> [Show&nbsp;ARM64&nbsp;updates](https://www.catalog.update.microsoft.com/Search.aspx?q=-Dynamic%20Cumulative%20Update%20for%20Windows%2010%20Version%201809%20for%20Arm64) |
   | Windows&nbsp;10&nbsp;IoT&nbsp;Enterprise&nbsp;LTSC&nbsp;2016 |   14393 | [Show&nbsp;update&nbsp;history](https://support.microsoft.com/topic/windows-10-and-windows-server-2016-update-history-4acfbc84-a290-1b54-536a-1c0430e9f3fd) | [Show&nbsp;x64&nbsp;updates](https://www.catalog.update.microsoft.com/Search.aspx?q=-Dynamic%20Cumulative%20Update%20for%20Windows%2010%20version%201607%20for%20x64)</br> [Show&nbsp;x86&nbsp;updates](https://www.catalog.update.microsoft.com/Search.aspx?q=-Dynamic%20Cumulative%20Update%20for%20Windows%2010%20version%201607%20for%20x86) |
   | Windows&nbsp;10&nbsp;IoT&nbsp;Enterprise&nbsp;LTSC&nbsp;2015 |   10240 |  [Show&nbsp;update&nbsp;history](https://support.microsoft.com/topic/windows-10-update-history-93345c32-4ae1-6d1c-f885-6c0b718adf3b) | [Show&nbsp;x64&nbsp;updates](https://www.catalog.update.microsoft.com/Search.aspx?q=-Dynamic%20Cumulative%20Update%20for%20Windows%2010%20version%201507%20for%20x64) </br> [Show&nbsp;x86&nbsp;updates](https://www.catalog.update.microsoft.com/Search.aspx?q=-Dynamic%20Cumulative%20Update%20for%20Windows%2010%20version%201507%20for%20x64) |

1. **[Optional] Gather third party drivers**  
   Place the third-party drivers required for your device in an uncompressed format into the root of `c:/MediaRefresh/drivers` folder or as subfolders to `c:/MediaRefresh/drivers`.

1. **[Optional] Gather configuration scripts**  
   Place your `Setupcomplete.cmd` and `ErrorHandler.cmd` custom scripts that run during or after the Windows Setup process into the `c:\MediaRefresh\Scripts` folder.

   For more information, see [Add a Custom Script to Windows Setup](/windows-hardware/manufacture/desktop/add-a-custom-script-to-windows-setup)

## Update Windows Preinstallation Environment (WinPE)

The Windows Preinstallation Environment (WinPE) is contained within `boot.wim` on the original installation media under the `\sources` folder.  In this section, we walk through the process of updating the `boot.wim` with the latest cumulative servicing update and incorporate third party drivers if needed into the WinPE environment using the [Media Servicing Environment](#prepare-media-servicing-environment).

1. **Mount WinPE boot.wim**  
   1. The first step in updating the WinPE environment is to create a temporary folder named `mounted` under `c:\mediarefresh` using the PowerShell command [New-Item](/powershell/module/microsoft.powershell.management/new-item#description)

      ```powershell
      MD c:\MediaRefresh\mounted
      ```

   1. Before we can update the `boot.wim`, we need to make sure that its file attribute isn't set to ReadOnly.  Use the PowerShell command Set-ItemProperty to remove the ReadOnly attribute.

      ```powershell
      Set-ItemProperty -Path "c:\mediarefresh\wim\boot.wim" -Name IsReadOnly -Value $false
      ```

   1. Now we can mount the WinPE image stored in `boot.wim` at index 2 using the PowerShell command [Mount-WindowsImage](/powershell/module/dism/mount-windowsimage#description)

      ```powershell.wim" -Name IsReadOnly -Value $false
      Mount-WindowsImage -ImagePath "c:\mediarefresh\wim\boot.wim" -Index 2 -Path "c:\mediarefresh\Mounted"
      ```

   1. The contents of the WinPE image stored in the `boot.wim` at index 2 is now viewable at `c:\mediarefresh\mounted`.

1. **Apply third-party drivers to WinPE**  
   Install third-party drivers you collected in the `c:\mediarefresh\drivers` folder to WinPE at `c:\mediarefresh\mounted` using the PowerShell command [Add-WindowsDriver](/powershell/module/dism/add-windowsdriver#description).

   > [!NOTE]
   > For testing purposes you can use `-ForceUnsigned` to add unsigned drivers and override the requirement that drivers must have a digital signature. For more information about driver signing requirements, see [Device Drivers and Deployment Overview](/windows-hardware/manufacture/desktop/device-drivers-and-deployment-overview).

    ```powershell
   Add-WindowsDriver -Path "c:\mediarefresh\Mounted" -Driver "c:\mediarefresh\drivers" -Recurse
   ```

1. **Apply servicing updates to WinPE**  
   Apply the latest cumulative update and its dependencies that you downloaded to `c:\mediarefresh\packages` folder to WinPE at `c:\mediarefresh\mounted` using the PowerShell command [Add-WindowsPackage](/powershell/module/dism/add-windowspackage#description).  This process may take several minutes to complete, however it ensures that your Windows image already has the latest servicing update applied.

   1. First apply the servicing stack update dependency.

      ```powershell
      Add-WindowsPackage -Path "c:\mediarefresh\mounted" -PackagePath "c:\mediarefresh\packages\SSU"
      ```

   1. Now apply the latest cumulative update.

      ```powershell
      Add-WindowsPackage -Path "c:\mediarefresh\mounted" -PackagePath "c:\mediarefresh\packages\LCU"
      ```

   > [!TIP]
   > If you encounter error 0x800f0823, your servicing update may have a dependency that must be applied first. If you already downloaded its dependency, try running the above command a second time.  If this does not resolve the issue you may need to download an additional prerequisite for your update.
   >
   > - Make note of the KB####### in the filename of the update in c:\mediarefresh\packages.
   > - Search *[support.microsoft.com](https://support.microsoft.com)* with the KB#######
   > - Open the first topic that matches and search for the term "prerequisite".
   > - Download any prerequisites mentioned and run the above command again.  Note, you may need to run the command twice in order to allow the prerequisite to applied first.
   > - Continue to next step once error has been resolved.

1. **Copy updated `Setup.exe`**  
   Before continuing copy the updated `setup.exe` from WinPE at `c:\mediarefresh\mounted\sources` to `c:\mediarefresh\out\sources` using [Robocopy](https://social.technet.microsoft.com/wiki/contents/articles/52831.robocopy-complete-reference.aspx).
  
   1. First we need to remove the ReadOnly attribute on `c:\mediarefresh\mounted\sources\setup.exe` using the PowerShell command Set-ItemProperty.

      ```powershell
      Set-ItemProperty -Path "c:\mediarefresh\out\sources\setup.exe" -Name IsReadOnly -Value $false
      ```

   1. Now we can copy `setup.exe` from `c:\mediarefresh\mounted\sources` to `c:\mediarefresh\out\sources` using [Robocopy](https://social.technet.microsoft.com/wiki/contents/articles/52831.robocopy-complete-reference.aspx).

      ```powershell
      robocopy c:\mediarefresh\mounted\sources c:\mediarefresh\out\sources setup.exe
      ```

1. **Dismount and save changes to WinPE**  

   To complete the servicing process, use the PowerShell command [Dismount-WindowsImage](/powershell/module/dism/dismount-windowsimage#description) to save the changes.  

   > [!IMPORTANT]
   > Before executing the `Dismount-WindowsImage` command, make sure you do not have any File Explorer views or command windows that are viewing contents under `c:\mediarefresh\mounted`.  Failure to do so will result in an error when attempting to dismount.

   ```powershell
   Dismount-WindowsImage -path "c:\mediarefresh\mounted" -save
   ```

1. **Delete temporary folder**  

   Upon successful dismounting of the boot.wim, now we can remove the temporary folder `c:\mediarefresh\mounted` using the PowerShell command [Remove-Item](/powershell/module/microsoft.powershell.management/rename-item#description)

   ```powershell
   RD c:\MediaRefresh\mounted
   ```

1. **Publish `Boot.wim` to `out` folder**
  
   Now copy the updated `boot.wim` from `c:\mediarefresh\wim` to `c:\mediarefresh\out\sources` using [Robocopy](https://social.technet.microsoft.com/wiki/contents/articles/52831.robocopy-complete-reference.aspx).

      ```powershell
      robocopy c:\mediarefresh\wim c:\mediarefresh\out\sources boot.wim
      ```

The Windows Preinstall Environment (WinPE) stored as `boot.wim` and `setup.exe` both located under `c:\mediarefresh\out\sources\` are fully updated.

## Update Windows IoT Enterprise

The Windows IoT Enterprise image is contained within `install.wim` on the original installation media under the `\sources` folder.  In the [Prepare Media Servicing Environment](#prepare-media-servicing-environment) section, we moved `install.wim` into a working folder.  In this section, we walk through the process of updating the `install.wim` with the latest cumulative servicing update and incorporate third party drivers if needed by the target device using the [Media Servicing Environment](#prepare-media-servicing-environment). Once the update is complete, split the `install.wim` into smaller `*.swm` files so that they can be copied to a flash drive formatted as FAT32.

1. **Mount the OS install.wim**  
   1. The first step in updating the WinPE environment is to create a temporary folder named `mounted` under  `c:\mediarefresh` using the PowerShell command [New-Item](/powershell/module/microsoft.powershell.management/new-item#description).

      ```powershell
      MD c:\MediaRefresh\mounted
      ```

   1. Before we can update the install.wim, we need to make sure that its file attribute isn't set to ReadOnly.  Use the PowerShell command Set-ItemProperty to remove the ReadOnly attribute.

      ```powershell
      Set-ItemProperty -Path "c:\mediarefresh\wim\install.wim" -Name IsReadOnly -Value $false
      ```

   1. Now we can mount the Windows IoT Enterprise image stored in install.wim at index 2 using the PowerShell command [Mount-WindowsImage](/powershell/module/dism/mount-windowsimage#description)

      ```powershell
      Mount-WindowsImage -ImagePath "c:\mediarefresh\wim\install.wim" -Index 2 -Path "c:\mediarefresh\Mounted"
      ```

   1. The contents of the Windows IoT Enterprise image store in install.wim at index 2 is now viewable at `c:\mediarefresh\mounted`.

1. **Install third-party drivers**  
   Install third-party drivers you collected in the `c:\mediarefresh\drivers` folder to the OS image at `c:\mediarefresh\mounted` using the PowerShell command [Add-WindowsDriver](/powershell/module/dism/add-windowsdriver#description). The `-recurse` parameter enables processing of subfolders.

   ```powershell
   Add-WindowsDriver -Path "c:\mediarefresh\mounted" -Driver "c:\mediarefresh\drivers" -Recurse 
   ```

   > [!NOTE]
   > For testing purposes you can use `-ForceUnsigned` to add unsigned drivers and override the requirement that drivers must have a digital signature. For more information about driver signing requirements, see [Device Drivers and Deployment Overview](/windows-hardware/manufacture/desktop/device-drivers-and-deployment-overview).

1. **Add Custom Setup Scripts**
   1. Before adding custom setup scripts to the OS image, first create a `scripts` folder under `c:\mediarefresh\mounted\windows\setup\` using the PowerShell command [New-Item](/powershell/module/microsoft.powershell.management/new-item#description).

      ```powershell
      MD c:\mediarefresh\mounted\windows\setup\scripts
      ```

   1. Copy scripts from `c:\mediarefresh\scripts` to `c:\mediarefresh\mounted\windows\setup\scripts` using [Robocopy](https://social.technet.microsoft.com/wiki/contents/articles/52831.robocopy-complete-reference.aspx).

      ```powershell
      robocopy c:\mediarefresh\scripts c:\mediarefresh\mounted\windows\setup\scripts *.cmd
      ```

1. **Apply servicing packages to the OS image**  
   Apply the latest cumulative update and its dependencies that you downloaded to `c:\mediarefresh\packages` folder to WinPE at `c:\mediarefresh\mounted` using the PowerShell command [Add-WindowsPackage](/powershell/module/dism/add-windowspackage#description).

   1. First apply the servicing stack update dependency.

      ```powershell
      Add-WindowsPackage -Path "c:\mediarefresh\mounted" -PackagePath "c:\mediarefresh\packages\SSU"
      ```

   1. Now apply the latest cumulative update.

      ```powershell
      Add-WindowsPackage -Path "c:\mediarefresh\mounted" -PackagePath "c:\mediarefresh\packages\LCU"
      ```

   > [!TIP]
   > If you encounter error 0x800f0823, your servicing update may have a dependency that must be applied first. If you already downloaded its dependency, try running the above command a second time.  If this does not resolve the issue you may need to download an additional prerequisite for your update.
   >
   > - Make note of the KB####### in the filename of the update in c:\mediarefresh\packages.
   > - Search *[support.microsoft.com](https://support.microsoft.com)* with the KB#######
   > - Open the first topic that matches and search for the term "prerequisite".
   > - Download any prerequisites mentioned and run the above command again.  Note, you may need to run the command twice in order to allow the prerequisite to applied first.
   > - Continue to next step once error has been resolved.

1. **Save and dismount updated install.wim**  
   To complete the servicing process use the PowerShell command [Dismount-WindowsImage](/powershell/module/dism/dismount-windowsimage#description) to save the changes.  

   > [!IMPORTANT]
   > Before executing the `Dismount-WindowsImage` command, make sure you do not have any File Explorer views or command windows that are viewing contents under `c:\mediarefresh\mounted`.  Failure to do so will result in an error when attempting to dismount.

   ```powershell
   Dismount-WindowsImage -path "c:\mediarefresh\mounted" -save
   ```
  
1. **Delete temporary folder `mounted`**  
   Upon successful dismounting of the boot.wim, now we can remove the temporary folder `c:\mediarefresh\mounted` using the PowerShell command [Remove-Item](/powershell/module/microsoft.powershell.management/rename-item#description)

   ```powershell
   RD c:\mediarefresh\mounted
   ```

1. **Split WIM to support FAT32 file system**  
   To ensure the new install.wim fits onto flash media formatted as FAT32, which has a maximum file size of 4 GB you split the Windows Image (install.wim) file into a set of smaller (.swm) files with a maximum size of 4000 MB using the PowerShell command [Split-WindowsImage](/windows-hardware/manufacture/desktop/split-a-windows-image--wim--file-to-span-across-multiple-dvds). The resulting `*.swm` files are written to the `c:\mediarefresh\out\sources` folder.

   ```powershell
   Split-WindowsImage -ImagePath "c:\mediarefresh\wim\install.wim" -SplitImagePath "c:\mediarefresh\out\sources\install.swm" -FileSize 4000 -CheckIntegrity
   ```

The OS installation image, originally stored as `install.wim`, is now stored under `c:\mediarefresh\out\sources\` as `install.swm` and `install2.swm` which setup uses as if they were the original `install.wim`.

## Copy updated media to flash drive

If you haven't created a bootable flash drive, do so before continuing by following the steps to [Install Windows from a flash drive](/windows-hardware/manufacture/desktop/install-windows-from-a-usb-flash-drive).

The final step of creating your updated installation media is to copy the contents of `c:\mediarefresh\out` to your bootable flash drive using  [Robocopy](https://social.technet.microsoft.com/wiki/contents/articles/52831.robocopy-complete-reference.aspx).

```powershell
robocopy c:\mediarefresh\out <DriveLetter>:\ /e
```

Where `<DriveLetter>` is the drive letter associated with your flash drive

## Install Windows to the new device

1. Connect the flash drive to your target device.
1. Turn on the device and press the key that opens the boot-device selection menu for the computer, such as the Esc/F10/F12 keys. Select the option that boots the device from the flash drive.

   Windows Setup starts.  Follow the instructions to install Windows

   > [!TIP]
   > You may need to consult the device manufacturer instructions to configure it for booting from the flash drive it this process does not work on your device.

1. Once the initial phase of Setup is complete and your device reboots, Setup may start again from the beginning.  If Setup starts again, cancel Setup, and shut down the computer then remove the flash drive and turn on the device to continue with the next phase of Setup.

   > [!TIP]
   > If, for some reason, you encounter an error during the Setup process, please see the following articles for troubleshooting guidance.
   >
   > - [Deployment Troubleshooting and Log Files](/windows-hardware/manufacture/desktop/deployment-troubleshooting-and-log-files)
   > - [Windows Setup Log Files and Event Logs](/windows-hardware/manufacture/desktop/windows-setup-log-files-and-event-logs)

## Full Script

This section contains a full script that performs each of the media servicing steps in succession automatically. Before using this script, you must complete the [Prepare Media Servicing Environment](#prepare-media-servicing-environment) section of this article.  Once you're ready, copy the following PowerShell script to `c:\mediarefresh\mediarefresh.ps1.`  

```powershell
$LogFile = ".\MediaRefresh.log"
$LogDetail = ".\MediaRefreshDetail.log"

"================================================" >> $LogFile
(get-date).ToString("yyyy-MM-dd HH:mm:ss") + " | Starting MediaRefresh" >> $LogFile
"================================================" >> $LogFile
Write-Host "Updating Boot.wim" -ForegroundColor Blue
(get-date).ToString("yyyy-MM-dd HH:mm:ss") + " | Boot.wim Update Started" >> $LogFile
Write-Host "     Preparing to mount boot.wim" -ForegroundColor Blue

(get-date).ToString("yyyy-MM-dd HH:mm:ss") + " |     Checking for existing .\Mounted folder" >> $LogFile

if ( -not (Test-Path -Path 'c:\MediaRefresh\mounted' -PathType Container)) { 
   (get-date).ToString("yyyy-MM-dd HH:mm:ss") + " |     Create .\Mounted folder" >> $LogFile
   MD c:\MediaRefresh\mounted >> $LogDetail
   (get-date).ToString("yyyy-MM-dd HH:mm:ss") + " |     Created .\Mounted folder" >> $LogFile
   }
   else {
   (get-date).ToString("yyyy-MM-dd HH:mm:ss") + " |     .\Mounted folder already existed" >> $LogFile 
   }

Write-Host "     Setting boot.wim file attributes to read-write" -ForegroundColor Blue
(get-date).ToString("yyyy-MM-dd HH:mm:ss") + " |     Setting boot.wim file attributes to read-write" >> $LogFile
Set-ItemProperty -Path "c:\mediarefresh\wim\boot.wim" -Name IsReadOnly -Value $false | out-null
(get-date).ToString("yyyy-MM-dd HH:mm:ss") + " |     Set boot.wim file attributes to read-write" >> $LogFile

Write-Host "     Mounting boot.wim" -ForegroundColor Blue
(get-date).ToString("yyyy-MM-dd HH:mm:ss") + " |     Mount-WindowsImage boot.wim Started" >> $LogFile
Mount-WindowsImage -ImagePath "c:\mediarefresh\wim\boot.wim" -Index 2 -Path "c:\mediarefresh\Mounted" >> $LogDetail
(get-date).ToString("yyyy-MM-dd HH:mm:ss") + " |     Mount-WindowsImage boot.wim Completed" >> $LogFile

Write-Host "     Installing Drivers" -ForegroundColor Blue
(get-date).ToString("yyyy-MM-dd HH:mm:ss") + " |     Add-WindowsDrivers to boot.wim Started" >> $LogFile
Add-WindowsDriver -Path "c:\mediarefresh\mounted" -Driver "c:\mediarefresh\drivers" -Recurse >> $LogDetail
(get-date).ToString("yyyy-MM-dd HH:mm:ss") + " |     Add-WindowsDrivers to boot.wim Completed" >> $LogFile

Write-Host "     Installing Servicing Stack Update" -ForegroundColor Blue
(get-date).ToString("yyyy-MM-dd HH:mm:ss") + " |     Add-WindowsPackage SSU to boot.wim Started" >> $LogFile
Add-WindowsPackage -Path "c:\mediarefresh\mounted" -PackagePath "c:\mediarefresh\packages\SSU" >> $LogDetail
(get-date).ToString("yyyy-MM-dd HH:mm:ss") + " |     Add-WindowsPackage SSU to boot.wim Completed" >> $LogFile

Write-Host "     Installing Latest Cumulative Update" -ForegroundColor Blue
Write-Host "          Note: This process may take several minutes to complete." -ForegroundColor Cyan
(get-date).ToString("yyyy-MM-dd HH:mm:ss") + " |     Add-WindowsPackage LCU to boot.wim Started" >> $LogFile
Add-WindowsPackage -Path "c:\mediarefresh\mounted" -PackagePath "c:\mediarefresh\packages\LCU" >> $LogDetail
(get-date).ToString("yyyy-MM-dd HH:mm:ss") + " |     Add-WindowsPackage LCU to boot.wim Completed" >> $LogFile

Write-Host "     Setting read-write attribute on \out\sources\setup.exe" -ForegroundColor Blue
(get-date).ToString("yyyy-MM-dd HH:mm:ss") + " |     Setting \out\sources\setup.exe file attributes to read-write" >> $LogFile
Set-ItemProperty -Path "c:\mediarefresh\out\sources\setup.exe" -Name IsReadOnly -Value $false >> $LogDetail
(get-date).ToString("yyyy-MM-dd HH:mm:ss") + " |     Set \out\sources\setup.exe file attributes to read-write" >> $LogFile

Write-Host "     Copying updated setup.exe to \out\sources" -ForegroundColor Blue
(get-date).ToString("yyyy-MM-dd HH:mm:ss") + " |     Copy updated setup.exe to .\out\sources Started" >> $LogFile
robocopy c:\mediarefresh\mounted\sources c:\mediarefresh\out\sources setup.exe | out-null
(get-date).ToString("yyyy-MM-dd HH:mm:ss") + " |     Copy updated setup.exe to .\out\sources Completed" >> $LogFile

Write-Host "     Saving and dismounting boot.wim" -ForegroundColor Blue
Write-Host "          Note: This process may take several minutes to complete." -ForegroundColor Cyan
(get-date).ToString("yyyy-MM-dd HH:mm:ss") + " |     Dismount-WindowsImage boot.wim Started" >> $LogFile
Dismount-WindowsImage -path "c:\mediarefresh\mounted" -save -CheckIntegrity -LogLevel 3 >> $LogDetail
(get-date).ToString("yyyy-MM-dd HH:mm:ss") + " |     Dismount-WindowsImage boot.wim Completed" >> $LogFile

Write-Host "     Removing \Mounted folder" -ForegroundColor Blue
(get-date).ToString("yyyy-MM-dd HH:mm:ss") + " |     Removing .\mounted folder" >> $LogFile
RD c:\mediarefresh\mounted | out-null
(get-date).ToString("yyyy-MM-dd HH:mm:ss") + " |     .\mounted folder removed" >> $LogFile

Write-Host "     Copying updated boot.wim to \out\sources" -ForegroundColor Blue
(get-date).ToString("yyyy-MM-dd HH:mm:ss") + " |     Copy boot.wim to .\out\sources Started" >> $LogFile
robocopy c:\mediarefresh\wim c:\mediarefresh\out\sources boot.wim | out-null
(get-date).ToString("yyyy-MM-dd HH:mm:ss") + " |     Copy boot.wim to .\out\sources Completed" >> $LogFile
(get-date).ToString("yyyy-MM-dd HH:mm:ss") + " | Boot.wim Update Completed" >> $LogFile
Write-Host "Updating Boot.wim Complete" -ForegroundColor Blue

Write-Host "Updating Install.wim" -ForegroundColor Blue
(get-date).ToString("yyyy-MM-dd HH:mm:ss") + " | Install.wim Update Started" >> $LogFile
Write-Host "     Preparing to mount install.wim" -ForegroundColor Blue

(get-date).ToString("yyyy-MM-dd HH:mm:ss") + " |     Checking for existing .\Mounted folder" >> $LogFile

if ( -not (Test-Path -Path 'c:\MediaRefresh\mounted' -PathType Container)) { 
   (get-date).ToString("yyyy-MM-dd HH:mm:ss") + " |     Create .\Mounted folder" >> $LogFile
   MD c:\MediaRefresh\mounted  >> $LogDetail
   (get-date).ToString("yyyy-MM-dd HH:mm:ss") + " |     Created .\Mounted folder" >> $LogFile
   }
   else {
   (get-date).ToString("yyyy-MM-dd HH:mm:ss") + " |     .\Mounted folder already existed" >> $LogFile 
   }

Write-Host "     Setting read-write attribute on install.wim" -ForegroundColor Blue
(get-date).ToString("yyyy-MM-dd HH:mm:ss") + " |     Setting install.wim file attributes to read-write" >> $LogFile
Set-ItemProperty -Path "c:\mediarefresh\wim\install.wim" -Name IsReadOnly -Value $false | out-null
(get-date).ToString("yyyy-MM-dd HH:mm:ss") + " |     Set install.wim file attributes to read-write" >> $LogFile

Write-Host "     Mounting install.wim" -ForegroundColor Blue
Write-Host "          Note: This process may take several minutes to complete." -ForegroundColor Cyan
(get-date).ToString("yyyy-MM-dd HH:mm:ss") + " |     Mount-WindowsImage install.wim Started" >> $LogFile
Mount-WindowsImage -ImagePath "c:\mediarefresh\wim\install.wim" -Index 2 -Path "c:\mediarefresh\Mounted" >> $LogDetail
(get-date).ToString("yyyy-MM-dd HH:mm:ss") + " |     Mount-WindowsImage install.wim Completed" >> $LogFile


Write-Host "     Installing Drivers" -ForegroundColor Blue
(get-date).ToString("yyyy-MM-dd HH:mm:ss") + " |     Add-WindowsDrivers to install.wim Started" >> $LogFile
Add-WindowsDriver -Path "c:\mediarefresh\mounted" -Driver "c:\mediarefresh\drivers" -Recurse  >> $LogDetail
(get-date).ToString("yyyy-MM-dd HH:mm:ss") + " |     Add-WindowsDrivers to install.wim Completed" >> $LogFile

Write-Host "     Creating folder \Windows\Setup\Scripts" -ForegroundColor Blue
(get-date).ToString("yyyy-MM-dd HH:mm:ss") + " |     Checking for existing \windows\setup\scripts folder" >> $LogFile
if ( -not (Test-Path -Path 'c:\mediarefresh\mounted\windows\setup\scripts' -PathType Container)) {
   (get-date).ToString("yyyy-MM-dd HH:mm:ss") + " |     Create \windows\setup\scripts folder" >> $LogFile
   MD c:\mediarefresh\mounted\windows\setup\scripts >> $LogDetail
   (get-date).ToString("yyyy-MM-dd HH:mm:ss") + " |     Created \windows\setup\scripts folder" >> $LogFile
   }
   else {
   (get-date).ToString("yyyy-MM-dd HH:mm:ss") + " |     \windows\setup\scripts already existed" >> $LogFile 
   }

Write-Host "     Copying Scripts to \Windows\Setup\Scripts" -ForegroundColor Blue
(get-date).ToString("yyyy-MM-dd HH:mm:ss") + " |     Copy scripts to \windows\setup\scripts Started" >> $LogFile
robocopy c:\mediarefresh\scripts c:\mediarefresh\mounted\windows\setup\scripts *.cmd | out-null
(get-date).ToString("yyyy-MM-dd HH:mm:ss") + " |     Copy scripts to \windows\setup\scripts Completed" >> $LogFile

Write-Host "     Installing Servicing Stack Update" -ForegroundColor Blue
(get-date).ToString("yyyy-MM-dd HH:mm:ss") + " |     Add-WindowsPackage SSU to install.wim Started" >> $LogFile
Add-WindowsPackage -Path "c:\mediarefresh\mounted" -PackagePath "c:\mediarefresh\packages\SSU"  >> $LogDetail
(get-date).ToString("yyyy-MM-dd HH:mm:ss") + " |     Add-WindowsPackage SSU to install.wim Completed" >> $LogFile 

Write-Host "     Installing Latest Cumulative Update" -ForegroundColor Blue
Write-Host "          Note: This process may take several minutes to complete." -ForegroundColor Cyan
(get-date).ToString("yyyy-MM-dd HH:mm:ss") + " |     Add-WindowsPackage LCU to install.wim Started" >> $LogFile 
Add-WindowsPackage -Path "c:\mediarefresh\mounted" -PackagePath "c:\mediarefresh\packages\LCU" >> $LogDetail
(get-date).ToString("yyyy-MM-dd HH:mm:ss") + " |     Add-WindowsPackage LCU to install.wim Completed" >> $LogFile 

Write-Host "     Saving and dismounting install.wim" -ForegroundColor Blue
Write-Host "          Note: This process may take several minutes to complete." -ForegroundColor Cyan
(get-date).ToString("yyyy-MM-dd HH:mm:ss") + " |     Dismount-WindowsImage install.wim Started" >> $LogFile
Dismount-WindowsImage -path "c:\mediarefresh\mounted" -save -CheckIntegrity -LogLevel 3 >> $LogDetail
(get-date).ToString("yyyy-MM-dd HH:mm:ss") + " |     Dismount-WindowsImage install.wim Completed" >> $LogFile

Write-Host "     Removing \Mounted folder" -ForegroundColor Blue
(get-date).ToString("yyyy-MM-dd HH:mm:ss") + " |     Removing .\mounted folder" >> $LogFile
RD c:\mediarefresh\mounted | out-null
(get-date).ToString("yyyy-MM-dd HH:mm:ss") + " |     .\mounted folder removed" >> $LogFile

Write-Host "Updating Install.wim Complete" -ForegroundColor Blue
(get-date).ToString("yyyy-MM-dd HH:mm:ss") + " | Install.wim Update Completed" >> $LogFile

Write-Host "Splitting Install.wim" -ForegroundColor Blue
Write-Host "     Note: This process may take several minutes to complete." -ForegroundColor Cyan
(get-date).ToString("yyyy-MM-dd HH:mm:ss") + " | Split-WindowsImage Started" >> $LogFile
Split-WindowsImage -ImagePath "c:\mediarefresh\wim\install.wim" -SplitImagePath "c:\mediarefresh\out\sources\install.swm" -FileSize 4000 -CheckIntegrity >> $LogDetail
(get-date).ToString("yyyy-MM-dd HH:mm:ss") + " | Split-WindowsImage Completed" >> $LogFile

Write-Host "Update Complete" -ForegroundColor Blue
Write-Host "Copy contents of c:\mediarefresh\out to your flash drive" -ForegroundColor Blue
```

## Other Resources

- [Update Windows installation media with Dynamic Update](/windows/deployment/update/media-dynamic-update)
- [Windows boot and installation overview](/windows-hardware/manufacture/desktop/boot-and-install-windows)
- [Add languages to Windows setup](/windows-hardware/manufacture/desktop/add-multilingual-support-to-windows-setup)
