---
title: Embedded Mode
author: rsameser
ms.author: riameser
ms.date: 1/31/2021
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Learn about the Embedded Mode features of Windows 10 IoT Enterprise.
keywords: IoT Enterprise, Networking
---

# Embedded mode
Embedded Mode is a Win32 service. In Windows 10 it only starts if the user, an application, or another service starts it. When the Embedded Mode service is started, it is runs as LocalSystem in a shared process of svchost.exe along with other services. Embedded Mode is supported on Windows 10 IoT Enterprise.

Embedded Mode enables:
* Background Applications
* Use of the lowLevelDevice capability
* Use of systemManagement capability

## Enable Embedded Mode
To enable embedded mode, you will need to create a provisioning package in Imaging and Configuration Designer (ICD) that sets AllowEmbeddedMode=1. To install ICD, you need to download and install the Windows ADK for Windows 10.

* [Download the Windows ADK for Windows 10](https://go.microsoft.com/fwlink/p/?LinkId=526740)
* [Learn about what's new in the Windows ADK for Windows 10](https://msdn.microsoft.com/library/windows/hardware/dn927348(v=vs.85).aspx)

1. When installing the ADK select **Imaging and Configuration Designer (ICD)**

2. After installation is complete, run **Windows Imaging and Configuration Designer (WICD)**.

    ![WICD Icon](../media/EmbeddedMode/WICD_Icon.png)

3. Click **Advanced provisioning**.  Name the project **AllowEmbeddedMode** and click **Next**.

    ![Step #3](../media/EmbeddedMode/Step3.png)

4. Choose common to **All Windows editions** then **Next**.

    ![Step #4](../media/EmbeddedMode/Step4.png)

5. Click **Finish**.

    ![Step #5](../media/EmbeddedMode/Step5.png)

6. In the search box type **EmbeddedMode** and then click on **AllowEmbeddedMode**.

    ![Step #6](../media/EmbeddedMode/Step6.png)

7. In the center pane set the value of **AllowEmbeddedMode** to **Yes**

    ![Step #7](../media/EmbeddedMode/Step7.png)

8. Click **Export** > **Provisioning Package**

    ![Step #8](../media/EmbeddedMode/Step8.png)

9. Click **Next**.

    ![Step #9](../media/EmbeddedMode/Step9.png)

10. Click **Next**.

    ![Step #10](../media/EmbeddedMode/Step10.png)

11. Click **Next**.

    ![Step #11](../media/EmbeddedMode/Step11.png)

12. Click **Build**.

    ![Step #12](../media/EmbeddedMode/Step12.png)

13. To install the embedded mode .PPKG on Windows IoT Enterprise double-click on the .PPKG.

14. Click **Yes, add it**.

    Click yes on the LUA dialog if it appears, and the click **Yes, add it** on the dialog shown below.

    ![Step #14 Standard](../media/EmbeddedMode/Step14Standard.png)


## Background Applications
[Background Applications](https://docs.microsoft.com/windows/iot-core/develop-your-app/backgroundapplications) are created using the Background Application (IoT) template in Visual Studio.

Background applications run without stopping and without resource limits. Also, if the background application stops for some reason and embedded mode is enabled the background application will be restarted by the system.

While the system will automatically restart background applications, system lockdown features must be enabled to prevent users from stopping or interfering with the operation of Background Applications.

## lowLevel device Capability and lowLevelDevice capability

The **lowLevel** device Capability gives access to low-level hardware interfaces like GPIO, SPI, and I2C.

* [Blinky Sample(GPIO)](https://developer.microsoft.com/windows/iot/samples/helloblinky)
* [Accelerometer Sample](https://github.com/Microsoft/Windows-iotcore-samples/tree/master/Samples/Accelerometer)

The **lowLevelDevices** Capability allows apps to access custom devices when a number of additional requirements are met. This
capability should not be confused with the lowLevel device capability, which allows access to GPIO, I2C, SPI, and PWM devices.

Refer to [App capability declarations](https://docs.microsoft.com/windows/uwp/packaging/app-capability-declarations) for details.

## systemManagment Capability

When you enable the systemManagment capabilities for your application, this is the set of APIs that gets unlocked:  

* [Windows.System.ProcessLauncher](https://msdn.microsoft.com/library/windows/apps/windows.system.processlauncher.aspx)
* [Windows.System.TimeZoneSettings](https://msdn.microsoft.com/library/windows/apps/windows.system.timezonesettings.aspx)
* [Windows.System.ShutdownManager](https://msdn.microsoft.com/library/windows/apps/windows.system.shutdownmanager.aspx)
* [Windows.Globalization.Language.TrySetInputMethodLanguageTag](https://msdn.microsoft.com/library/windows/apps/windows.globalization.language.trysetinputmethodlanguagetag.aspx)

## Debugging Background Applications

If you are debugging on a device and you see either of the following error messages you need to ensure **AllowEmbeddedMode** is enabled on the device and that the Embedded Mode service is running:

* There are no more endpoints available from the endpoint mapper.
* This program is blocked by group policy. For more information, contact your system administrator.
