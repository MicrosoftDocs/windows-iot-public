---
title: Setting up an NXP i.MX EVK device
description: Setting up an NXP i.MX8 EVK device 
author: terrywarwick
ms.author: twarwick
ms.prod: windows-iot
ms.topic: tutorial 
ms.technology: iot
ms.date: 05/25/2023
---

# Tutorial: Setup an NXP i.MX EVK

In this tutorial, you learn how to:

- Add the board support package drivers from NXP for the i.MX EVKs to the *Windows 10 IoT Enterprise LTSC 2021* installation media.
- Update the *Windows 10 IoT Enterprise LTSC 2021* installation media with the latest cumulative servicing update.
- Install *Windows 10 IoT Enterprise LTSC 2021* to your i.MX EVK board.

## Prerequisites

- Windows 10 IoT Enterprise LTSC 2021 for Arm64 DVD or ISO
- microSD card (minimum 8 GB)
- One of the following NXP evaluation boards
  - i.MX 8M Quad EVK
  - i.MX 8M Mini EVK
  - i.MX 8M Nano EVK
  - i.MX 8M Plus EVK
  - i.MX 8QuadXPlus EVK
  - i.MX 93 EVK

## Prepare Media Servicing Environment

In this section, you gather all of the components required to add the board support package for the i.MX EVK boards and apply the latest cumulative update to the Windows 10 IoT Enterprise LTSC installation media.  Once complete, you can use our standard process for updating the installation media to install Windows 10 IoT Enterprise LTSC 2021 on your NXP i.MX EVK.

1. **Start PowerShell with Administrator privileges.**</br>
   We use this instance of PowerShell for the end to end process of servicing the installation media to apply updates and, if needed, incorporate required drivers that aren't part of the Windows installation media  
    - Select **Start**
    - Type PowerShell
    - Right-click **Windows PowerShell**
    - Select **Run as administrator**

