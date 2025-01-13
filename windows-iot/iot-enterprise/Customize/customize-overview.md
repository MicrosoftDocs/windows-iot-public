---
title: Customizations for IoT Enterprise
description: Windows IoT Enterprise customizations provide a controlled and specialized experience for the end-users of a Windows device by allowing OEMs and system administrators to lock down the Windows device interaction experience.
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: dac59fd3-f5d0-4d02-ac89-0caf7fe3c9dd
author: sydbruck
ms.author: sybruckm
ms.service: windows-iot
ms.subservice: iot
ms.date: 02/27/2024
ms.topic: article


---
# Customizations for IoT Enterprise

> [!TIP]
> In addition to the customizations highlighted in this topic, Windows IoT Enterprise [Mobile device management (MDM)](/windows/client-management/mdm/) to help IT pros manage company security policies and business applications, while avoiding compromise of the users' privacy on their personal devices. Under MDM, mobile device OEMs can also create custom configuration service providers (CSPs) to manage their devices. For more information, see [Mobile device management](/windows/client-management/mdm/).

## Customize using advanced lockdown

Windows 10 Enterprise customizations provide a controlled and specialized experience for the end-users of a Windows 10 device by allowing OEMs and system administrators to lock down the Windows 10 device interaction experience.

There are many reasons for locking down a device, such as protecting the system from malicious users, providing a custom defined user experience, and increasing system reliability.

You can lock down your Windows 10 desktop device by using the lock down features individually or in combination with each other to get the effect you desire for your image. You can, for instance, create a dedicated cashier device that runs a full screen Point of Service (POS) application.

| Topic                                                   | Description                                                                                         |
|:--------------------------------------------------------|:----------------------------------------------------------------------------------------------------|
| [Custom Logon](custom-logon.md)  | You can use the Custom Logon feature to suppress Windows 10 UI elements that relate to the Welcome screen and shutdown screen. For example, you can suppress all elements of the Welcome screen UI and provide a custom logon UI. You can suppress the ease of access option on the logon screen. You can also suppress the Blocked Shutdown Resolver (BSDR) screen and automatically end applications while the OS waits for applications to close before a shutdown.    |
| [Keyboard Filter](/windows/configuration/keyboard-filter)     | Use Keyboard Filter to suppress undesirable key presses or key combinations. Normally, a customer can use certain Windows key combinations like `Ctrl+Alt+Delete` or `Ctrl+Shift+Tab` to alter the operation of a device by locking the screen or using Task Manager to close a running application.   |
| [Shell Launcher](shell-launcher.md)   | Use Shell Launcher to replace the default Windows 10 shell with a custom shell. You can use almost any application or executable as your custom shell, such as a command window or a custom dedicated application.    |
| [Unbranded Boot](unbranded-boot.md)    | Unbranded Boot can suppress Windows elements that appear when Windows starts or resumes and can suppress the crash screen when Windows encounters an error that it cannot recover from.    |
| [Unified Write Filter (UWF)](unified-write-filter.md)    | Use Unified Write Filter (UWF) on your device to help protect your physical storage media, including most standard writable storage types that are supported by Windows, such as physical hard disks, solid-state drives, internal USB devices, external SATA devices, and so on. You can also use UWF to make read-only media appear to the OS as a writable volume.  |

## Windows Desktop Customizations

These are some common ways to customize your Windows device.

