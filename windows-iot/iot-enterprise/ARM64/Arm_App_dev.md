---
title: Develop Apps for Windows IoT Enterprise on ARM64
author: sydbruck
ms.author: sybruckm
ms.date: 12/14/2023
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: App development guidance for Windows IoT Enterprise on ARM64
keywords: IoT Enterprise, ARM64, App Development
---

# Develop Apps for Windows IoT Enterprise on ARM64

Creating applications for Windows IoT Enterprise is much like developing apps for Windows Client. This page has resources to kickstart your journey in app development for Windows IoT Enterprise ARM64 devices.

## Set Up your Environment

### Set up Embedded Mode

Set up your device for Windows app development.

|Topic|Resource|Description|
|---|---|---|
|Enable Embedded Mode |[Embedded mode](../OS-Features/Embedded-Mode.md) |Windows has a special mode for developers that adjusts security settings in order let you run the apps you'are working on. |
|Create a Developer Account |[Create a Developer Account](/windows/apps/get-started/sign-up) |A developer account allows you to publish your apps to the Microsoft Store. |

### Install Development Tools

Microsoft has a series of tools available to streamline app development.

|Topic  |Resource  |Description  |
|---------|---------|---------|
|Install Dev Home   | [Dev Home](/windows/dev-home/)    |Dev Home was introduced with Windows 11, and is a dashboard that provides quick access to the tools you need to develop apps for Windows. It also provides links to training and code samples.   |
|Dev Drive  |[Dev Drive](/windows/dev-drive/)  |In order to speed up common development tasks, you can create a specially formatted drive that is used to store your projects called a Dev Drive.|
|Visual Studio   |[Visual Studio](https://visualstudio.microsoft.com/downloads/) | The preferred development tool of many Windows developers, Visual Studio lets you create projects for Windows, and many other platforms. It's a powerful IDE that can help you write, debug, and deploy your apps.        |
|Visual Studio Code   | [Visual Studio Code](https://code.visualstudio.com/)|A highly extensible editor, Visual Studio Code can be customized to support almost any kind of development you can think of. It's a great choice for writing apps for Windows, and other platforms.   |
|Windows App SDK| [Windows App SDK](/windows/apps/windows-app-sdk/set-up-your-development-environment)|To develop apps for Windows 10 and 11, you will need Visual Studio, the Windows SDK, and the Windows App SDK. |
|Windows SDK| [Windows SDK](/windows/downloads/windows-sdk/)|To develop apps for Windows 10 and 11, you'll need Visual Studio, the Windows SDK, and the Windows App SDK. |
|Windows Terminal  |[Windows Terminal](/windows/terminal/)  |Windows Terminal is a modern host application for the command-line shells you already love, like Command Prompt, PowerShell, and bash (via Windows Subsystem for Linux (WSL)). It provides a modern, tabbed interface, and supports themes and extensions.  |
|Windows Subsystem for Linux|[Windows Subsystem for Linux](/windows/wsl/install)|WSL lets you run Linux distributions on Windows and is a great way to use open source tools to develop apps for Windows.|

## Start Developing

### Windows App Development Options

Understand the options available to you for developing Windows Apps.

|Topic  |Resource  |Description  |
|---------|---------|---------|
|Windows Language and Platform Options |[Windows Development Options](windows/apps/get-started/)  |Windows offers a wide range of options for building apps, including C++, .NET, and other emerging technologies such as open source tools on WSL and Rust. This article contains the information you need to get started building apps for the Windows desktop environment. |
|App Framework Comparison |  [App Development Frameworks](/windows/apps/get-started/dev-options) |Evaluate which app development framework is best suited for your app.  |
|Windows App Packaging and Deployment Options   |[Windows apps: packaging, deployment, and process](/windows/apps/get-started/intro-pack-dep-proc)  |This topic discusses your options concerning whether or not your app will be packaged, how you'll deploy/distribute your app, and your app's run-time process.|
|Windows Services (background apps)   |[Worker Services](/dotnet/core/extensions/workers) |A Windows service is a background process that runs independently of any user interface and is designed to perform specific tasks or functions on a Windows operating system.  |

### Test and Debug

Use Visual Studio to debug your applications and run tests before release. Make sure to select the correct version of Visual Studio from the drop-down at the top of the table of contents pane.

|Topic  |Resource  |Description  |
|---------|---------|---------|
|Debug your apps using Visual Studio|  [Debug your apps using Visual Studio](/visualstudio/debugger/)   |Use the Visual Studio debugger to prepare your apps for release.|
|Explore Testing in Visual Studio|[Visual Studio Testing Tools](/visualstudio/test/getting-started-with-unit-testing)| Explore the testing options available in Visual Studio|
|Unit Testing| [Unit testing in Visual Studio](/visualstudio/test/getting-started-with-unit-testing)| Get started with unit tests in Visual Studio|
|Live Unit Testing|[Live Unit Testing](/visualstudio/test/live-unit-testing-intro)|Live Unit Testing executes your unit tests automatically and in real time as you make code changes. |
|Remote Testing|[Remote Testing in Visual Studio](/visualstudio/test/remote-testing)|Remote testing enables developers to connect Visual Studio 2022 to remote environments for running and debugging tests.|


### Deploy your App

How to publish and share your app. Make sure to select the correct version of Visual Studio from the drop-down at the top of the table of contents pane, and the correct language on the right side above the article title.


|Topic  |Resource |Description  |
|---------|---------|---------|
|Deploy your App Overview  |[Deploy your app using Visual Studio](/visualstudio/deployment/deploying-applications-services-and-components) |Use Visual Studio to deploy your applications.  |
|Deploy to a Local Folder|[Deploy to Local Folder using Visual Studio](/visualstudio/deployment/deploying-applications-services-and-components#deploy-to-a-local-folder)|Deployment to a local folder is typically used for testing or to begin a staged deployment in which another tool is used for final deployment.|
|Publish to Azure| [Publish to Azure using Visual Studio](/visualstudio/deployment/deploying-applications-services-and-components#publish-to-azure)| Publish your application to Azure using Visual Studio.
|Publish to the Web or Network Share| [Publish to the Web using Visual Studio](/visualstudio/deployment/deploying-applications-services-and-components#publish-to-the-web-or-deploy-to-a-network-share)|Publish your app to the web or deploy to a network share in Visual Studio.|
|Create an Installer Package|[Create an installer package](/visualstudio/deployment/deploying-applications-services-and-components#create-an-installer-package-windows-desktop-1)|Use Visual Studio to create a Windows Desktop installer package for your app|
|Publish to the Microsoft Store|[Publish to the Microsoft Store](/visualstudio/deployment/deploying-applications-services-and-components#publish-to-microsoft-store)|Publish firstly to the Microsoft Store.
|Deploy as a Windows App|[Deploy as a Windows app (create an app installer)](/windows/msix/app-installer/create-appinstallerfile-vs)|To package a project as a Windows app that can receive servicing updates, you can create an app installer.|
|Deploy to a Device (UWP)|[Deploy remotely to a device](/visualstudio/debugger/run-windows-store-apps-on-a-remote-machine)|Deploy a UWP for testing on a device.
|Preinstall your app to the OS image|[Preinstall apps using DISM](/windows-hardware/manufacture/desktop/preinstall-apps-using-dism)|This topic covers how to preinstall apps so they're included as part of a Windows image.|
|Install Apps using WinGet|[Using WinGet to Install Apps on Windows IoT Enterprise](../Deployment/install-winget-windows-iot.md)|The WinGet command line tool enables users to discover, install, upgrade, remove and configure applications on Windows 10 and Windows 11 devices.|



## App Emulation on ARM64 Devices

### Which Platforms Support App Emulation?

Windows IoT Enterprise supports app emulation on ARM64 devices according to this table. 

|OS Version  |Emulation support on ARM64 devices  |
|---------|---------|
|Windows 10     |X86   |
|Windows 11     |X86, X64   |

### How to Emulate your App

To emulate an X86 or X64 application on your ARM64 device, load the app on to the device using an appropriate method mentioned in [Deploy your App](#deploy-your-app).

## Get Support

Need personalized support to get your solution running? Microsoft's [App Assure](https://www.microsoft.com/fasttrack/microsoft-365/app-assure) program might be right for you. 
