---
title: Install WinGet (Windows Package Manager) on Windows IoT OS
description: How to Install WinGet on Windows IoT Enterprise
author: trumanbrown-msft 
ms.author: trumanbrown
ms.topic: how-to 
ms.date: 05/18/2023
ms.prod: windows-iot
ms.custom: template-how-to 
---

# Install `WinGet` (Windows Package Manager) on Windows IoT Enterprise

In this tutorial, you learn how to install the Windows Package Manager (WinGet) on Windows IoT Enterprise. Modified from [original WinGet documentation for non-IoT Windows](https://github.com/microsoft/winget-cli) as there's no Windows Store to download from on Windows IoT. This copies many instructions from Zamiell's original discussion [here](https://github.com/microsoft/winget-cli/discussions/1956) and from MuradBuyukasik's repo [here](https://github.com/muradbuyukasik/winget-script). This documentation is all tested on Windows 10 IoT Enterprise LTSC 2021.

## Download the Latest WinGet Release Files and Other Build files

1. Navigate to the [WinGet CLI Repo Releases](https://github.com/microsoft/winget-cli/releases) to download the WinGet bundle files
   1. Choose the latest version that isn't "Prerelease" (It should have the **Latest** tag.)
   2. In My case, this version is version 1.4.10173  
   :::image type="content" source="media/winget-version.png" alt-text="Release screenshot":::
2. Download the `msixbundle` file and the `License1.xml` file.
3. Navigate to the [following page](https://learn.microsoft.com/troubleshoot/developer/visualstudio/cpp/libraries/c-runtime-packages-desktop-bridge#how-to-install-and-update-desktop-framework-packages) for the VC++ v14 Desktop Framework Package and select your correct package for your OS
   1. If running on Arm64 architecture, download `Microsoft.VCLibs.arm64.14.00.Desktop.appx`
   2. If running on x64 architecture, download `Microsoft.VCLibs.x64.14.00.Desktop.appx` and etc.  
   :::image type="content" source="media/vclibs.png" alt-text="Packages screenshot":::
4. Winget v1.2.10271 and later introduced a new dependency for Microsoft.UI.Xaml.2.7, which you have to install manually.
   1. Download the [NuGet package](https://www.nuget.org/packages/Microsoft.UI.Xaml/2.7.0) from the link. Go to the right side, select **Download Package**.
      > [!NOTE]
      > This link (<https://www.nuget.org/packages/Microsoft.UI.Xaml/2.7.0>>) is specific to version 2.7.0. Do not use a newer version unless a future release supports it.  

   2. Change the file extension from `.nuget` or whatever else the file extension is (.nupkg) to `.zip` and open it with any archiving program.
   3. Within the archive, navigate to `tools\AppX\[YOUR ARCHITECTURE]\Release` and extract `Microsoft.UI.XAML.2.7.appx` to a location you use later.
   4. **MAKE SURE YOU ARE USING VERSION 2.7. XAML 2.8 IS NOT SUPPORTED YET**. The installation will fail with 2.8 as of May 18, 2023.

## Install the WinGet Client

1. Open an **Administrator** PowerShell session
1. Run the following command to install the Desktop Framework Package

   ```powershell
   Add-AppxPackage -Path <path to VCLibs .appx file>
   ```

      1. Without this dependency installed, the winget installer fails (without any error/warning messages). Specifically, the "winget.exe" file isn't added to "C:\Users\\[Username]\AppData\Local\Microsoft\WindowsApps".
1. Install Microsoft UI Xaml with:

    ```powershell
   Add-AppxPackage -Path <path to UI xaml.appx file>
    ```

   1. Without this dependency installed, the winget installer fails (without any error/warning messages). Specifically, the "winget.exe" file isn't added to "C:\Users[Username]\AppData\Local\Microsoft\WindowsApps".
1. Run the following commands to install the WinGet client from the msixbundle file and apply the license

    ```powershell
   Add-AppxPackage -Path <path to .msixbundle file>
   ```

   ```powershell
   Add-AppxProvisionedPackage -Online -PackagePath <path to .msixbundle file> -LicensePath <path to xml file>
   ```

   :::image type="content" source="media/add-app-package.png" alt-text="All the commands ran":::
1. Now, you should see the "winget.exe" file appear at "C:\Users[Username]\AppData\Local\Microsoft\WindowsApps". Furthermore, it should also be automatically added to your path. You should also be able to use `winget` in the PowerShell terminal
   1. If you're having issues, try restarting the shell and the PC.  
   :::image type="content" source="media/winget-result.png" alt-text="Winget in powershell":::

## More Resources

- [Install WinGet on non-IoT Windows Versions](https://learn.microsoft.com/windows/package-manager/winget/)
- [Using WinGet](https://learn.microsoft.com/windows/package-manager/winget/)
