---
title: Develop Apps for Windows IoT Enterprise
author: sydbruck
ms.author: sybruckm
ms.date: 2/5/2024
ms.topic: article
ms.service: windows-iot
ms.subservice: iot
description: App development guidance for Windows IoT Enterprise
keywords: IoT Enterprise, App Development
---

# Develop Apps for Windows IoT Enterprise

This page compiles resources on Windows application development to help you get started developing applications for Windows IoT Enterprise devices.

Developing applications for Windows IoT Enterprise devices is much like developing for Windows Client devices. The same applications built for Windows Client run on Windows IoT Enterprise without any modifications. The difference between developing applications for Windows IoT Enterprise and Windows Desktop is the extra consideration that should be taken for the hardware you deploy your application to, and any [Windows IoT customization or lockdown policies](../Customize/customize-overview.md) applied to the device.

## Set Up your Environment

### Install Development Tools

To develop applications for Windows IoT, you need Visual Studio, the Windows SDK, and the Windows App SDK.

|Topic  |Resource  |Description  |
|---------|---------|---------|
|Visual Studio|[Visual Studio](https://visualstudio.microsoft.com/downloads/) | The preferred development tool of many Windows developers, Visual Studio lets you create projects for Windows, and many other platforms. It's a powerful IDE that can help you write, debug, and deploy your apps.        |
|Windows SDK| [Windows SDK](https://developer.microsoft.com/windows/downloads/windows-sdk/)|The Windows SDK is a development platform that lets you build UWP apps and Win32/desktop apps. It's designed around Windows APIs that are coupled to particular versions of the OS.|
|Windows App SDK| [Windows App SDK](/windows/apps/windows-app-sdk/set-up-your-development-environment)|The Windows App SDK complements the Windows SDK by letting you build modern desktop apps that can be installed across Windows versions (down to Windows 10 1809).|

## Start Developing

### Windows App Development

Learn everything about writing apps for Windows devices and explore sample application code.

|Topic  |Resource  |Description  |
|---------|---------|---------|
|Windows Language and Platform Options |[Windows Development Options](/windows/apps/get-started)  |Windows offers a wide range of options for building apps, from the programming language to the application framework. This article contains the information you need to get started building apps. |
|App Framework Comparison |  [App Development Frameworks](/windows/apps/get-started/dev-options) |Evaluate which app development framework is best suited for your app.  |
|Windows App Packaging and Deployment Options   |[Windows apps: packaging, deployment, and process](/windows/apps/get-started/intro-pack-dep-proc)  |Learn how Windows applications are packaged, distributed, and deployed, and how these different options impact your app's run-time process. |
|Sample Code |[Sample applications for Windows development](/windows/apps/get-started/samples)  |This topic compiles sample code for Windows applications that demonstrate specific tasks, features, and API usage patterns. These samples demonstrate features from Windows App SDK / WinUI 3, UWP / WinUI 2, .NET MAUI, and more. |


### Windows IoT App Development Considerations

Learn about Windows app development patterns and features commonly used for Windows IoT devices.

|Topic|Resource|Description|
|---|---|---|
|Embedded Mode |[Embedded mode](../OS-Features/Embedded-Mode.md) |Enables UWP applications to run in the [background](/windows/iot-core/develop-your-app/backgroundapplications), and to use [the lowLevelDevices or the systemManagement UWP application capabilities](/windows/uwp/packaging/app-capability-declarations) |
|Background Applications (UWP)|[Background UWP tasks and applications](/windows/uwp/launch-resume/#background-tasks)|Background Applications are a special type of UWP application that has no UI but can still run code. These apps are commonly used on Windows IoT Core devices and devices without displays. [Embedded Mode](../OS-Features/Embedded-Mode.md) must be enabled in order for Background Applications to run.|
|Windows Services (.NET) |[Windows services](/dotnet/core/extensions/workers) |Windows Services are background processes that that have no UI and are designed to perform specific tasks or functions. Windows Services are commonly used on Windows Client devices and can also be used on Windows IoT devices.|
|UWP Application Deployment|[Deploying and debugging UWP applications](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps)|Describes the various ways you can deploy and debug UWP applications. The most common paradigm for IoT Devices is deploying to a Remote Machine, which [requires extra steps to set up on the IoT device](/windows/uwp/debug-test-perf/deploying-and-debugging-uwp-apps#remote-pc-instructions)|
|UWP Application Debugging|[Debugging UWP applications on remote machines](/visualstudio/debugger/run-windows-store-apps-on-a-remote-machine)|Describes how you debug your application running on a Windows IoT device from your development machine.|


## Developing Applications for ARM64 Devices

### Native vs. Emulated ARM64 Applications
A **Native ARM64 Application** refers to an application that is natively built for Arm64. An **Emulated ARM64 Application** refers to an application that is built for X86 or X64, but uses Windows' built in emulation technology to enable the application to run on ARM64 devices without modification.

Native ARM64 applications have several advantages compared to emulated ARM64 applications including:
- Improved performance
- Lower power consumption
- Better compatibility

The decision to run a ARM64 application natively or emulated on an ARM64 device comes down to what is right for your specific device scenario. It's recommended to build your applications natively for ARM64 so you can take advantage of the benefits on native ARM64 applications. However, it's also perfectly fine to run the application using Windows' built in ARM64 emulation technology.

### How to Add ARM64 Native Support
To add ARM64 Native Support to an existing or a new application, follow the [guide on adding ARM64 support to Windows applications](/windows/arm/add-arm-support)

### Which Windows IoT Enterprise Versions Support App Emulation?

Windows IoT Enterprise supports app emulation on ARM64 devices according to this table. 

|OS Version  |Emulation support on ARM64 devices  |
|---------|---------|
|Windows 10     |X86   |
|Windows 11     |X86, X64   |

### How to Use ARM64 Emulation Technology to Run Your App

To use Windows' built-in emulation technology to run an X86 or X64 application on your ARM64 device, simply deploy the X86 or X64 application to your ARM64 device and run it normally.

## More App Development Resources

### Testing and Debugging

Use Visual Studio to debug your applications and run tests before release. Make sure to select the correct version of Visual Studio from the drop-down at the top of the table of contents pane.

|Topic  |Resource  |Description  |
|---------|---------|---------|
|Debug your apps using Visual Studio|  [Debug your apps using Visual Studio](/visualstudio/debugger/)   |Use the Visual Studio debugger to prepare your apps for release.|
|Explore Testing in Visual Studio|[Visual Studio Testing Tools](/visualstudio/test/getting-started-with-unit-testing)| Explore the testing options available in Visual Studio|
|Unit Testing| [Unit testing in Visual Studio](/visualstudio/test/getting-started-with-unit-testing)| Get started with unit tests in Visual Studio|
|Live Unit Testing|[Live Unit Testing](/visualstudio/test/live-unit-testing-intro)|Live Unit Testing executes your unit tests automatically and in real time as you make code changes. |
|Remote Testing|[Remote Testing in Visual Studio](/visualstudio/test/remote-testing)|Remote testing enables developers to connect Visual Studio 2022 to remote environments for running and debugging tests.|


### Deploying your Application

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

### Other Useful Windows Development Tools

|Topic  |Resource  |Description  |
|---------|---------|---------|
|Install Dev Home   | [Dev Home](/windows/dev-home/)    |Dev Home was introduced with Windows 11, and is a dashboard that provides quick access to the tools you need to develop apps for Windows. It also provides links to training and code samples.   |
|Dev Drive  |[Dev Drive](/windows/dev-drive/)  |In order to speed up common development tasks, you can create a specially formatted drive that is used to store your projects called a Dev Drive.|
|Visual Studio Code   | [Visual Studio Code](https://code.visualstudio.com/)|A highly extensible editor, Visual Studio Code can be customized to support almost any kind of development you can think of. It's a great choice for writing apps for Windows, and other platforms.   |
|Windows Terminal  |[Windows Terminal](/windows/terminal/)  |Windows Terminal is a modern host application for the command-line shells you already love, like Command Prompt, PowerShell, and bash (via Windows Subsystem for Linux (WSL)). It provides a modern, tabbed interface, and supports themes and extensions.  |
|Windows Subsystem for Linux|[Windows Subsystem for Linux](/windows/wsl/install)|WSL lets you run Linux distributions on Windows and is a great way to use open source tools to develop apps for Windows.|
