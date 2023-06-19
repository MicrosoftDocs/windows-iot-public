---
title: Windows IoT Enterprise Customization Overview
author: TerryWarwick
ms.author: twarwick
ms.date: 06/19/2023
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Windows IoT Enterprise customizations allow OEMs and system administrators to provide a controlled and specialized experience for end-users of Windows IoT Enterprise based devices..

---
# Customization Overview

Windows IoT Enterprise advanced lockdown features provide a controlled and specialized experience for end-users of Windows IoT Enterprise by allowing OEMs and system administrators to lock down the device interaction experience.

There are many reasons for locking down a device, such as protecting the system from malicious users, providing a custom defined user experience, and increasing system reliability.

You can lock down your Windows IoT Enterprise device by using the lock down features individually or in combination with each other to get the effect you desire for your image. You can, for instance, create a dedicated cashier device that runs a full screen Point of Service (POS) application.

## In this section

| Topic                                                   | Description                                                                                         |
|:--------------------------------------------------------|:----------------------------------------------------------------------------------------------------|
| [Custom Logon](custom-logon.md)  | You can use the Custom Logon feature to suppress Windows 10 UI elements that relate to the Welcome screen and shutdown screen. For example, you can [suppress all elements of the Welcome screen UI](/windows-hardware/customize/enterprise/complementary-features-to-custom-logon) and provide a custom logon UI. You can suppress the ease of access option on the logon screen. You can also suppress the Blocked Shutdown Resolver (BSDR) screen and automatically end applications while the OS waits for applications to close before a shutdown.    |
| [Keyboard Filter](Keyboard-Filter.md)     | Use Keyboard Filter to suppress undesirable key presses or key combinations. Normally, a customer can use certain Windows key combinations like **Ctrl+Alt+Delete** or **Ctrl+Shift+Tab** to alter the operation of a device by locking the screen or using Task Manager to close a running application.   |
| [Shell Launcher](shell-launcher.md)   | Use Shell Launcher to replace the default Windows 10 shell with a custom shell. You can use almost any application or executable as your custom shell, such as a command window or a custom dedicated application.    |
| [Unbranded Boot](unbranded-boot.md)    | Unbranded Boot can suppress Windows elements that appear when Windows starts or resumes and can suppress the crash screen when Windows encounters an error that it cannot recover from.    |
| [Unified Write Filter (UWF)](unified-write-filter.md)    | Use Unified Write Filter (UWF) on your device to help protect your physical storage media, including most standard writable storage types that are supported by Windows, such as physical hard disks, solid-state drives, internal USB devices, external SATA devices, and so on. You can also use UWF to make read-only media appear to the OS as a writable volume.  |

> [!TIP]
> In addition to the customizations above for OEMs, Windows 10 provides a [Mobile device management (MDM)](/windows/client-management/mdm/) to help IT pros manage company security policies and business applications, while avoiding compromise of the users’ privacy on their personal devices. Under MDM, mobile device OEMs can also create custom configuration service providers (CSPs) to manage their devices. For more information, see [Mobile device management](/windows/client-management/mdm/).

## Related topics