| Topic | Description |
|:------|:------------|
| [Customize the taskbar](/windows-hardware/customize/desktop/customize-the-taskbar) | You can pin up to three additional apps to the taskbar by adding a taskbar layout modification file, for example, TaskbarLayoutModification.xml. You can specify different taskbar configurations based on SKU, device locale, or region.                                |
| [Customize the Start layout](/windows-hardware/customize/desktop/customize-start-layout) | Learn how to customize the Start menu with a group of your own tiles. |
| [Customize OOBE](/windows-hardware/customize/desktop/customize-oobe)                     | When customers turn on their Windows PCs for the first time, they will see the Windows Out of Box Experience (OOBE). Customize OOBE to determine how much work customers must do to complete the OOBE screens before they can enjoy their PCs running Windows 10. |
| [Customize the Retail Demo Experience (RDX)](/windows-hardware/customize/desktop/retail-demo-experience)                     | Showcase your new devices on the retail sales floor with a rich, engaging videos and experiences. |
| [Customize the Windows power slider](/windows-hardware/customize/desktop/customize-power-slider) | The Windows Performance Power slider enables end customers to quickly and intelligently trade performance of their system for longer battery life. You can set the default slider mode for both AC and DC, and configure the power settings and PPM options that are engaged in each power slider mode. |
| [Set dark mode](/windows-hardware/customize/desktop/set-dark-mode)                       | This personalization setting for end users allows them to express preference whether to see applications which support the setting in a dark or light mode. You can set the dark mode as the default for apps using Unattend.    |
| [Customize the Get Help app](/windows-hardware/customize/desktop/customize-get-help-app) | The Get Help app empowers customers to self-help with troubleshooters, instant answers, Microsoft support articles, and more, before contacting assisted support. You can customize the Get Help app to surface your support app or support website.                      |
| [Customize SIM card slot names](/windows-hardware/customize/desktop/customize-sim-card-slot-names) | You can customize the names of SIM card slots on the device to more easily differentiate between them. For example, if the device has both an embedded SIM slot and an external SIM slot, customizing the names will help your customers understand which is which. |
| [Customize a Specific Absorption Rate mapping table](/windows-hardware/customize/desktop/customize-sar-mapping-table) | You can configure and store a Specific Absorption Rate (SAR) table for mobile broadband modems in the registry. When a mobile broadband modem is connected to the Windows device, Windows automatically uses the table to map the mobile country code (MCC) of the modem's registered mobile operator (MO) to its appropriate SAR back-off index, and configures the modem with it.                               |
| [Pen and Windows ink](/windows-hardware/customize/desktop/pen-and-ink) | You can create an advanced Pen settings app, or link to your own apps, in the Pen and Windows Ink settings. |
| [Windows SIM Technical Reference](/windows-hardware/customize/desktop/wsim/windows-system-image-manager-technical-reference) | Settings reference for Windows System Image Manager.            |
| [Unattended Windows Setup Reference](/windows-hardware/customize/desktop/unattend/index) | Settings reference for Unattend.                                                              |

## Configure Power Settings

| Topic | Description |
|-------|-------------|
| [Adaptive hibernate](/windows-hardware/customize/power-settings/adaptive-hibernate) |Adaptive hibernate supports triggers which eliminate resume to a dead battery, and provide a great Modern Standby experience by ensuring that the system remains in CS for as long as possible. |
| [Power controls](/windows-hardware/customize/power-settings/power-controls) | Settings in this subgroup include settings that control the system&#39;s power and behavior. |
| [Processor power management options](/windows-hardware/customize/power-settings/configure-processor-power-management-options) | The Windows processor power management (PPM) algorithms allow the OS to efficiently use the available processing resources by balancing the user&#39;s expectations of performance and energy efficiency. |
| [Battery settings](/windows-hardware/customize/power-settings/battery-settings) | Settings in this subgroup control the customization of battery actions and thresholds. |
| [Power button and lid settings](/windows-hardware/customize/power-settings/power-button-and-lid-settings) | Settings in this subgroup control the customization of system button actions. |
| [Display settings](/windows-hardware/customize/power-settings/display-settings) | Settings in this subgroup control the power management of the display. |
| [Disk settings](/windows-hardware/customize/power-settings/disk-settings) | Settings in this subgroup control the power management of disk devices. |
| [Energy Saver settings](/windows-hardware/customize/power-settings/energy-saver-settings) | Settings in this subgroup control the battery threshold and brightness when Energy Saver is turned on. |
| [PCI Express settings](/windows-hardware/customize/power-settings/pci-express-settings) | Settings in this subgroup control the power management of PCI Express links. |
|[Sleep settings](/windows-hardware/customize/power-settings/sleep-settings) | Settings in this subgroup control sleep, resume, and other related functionality. |
| [Other power settings](/windows-hardware/customize/power-settings/no-subgroup-settings) | Settings in this subgroup don't belong to any other subgroup. |
| [Legacy configuration options](/windows-hardware/customize/power-settings/legacy-configuration-options) |