1. **Create folders to store files during media servicing**</br>
   Use the PowerShell command [New_Item](/powershell/module/microsoft.powershell.management/new-item?#example-2-create-a-directory) to create the following folders on your technician PC to store files needed during media servicing.

   **c:\MediaRefresh**: Parent folder for storing files during media servicing.  
   **c:\MediaRefresh\Out**: Copy of the original media updated during servicing.  
   **c:\MediaRefresh\Packages**: Windows servicing updates.  
   **c:\MediaRefresh\Drivers**: NXP i.MX8 EVK drivers.  
   **c:\MediaRefresh\Scripts**: Custom install scripts.

   ```powershell
   md c:\MediaRefresh\Drivers
   md c:\MediaRefresh\Out
   md c:\MediaRefresh\Packages
   md c:\MediaRefresh\Scripts
   ```

1. **Copy files from original media**</br>
   Copy all files from the original installation media to `c:\MediaRefresh\Out`.

   1. Proceed to step `b.` if you have physical media,  otherwise you must first mount the Windows IoT Enterprise installation ISO using [Mount-DiskImage](/powershell/module/storage/mount-diskimage) and display the resulting mounted drive letter using [Get-Volume](/powershell/module/storage/get-volume).

      ```powershell
      Mount-DiskImage -ImagePath <ISO Path> | Get-Volume
      ```

      Where `<ISO Path>` is a fully qualified path to your ISO

      Make note of the DriveLetter as we'll need to use it in the next step.

   1. Copy files from the original installation media denoted here by `<DriveLetter>` to  `c:\MediaRefresh\ISO\Out` folder using [Robocopy](https://social.technet.microsoft.com/wiki/contents/articles/52831.robocopy-complete-reference.aspx).

      ```powershell
      robocopy <DriveLetter>:\ c:\MediaRefresh\Out /e
      ```

      Where `<DriveLetter>` represents the drive letter associated with the mounted ISO file  

   1. Proceed to next step if you didn't mount an ISO for the previous command, otherwise you must first dismount the Windows IoT Enterprise installation ISO using [Dismount-Diskimage](/powershell/module/storage/dismount-diskimage)

      ```powershell
      Dismount-DiskImage -ImagePath <ISO Path>  
      ```

      Where `<ISO Path>` is a fully qualified path to your ISO file.

1. **Gather servicing packages**
   1. Locate the most recent cumulative update for Windows 10 IoT Enterprise LTSC 2021 (also known as Windows 10 version 21H2) in the [Windows Update Catalog](https://www.catalog.update.microsoft.com/Search.aspx?q=-Dynamic%20Cumulative%20Update%20for%20Windows%2010%20Version%2021H2%20for%20Arm64). The most recent cumulative update should be the first one in the list.  You can verify using the value in the Last Updated column.
   1. Select `Download` and save the `.msu` file to `c:\mediarefresh\packages` folder.
   1. While you're still viewing the Windows Update Catalog, select on the title of the cumulative update that you downloaded, then select on the `Support Url` on the Overview tab.  This link opens a webpage with more details about the update.
   1. Scroll down to the *How to get this update* section to see if there are any prerequisites required.  Assume that you don't have any updates installed.  If there are prerequisites listed, download the extra `.msu` file(s) to the `c:\MediaRefresh\Packages` folder.

1. **Gather NXP i.MX drivers**

   1. Download the **BSP Prebuilt Binaries** from [NXP IMXWIN10IOT Releases](https://www.nxp.com/design/software/embedded-software/i-mx-software/windows-10-iot-enterprise-for-i-mx-applications-processors:IMXWIN10IOT#RCA) to your local Downloads folder.
   1. Using the PowerShell session from earlier, use the PowerShell command [Expand-Archive](/powershell/module/microsoft.powershell.archive/expand-archive) to extract the contents of the downloaded ZIP file.

      ```powershell
      Expand-Archive -LiteralPath <Path to ZIP file> -Destination c:\mediarefresh\NXP
      ```

      Where `<Path to ZIP file>` represents the fully qualified path to the BSP Prebuilt Binaries ZIP file downloaded in the previous step.

   1. Copy the drivers folder from `c:\mediarefresh\nxp\IoTEntOnNXP\drivers` to `c:\mediarefresh\drivers using [Robocopy](https://social.technet.microsoft.com/wiki/contents/articles/52831.robocopy-complete-reference.aspx).

      ```powershell
      robocopy c:\mediarefresh\nxp\IoTEntOnNXP\drivers c:\mediarefresh\drivers /e
      ```

1. **Create a `SetupComplete.cmd` script to install VPU**</br>
   Save the contents of the following script as `SetupComplete.cmd` in the `c:\MediaRefresh\Scripts` folder.

   For more information about using SetupComplete.cmd, see [Add a Custom Script to Windows Setup](/windows-hardware/manufacture/desktop/add-a-custom-script-to-windows-setup)

   ```cmd
   @echo off
   echo Detect VPU Variant
   set VPU_HANTRO_FF_STR="NXP0109\1" 
   set VPU_HANTRO_LF_STR="NXP0109\2" 
   set VPU_MALONE_STR="NXP0224\0" 
   set VPU_HANTRO_FF_ID=1 
   set VPU_HANTRO_LF_ID=2 
   set VPU_MALONE_ID=3 
   set VPU_NONE=0 
   set VPU_HANTRO=false 
   set VPU_MALONE=false 
   set vpu_variant=%VPU_NONE% 
   pnputil /enum-devices | find %VPU_HANTRO_FF_STR% > nul 
   if %errorlevel% == 0 ( set vpu_variant=%VPU_HANTRO_FF_ID% & goto vpu_found ) 
   pnputil /enum-devices | find %VPU_HANTRO_LF_STR% > nul 
   if %errorlevel% == 0 ( set vpu_variant=%VPU_HANTRO_LF_ID% & goto vpu_found ) 
   pnputil /enum-devices | find %VPU_MALONE_STR% > nul 
   if %errorlevel% == 0 ( set vpu_variant=%VPU_MALONE_ID% & goto vpu_found ) 
   
   :vpu_found 
   if %vpu_variant% == %VPU_HANTRO_FF_ID% set VPU_HANTRO=true 
   if %vpu_variant% == %VPU_HANTRO_LF_ID% set VPU_HANTRO=true 
   if %vpu_variant% == %VPU_MALONE_ID% set VPU_MALONE=true 
   if %VPU_MALONE% == true (
     echo Installing VPU MALONE 
     REG ADD "HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DeviceAccess\Classes\{40d466e9-e5fd-45a1-8707-e5059211c021}" /V Policy /T REG_DWORD /D 1 /F 
     REG ADD "HKLM\SOFTWARE\Classes\MediaFoundation\Transforms\Preferred" /V {34363248-0000-0010-8000-00AA00389B71} /T REG_SZ /D {16977919-9727-4e04-ABD6-7D04C3828977} /F 
     REG ADD "HKLM\SOFTWARE\Classes\MediaFoundation\Transforms\Preferred" /V {35363248-0000-0010-8000-00AA00389B71} /T REG_SZ /D {16977919-9727-4e04-ABD6-7D04C3828977} /F 
     REG ADD "HKLM\SOFTWARE\Classes\MediaFoundation\Transforms\Preferred" /V {43564548-0000-0010-8000-00AA00389B71} /T REG_SZ /D {16977919-9727-4e04-ABD6-7D04C3828977} /F 
     REG ADD "HKLM\SOFTWARE\Classes\MediaFoundation\Transforms\Preferred" /V {30385056-0000-0010-8000-00AA00389B71} /T REG_SZ /D {16977919-9727-4e04-ABD6-7D04C3828977} /F 
     REG ADD "HKLM\SOFTWARE\Classes\MediaFoundation\Transforms\Preferred" /V {5334504D-0000-0010-8000-00AA00389B71} /T REG_SZ /D {16977919-9727-4e04-ABD6-7D04C3828977} /F 
     REG ADD "HKLM\SOFTWARE\Classes\MediaFoundation\Transforms\Preferred" /V {3253344D-0000-0010-8000-00AA00389B71} /T REG_SZ /D {16977919-9727-4e04-ABD6-7D04C3828977} /F 
     REG ADD "HKLM\SOFTWARE\Classes\MediaFoundation\Transforms\Preferred" /V {5634504D-0000-0010-8000-00AA00389B71} /T REG_SZ /D {16977919-9727-4e04-ABD6-7D04C3828977} /F 
     REG ADD "HKLM\SOFTWARE\Classes\MediaFoundation\Transforms\Preferred" /V {E06D8026-DB46-11CF-B4D1-00805F6CBBEA} /T REG_SZ /D {16977919-9727-4e04-ABD6-7D04C3828977} /F 
     REG ADD "HKLM\SOFTWARE\Classes\MediaFoundation\Transforms\62ce7e72-4c71-4d20-b15d-452831a87d9d" /V MFTFLAGS /T REG_DWORD /D 00000008 /F 
     REG ADD "HKLM\SOFTWARE\Classes\CLSID\{16977919-9727-4e04-ABD6-7D04C3828977}" /D "i.MX8QM/QXP Malone VPU MFT hardware accelerator" /F 
     REG ADD "HKLM\SOFTWARE\Classes\CLSID\{16977919-9727-4e04-ABD6-7D04C3828977}\InprocServer32" /T REG_EXPAND_SZ /D "%SystemRoot%\System32\malonemft.dll" /F 
     REG ADD "HKLM\SOFTWARE\Classes\CLSID\{16977919-9727-4e04-ABD6-7D04C3828977}\InprocServer32" /V ThreadingModel /D "Both" /F 
     REG ADD "HKLM\SOFTWARE\Classes\MediaFoundation\Transforms\16977919-9727-4e04-ABD6-7D04C3828977" /D "i.MX8QM/QXP Malone VPU MFT hardware accelerator" /F 
     REG ADD "HKLM\SOFTWARE\Classes\MediaFoundation\Transforms\16977919-9727-4e04-ABD6-7D04C3828977" /V InputTypes /T REG_BINARY /D 7669647300001000800000AA00389B714832363400001000800000AA00389B717669647300001000800000AA00389B714832363500001000800000AA00389B717669647300001000800000AA00389B714845564300001000800000AA00389B717669647300001000800000AA00389B715650383000001000800000AA00389B717669647300001000800000AA00389B7126806DE046DBCF11B4D100805F6CBBEA7669647300001000800000AA00389B714D50345300001000800000AA00389B717669647300001000800000AA00389B714D34533200001000800000AA00389B717669647300001000800000AA00389B714D50345600001000800000AA00389B71 /F 
     REG ADD "HKLM\SOFTWARE\Classes\MediaFoundation\Transforms\16977919-9727-4e04-ABD6-7D04C3828977" /V OutputTypes /T REG_BINARY /D 7669647300001000800000AA00389B711500000000001000800000AA00389B71 /F    
     REG ADD "HKLM\SOFTWARE\Classes\MediaFoundation\Transforms\16977919-9727-4e04-ABD6-7D04C3828977" /V MFTFlags /T REG_DWORD /D 0x00000002 /F 
     REG ADD "HKLM\SOFTWARE\Classes\MediaFoundation\Transforms\16977919-9727-4e04-ABD6-7D04C3828977" /V MFTFlags /T REG_DWORD /D 0x00000002 /F 
     REG ADD "HKLM\SOFTWARE\Classes\MediaFoundation\Transforms\Categories\d6c02d4b-6833-45b4-971a-05a4b04bab91\16977919-9727-4e04-ABD6-7D04C3828977" /F 
   ) 
   if %VPU_HANTRO% == true ( 
     echo Installing VPU HANTRO
     REG ADD "HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DeviceAccess\Classes\{ADA9253B-628C-40CE-B2C1-19F489A0F3DA}" /V Policy /T REG_DWORD /D 1 /F 
     REG ADD "HKLM\SOFTWARE\Classes\MediaFoundation\Transforms\Preferred" /V {34363248-0000-0010-8000-00AA00389B71} /T REG_SZ /D {8A12D5A9-69EC-4FE2-BF16-7B4C857D0DC0} /F 
     REG ADD "HKLM\SOFTWARE\Classes\MediaFoundation\Transforms\Preferred" /V {35363248-0000-0010-8000-00AA00389B71} /T REG_SZ /D {8A12D5A9-69EC-4FE2-BF16-7B4C857D0DC0} /F 
     REG ADD "HKLM\SOFTWARE\Classes\MediaFoundation\Transforms\Preferred" /V {43564548-0000-0010-8000-00AA00389B71} /T REG_SZ /D {8A12D5A9-69EC-4FE2-BF16-7B4C857D0DC0} /F 
     REG ADD "HKLM\SOFTWARE\Classes\MediaFoundation\Transforms\Preferred" /V {30385056-0000-0010-8000-00AA00389B71} /T REG_SZ /D {8A12D5A9-69EC-4FE2-BF16-7B4C857D0DC0} /F 
     REG ADD "HKLM\SOFTWARE\Classes\MediaFoundation\Transforms\Preferred" /V {30395056-0000-0010-8000-00AA00389B71} /T REG_SZ /D {8A12D5A9-69EC-4FE2-BF16-7B4C857D0DC0} /F 
     REG ADD "HKLM\SOFTWARE\Classes\MediaFoundation\Transforms\62ce7e72-4c71-4d20-b15d-452831a87d9d" /V MFTFLAGS /T REG_DWORD /D 00000008 /F 
     REG ADD "HKLM\SOFTWARE\Classes\CLSID\{8A12D5A9-69EC-4FE2-BF16-7B4C857D0DC0}" /D "i.MX VPU MFT hardware accelerator" /F 
     REG ADD "HKLM\SOFTWARE\Classes\CLSID\{8A12D5A9-69EC-4FE2-BF16-7B4C857D0DC0}\InprocServer32" /T REG_EXPAND_SZ /D "%SystemRoot%\System32\imxvpumft.dll" /F 
     REG ADD "HKLM\SOFTWARE\Classes\CLSID\{8A12D5A9-69EC-4FE2-BF16-7B4C857D0DC0}\InprocServer32" /V ThreadingModel /D "Both" /F 
     REG ADD "HKLM\SOFTWARE\Classes\MediaFoundation\Transforms\8a12d5a9-69ec-4fe2-bf16-7b4c857d0dc0" /D "i.MX VPU MFT hardware accelerator" /F 
     REG ADD "HKLM\SOFTWARE\Classes\MediaFoundation\Transforms\8a12d5a9-69ec-4fe2-bf16-7b4c857d0dc0" /V OutputTypes /T REG_BINARY /D 7669647300001000800000AA00389B714E56313200001000800000AA00389B71 /F 
     REG ADD "HKLM\SOFTWARE\Classes\MediaFoundation\Transforms\8a12d5a9-69ec-4fe2-bf16-7b4c857d0dc0" /V MFTFlags /T REG_DWORD /D 0x00000002 /F 
     REG ADD "HKLM\SOFTWARE\Classes\MediaFoundation\Transforms\Categories\d6c02d4b-6833-45b4-971a-05a4b04bab91\8a12d5a9-69ec-4fe2-bf16-7b4c857d0dc0" /F 
   ) 
   if %vpu_variant% == %VPU_HANTRO_FF_ID% ( 
     echo Installing VPU HANTRO FF
     REG ADD "HKLM\SOFTWARE\Classes\MediaFoundation\Transforms\Preferred" /V {5334504D-0000-0010-8000-00AA00389B71} /T REG_SZ /D {8A12D5A9-69EC-4FE2-BF16-7B4C857D0DC0} /F 
     REG ADD "HKLM\SOFTWARE\Classes\MediaFoundation\Transforms\Preferred" /V {3253344D-0000-0010-8000-00AA00389B71} /T REG_SZ /D {8A12D5A9-69EC-4FE2-BF16-7B4C857D0DC0} /F 
     REG ADD "HKLM\SOFTWARE\Classes\MediaFoundation\Transforms\Preferred" /V {5634504D-0000-0010-8000-00AA00389B71} /T REG_SZ /D {8A12D5A9-69EC-4FE2-BF16-7B4C857D0DC0} /F 
     REG ADD "HKLM\SOFTWARE\Classes\MediaFoundation\Transforms\Preferred" /V {E06D8026-DB46-11CF-B4D1-00805F6CBBEA} /T REG_SZ /D {8A12D5A9-69EC-4FE2-BF16-7B4C857D0DC0} /F 
     REG ADD "HKLM\SOFTWARE\Classes\MediaFoundation\Transforms\8a12d5a9-69ec-4fe2-bf16-7b4c857d0dc0" /V InputTypes /T REG_BINARY /D 7669647300001000800000AA00389B714832363400001000800000AA00389B717669647300001000800000AA00389B714832363500001000800000AA00389B717669647300001000800000AA00389B714845564300001000800000AA00389B717669647300001000800000AA00389B715650383000001000800000AA00389B717669647300001000800000AA00389B715650393000001000800000AA00389B717669647300001000800000AA00389B7126806DE046DBCF11B4D100805F6CBBEA7669647300001000800000AA00389B714D50345300001000800000AA00389B717669647300001000800000AA00389B714D34533200001000800000AA00389B717669647300001000800000AA00389B714D50345600001000800000AA00389B71 /F 
   ) 
   if %vpu_variant% == %VPU_HANTRO_LF_ID% ( 
     echo Installing VPU HANTRO LF
     REG ADD "HKLM\SOFTWARE\Classes\MediaFoundation\Transforms\8a12d5a9-69ec-4fe2-bf16-7b4c857d0dc0" /V InputTypes /T REG_BINARY /D 7669647300001000800000AA00389B714832363400001000800000AA00389B717669647300001000800000AA00389B714832363500001000800000AA00389B717669647300001000800000AA00389B714845564300001000800000AA00389B717669647300001000800000AA00389B715650383000001000800000AA00389B717669647300001000800000AA00389B715650393000001000800000AA00389B71 /F 
   ) 

   echo Installation Complete

   ```

## Review

The media servicing environment is now set up.  Lets do a quick review.

- Windows 10 IoT Enterprise LTSC 2021 installation has been copied to `c:\mediarefresh\out`.
- The Latest Cumulative Update for Windows 10 IoT Enterprise LTSC 2021 has been downloaded to `c:\mediarefresh\packages`.
- The NXP i.MX EVK BSP Drivers have been downloaded and copied to `c:\mediarefresh\drivers`
- A custom SetupComplete.cmd to configure the VPU for your NXP device has been saved to `c:\mediarefresh\scripts`.

## Next Steps

1. Use the media servicing environment created for the i.MX EVK boards to complete the refresh of the Windows 10 IoT Enterprise LTSC 2021 installation media.

   > [!WARNING]
   > The current BSP Prebuilt Binaries for the NXP i.MX EVK are Test Signed. When using `Add-WindowsDriver` in the next steps you must use the `-ForceUnsigned` attribute.

   1. [Update Windows Preinstallation Environment (WinPE)](/windows/iot/iot-enterprise/deployment/media-refresh#update-windows-preinstallation-environment-winpe)
   1. [Update Windows 10 IoT Enterprise LTSC 2021 Image](/windows/iot/iot-enterprise/deployment/media-refresh#update-windows-iot-enterprise)
   1. [Copy updated media to microSD card](/windows/iot/iot-enterprise/deployment/media-refresh#copy-updated-media-to-flash-drive)

1. Make sure the NXP i.MX EVK board is in eMMC boot mode. Refer to the Quick Start Guide from NXP to learn how to configure your board.
1. Insert the microSD card into the slot on the NXP i.MX EVK board.
1. Connect the power to the i.MX EVK and power it on to boot into the Windows setup experience.
1. Window setup walks you through the rest of the process.

## Other Information

- [Refresh IoT Enterprise Installation Media](/windows/iot/iot-enterprise/deployment/media-refresh)
