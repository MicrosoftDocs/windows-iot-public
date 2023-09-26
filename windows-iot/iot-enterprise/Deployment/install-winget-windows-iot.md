---
title: Using WinGet to Install Apps on Windows IoT Enterprise
description: How to Install WinGet on Windows IoT Enterprise
author: trumanbrown-msft 
ms.author: trumanbrown
ms.topic: how-to 
ms.date: 09/08/2023
ms.prod: windows-iot
ms.custom: template-how-to 
---

# Using WinGet to Install Apps on Windows IoT Enterprise

 The WinGet command line tool enables users to discover, install, upgrade, remove and configure applications on Windows 10 and Windows 11 devices. This tool is the client interface to the Windows Package Manager service.

In this tutorial, you learn how to install and utilize WinGet on Windows IoT Enterprise. This guide is useful for Windows IoT Enterprise LTSC versions as they don't support the Microsoft Store application itself, which is commonly used to install WinGet. The documentation is all tested on Windows 10 IoT Enterprise LTSC 2021.

## Download WinGet

1. Download WinGet bundle files from [WinGet CLI Repo Releases](https://github.com/microsoft/winget-cli/releases).

   1. Choose the latest version that isn't "Prerelease" (It should have the **Latest** tag.)

   1. In my case, this version is version 1.4.10173  
   :::image type="content" source="media/winget-version.png" alt-text="Release screenshot":::

1. Download the `msixbundle` file and the `License1.xml` file.

1. Download the VCLibs Desktop framework package associated with your processor architecture.

   - For Arm64 architecture, download [Microsoft.VCLibs.arm64.14.00.Desktop.appx](https://aka.ms/Microsoft.VCLibs.arm64.14.00.Desktop.appx)

   - For x64 architecture, download [Microsoft.VCLibs.x64.14.00.Desktop.appx](https://aka.ms/Microsoft.VCLibs.x64.14.00.Desktop.appx)  

   For more information, see [How to install and update Desktop framework packages](/troubleshoot/developer/visualstudio/cpp/libraries/c-runtime-packages-desktop-bridge)

1. WinGet CLI has a dependency on `Microsoft.UI.Xaml.2.7`.

   1. Download the `Microsoft.UI.Xaml.2.7` NuGet package from [Microsoft UI NuGet Org](https://www.nuget.org/packages/Microsoft.UI.Xaml/2.7.0). The download link is located on the right side at **Download Package**.
      > [!NOTE]
      > The dependency (<https://www.nuget.org/packages/Microsoft.UI.Xaml/2.7.0>>) is specific to version 2.7.0.
      > Do not use a newer version unless a future release supports it.
      > The installation will fail with 2.8 as of May 18, 2023.

   1. Change the file extension from `.nupkg` to `.zip`. To change the file extension, Open Command Prompt, navigate to the directory where the nupkg file was downloaded and run the following command to rename the file:

   ```cmd
   ren Microsoft.UI.Xaml.2.7.0.nupkg Microsoft.UI.Xaml.2.7.0.zip
   ```

   1. Open the `.zip` folder renamed in the previous step using `File Explorer` and copy the file `tools\AppX\<your architecture>\release\Microsoft.UI.XAML.2.7.appx` to your downloads folder.  This file will be installed to your device in a future step.
      1. For more information about working with `.zip files`, see [zipping and unzipping files.](https://support.microsoft.com/windows/zip-and-unzip-files-8d28fa72-f2f9-712f-67df-f80cf89fd4e5)

## Install WinGet Client

1. Launch PowerShell as Administrator

1. Install the Desktop Framework Package using the PowerShell command [Add-AppxPackage](/powershell/module/appx/add-appxpackage).

   ```powershell
   Add-AppxPackage -Path <path to VCLibs .appx file>
   ```

   Where
   - `<path to VCLibs .appx file>` is the fully qualified path to the VC++ v14 Desktop Framework Package you downloaded earlier.

1. Install Microsoft UI Xaml using the PowerShell command [Add-AppxPackage](/powershell/module/appx/add-appxpackage).

    ```powershell
   Add-AppxPackage -Path <path to UI xaml.appx file>
    ```

   Where

   - `<path to UI xaml.appx file>` is the fully qualified path to the Microsoft UI Xaml 2.7.0 package you downloaded earlier.

   > [!CAUTION]
   > Without the VCLibs and UI Xaml dependencies installed, the WinGet installer fails (without any error/warning messages). Specifically, the "winget.exe" file isn't added to "C:\Users\\[Username]\AppData\Local\Microsoft\WindowsApps"

1. Install the WinGet client using the PowerShell command [Add-AppxPackage](/powershell/module/appx/add-appxpackage).

    ```powershell
   Add-AppxPackage -Path <path to .msixbundle file>
   ```

   Where

   - `<path to .msixbundle file>` is the fully qualified path to the WinGet bundle file you downloaded earlier.

1. Configure the WinGet client with the correct license file using the PowerShell command [Add-AppxProvisionedPackage](/powershell/module/dism/add-appxprovisionedpackage)

   ```powershell
   Add-AppxProvisionedPackage -Online -PackagePath <path to .msixbundle file> -LicensePath <path to xml file>
   ```

   Where

   - `<path to .msixbundle file>` is the fully qualified path to the WinGet bundle file
   - `<path to xml file>` is the fully qualified path to the License1.xml file you downloaded earlier.

   :::image type="content" source="media/add-app-package.png" alt-text="All the commands ran":::

Now, you should see the `winget.exe` file appear at `C:\Users\[Username]\AppData\Local\Microsoft\WindowsApps`. Furthermore, it should also be automatically added to your path. You should also be able to use `WinGet` in the PowerShell terminal.  
:::image type="content" source="media/winget-result.png" alt-text="WinGet in powershell":::

> [!TIP]
> If the `winget` command is not recognized in PowerShell, try restarting PowerShell first, and if unsuccessful again, try restarting your computer.

## Install Applications with WinGet

1. First, search the WinGet repository for the application you want to install. For example, to search for the 'Windows Camera' application, use the `search` command:

   ```powershell
   winget search "Windows Camera"
   ```

1. Next, learn more about the application with the `show` command:

   ```powershell
   winget show "Windows Camera"
   ```

1. Next, install the application with the `install` command:

   ```powershell
   winget install "Windows Camera"
   ```

1. For more detail on how to search, install, configure, and uninstall applications with WinGet, see [**Use WinGet**](/windows/package-manager/winget/#use-winget).

> [!NOTE]
> These instructions are adapted from the [original WinGet documentation](https://github.com/microsoft/winget-cli) targeting Windows desktop editions for Windows IoT Enterprise LTSC which does not have a Windows Store user experience. These instructions also incorporate guidance [Zamiell's WinGet CLI repository discussion](https://github.com/microsoft/winget-cli/discussions/1956) and from [MuradBuyukasik's WinGet Scripts repository](https://github.com/muradbuyukasik/winget-script).

## More Resources

- [Install WinGet on non-IoT LTSC Windows Versions](/windows/package-manager/winget/)
- [Using WinGet and Command Information](/windows/package-manager/winget/)
