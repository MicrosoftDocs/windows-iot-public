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

# Using WinGet to Install Windows Store Apps on Windows IoT Enterprise LTSC

 The winget command line tool enables users to discover, install, upgrade, remove and configure applications on Windows 10 and Windows 11 devices. This tool is the client interface to the Windows Package Manager service. In this tutorial, you learn how to install and utilize WinGet on Windows IoT Enterprise. This guide is useful for Windows IoT Enterprise LTSC versions as they don't support the Microsoft Store application itself, which is commonly used to install WinGet. The documentation is all tested on Windows 10 IoT Enterprise LTSC 2021.

## Install WinGet on Windows 10 IoT Enterprise LTSC
### Download the Latest WinGet Release Files and Other Build files

1. Download WinGet bundle files from [WinGet CLI Repo Releases](https://github.com/microsoft/winget-cli/releases).
   1. Choose the latest version that isn't "Prerelease" (It should have the **Latest** tag.)
   1. In my case, this version is version 1.4.10173  
   :::image type="content" source="media/winget-version.png" alt-text="Release screenshot":::
1. Download the `msixbundle` file and the `License1.xml` file.
1. Navigate to the [following page](/troubleshoot/developer/visualstudio/cpp/libraries/c-runtime-packages-desktop-bridge#how-to-install-and-update-desktop-framework-packages) for the VC++ v14 Desktop Framework Package and select the correct package for your OS
   1. For Arm64 architecture, download `Microsoft.VCLibs.arm64.14.00.Desktop.appx`
   2. For x64 architecture, download `Microsoft.VCLibs.x64.14.00.Desktop.appx`  
   :::image type="content" source="media/vclibs.png" alt-text="Packages screenshot":::
2. Winget has a dependency on Microsoft.UI.Xaml.2.7, which you have to install manually.
   1. Download the NuGet package from [Microsoft UI NuGet Org](https://www.nuget.org/packages/Microsoft.UI.Xaml/2.7.0). The download link is located on the right side at **Download Package**.
      > [!NOTE]
      > This link (<https://www.nuget.org/packages/Microsoft.UI.Xaml/2.7.0>>) is specific to version 2.7.0. 
      > Do not use a newer version unless a future release supports it. 
      > The installation will fail with 2.8 as of May 18, 2023.

   2. Change the file extension from `.nupkg` to `.zip`. To change the file extension, Open Command Prompt, navigate to the directory where the nupkg file was downloaded and run the following command to rename the file:

   ```cmd
   ren Microsoft.UI.Xaml.2.7.0.nupkg Microsoft.UI.Xaml.2.7.0.zip
   ```

   3. Open the `.zip` archive you renamed, navigate to `tools\AppX\[YOUR ARCHITECTURE]\Release` and extract `Microsoft.UI.XAML.2.7.appx` to a location you use later.

### Install the WinGet Client

1. Open an **Administrator** PowerShell session
1. Run the following command to install the Desktop Framework Package

   ```powershell
   Add-AppxPackage -Path <path to VCLibs .appx file>
   ```

      1. Where `<path to VCLibs .appx file>` is the fully qualified path to the VC++ v14 Desktop Framework Package you downloaded earlier.
   > [!CAUTION]
   > Without this dependency installed, the winget installer fails (without any error/warning messages). Specifically, the "winget.exe" file isn't added to "C:\Users\\[Username]\AppData\Local\Microsoft\WindowsApps"

1. Install Microsoft UI Xaml with:

    ```powershell
   Add-AppxPackage -Path <path to UI xaml.appx file>
    ```

   1. Where `<path to UI xaml.appx file>` is the fully qualified path to the Microsoft UI Xaml 2.7.0 package you downloaded earlier.
   > [!CAUTION]
   > Without this dependency installed, the winget installer fails (without any error/warning messages). Specifically, the "winget.exe" file isn't added to "C:\Users\\[Username]\AppData\Local\Microsoft\WindowsApps"

1. Install the WinGet client with:

    ```powershell
   Add-AppxPackage -Path <path to .msixbundle file>
   ```

   1. Where `<path to .msixbundle file>` is the fully qualified path to the WinGet bundle file you downloaded earlier.
1. Configure the WinGet client with the correct license file with:

   ```powershell
   Add-AppxProvisionedPackage -Online -PackagePath <path to .msixbundle file> -LicensePath <path to xml file>
   ```

   1. Where `<path to .msixbundle file>` is the fully qualified path to the WinGet bundle file and `<path to xml file>` is the fully qualified path to the License1.xml file you downloaded earlier.

   :::image type="content" source="media/add-app-package.png" alt-text="All the commands ran":::
1. Now, you should see the "winget.exe" file appear at "C:\Users[Username]\AppData\Local\Microsoft\WindowsApps". Furthermore, it should also be automatically added to your path. You should also be able to use `winget` in the PowerShell terminal
   1. If you're having issues, try restarting the shell and the PC.  
   :::image type="content" source="media/winget-result.png" alt-text="Winget in powershell":::

### Install and Configure Applications with WinGet

1. Follow the [**Use winget**](/windows/package-manager/winget/#use-winget) documentation on instructions on how to search, install, configure, and uninstall applications with WinGet.

## Note

Some of these instructions are modified from [original WinGet documentation for non-IoT Windows](https://github.com/microsoft/winget-cli) as there's no Windows Store to download from on Windows IoT LTSC versions. This copies many instructions from Zamiell's original discussion [here](https://github.com/microsoft/winget-cli/discussions/1956) and from MuradBuyukasik's repo [here](https://github.com/muradbuyukasik/winget-script).
## More Resources

- [Install WinGet on non-IoT LTSC Windows Versions](/windows/package-manager/winget/)
- [Using WinGet and Command Information](/windows/package-manager/winget/)
