---
title: Unified Write Filter (UWF) feature (unified-write-filter)
description: Unified Write Filter (UWF) feature (unified-write-filter)
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 05f82dbf-64e7-4ed2-8932-9abcfad59598
author: TerryWarwick
ms.author: twarwick
ms.prod: windows-iot
ms.date: 10/02/2018
ms.topic: article


---
# Unified Write Filter (UWF) feature

Unified Write Filter (UWF) is an optional Windows 10 feature that helps to protect your drives by intercepting and redirecting any writes to the drive (app installations, settings changes, saved data) to a virtual overlay. The virtual overlay is a temporary location that is usually cleared during a reboot or when a guest user logs off.

## Benefits

* Provides a clean experience for thin clients and workspaces that have frequent guests, like school, library or hotel computers. Guests can work, change settings, and install software. After the device reboots, the next guest receives a clean experience.

* Increases security and reliability for kiosks, IoT-embedded devices, or other devices where new apps are not expected to be frequently added.

* Can be used to reduce wear on solid-state drives and other write-sensitive media.

* Optimizing Application load timing on boot – it can be faster to resume from a HORM file on every boot rather than reloading the system on each boot

UWF replaces the Windows 7 Enhanced Write Filter (EWF) and the File Based Write Filter (FBWF).

## Features

* UWF can protect most supported writable storage types, including physical hard disks, solid-state drives, internal USB devices, and external SATA devices. You cannot use UWF to protect external removable drives, USB devices or flash drives. Supports both master boot record (MBR) and GUID partition table (GPT) volumes.

* You can use UWF to make read-only media appear to the OS as a writable volume.

* You can manage UWF directly on a Windows 10 device using [uwfmgr.exe](uwfmgrexe.md), or remotely using MDM tools with the [UnifiedWriteFilter CSP](/windows/client-management/mdm/unifiedwritefilter-csp) or the [UWF WMI](uwf-wmi-provider-reference.md).

* You can [update and service UWF-protected devices](service-uwf-protected-devices.md), either by using UWF servicing mode or by adding file and registry exclusions to specific system areas.

* On Windows 10, version 1803, you can use a [persistent overlay](uwfoverlay.md#persistentoverlay) to allow data saved in the virtual overlay to remain even after a reboot.

* On devices with a disk overlay, you can use [freespace passthrough](uwfoverlay.md#freespacepassthrough) to access your drive's additional free space.

* UWF supports paging to increase virtual memory, if the page file exists on an unprotected volume. When paging is used together with a RAM-based overlay, the uptime of the system can be significantly increased.

## Requirements

Supported Operating Systems
- Windows 10/11 Enterprise
- Windows 10/11 IoT Enterprise
- Windows 10 Enterprise LTSC
- Windows 10 IoT Enterprise LTSC
- Windows 10 IoT Core

## Limitations

* File systems:
  * FAT: fully supported.
  * NTFS: fully supported. However, during device startup, NTFS file system journal files can write to a protected volume before UWF has started protecting the volume.
  * Other file systems (example: exFAT): You can protect the volume, but cannot create file exclusions or do file commit operations on the volume. Writes to excluded files still influence the growth of the Overlay.

* The overlay does not mirror the entire volume, but dynamically grows to keep track of redirected writes.

* UWF supports up to 16 terabytes of protected volumes.

* UWF does not support the use of fast startup when shutting down your device. If fast startup is turned on, shutting down the device does not clear the overlay. You can disable fast startup in Control Panel by navigating to **Control Panel** &gt; **All Control Panel Items** &gt; **Power Options** &gt; **System Settings** and clearing the checkbox next to **Turn on fast startup (recommended)**.

* UWF does not support [Storage Spaces](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831739(v=ws.11)).

* On a computer on which [UWF is enabled and used to protect drive C](./uwf-turnonuwf.md#turn-on-uwf-on-a-running-pc), you cannot permanently set the date and time to a past time. If you make such a change, the original date and time settings will be restored after the computer restarts.

  To work around this issue, you must disable UWF before you change the date and time. To do this, run uwfmgr.exe filter disable.

  > [!Note]
  > Do not add the file that retains date and time settings ("%windir%\bootstat.dat") to the [write filter exclusions](./uwfexclusions.md) to work around this issue. Doing this causes Stop error 0x7E (SYSTEM_THREAD_EXCEPTION_NOT_HANDLED) to occur.

## Turn on and configure UWF

UWF is an optional component and is not enabled by default in Windows 10. You must [turn on UWF](uwf-turnonuwf.md) before you can configure it. 

## UWF overlay

You can choose where the overlay is stored (RAM or disk), how much space is reserved, whether the overlay persists after a reboot.

To increase uptime, set up monitoring to check if your overlay is filling up. At certain levels, your device can warn users and/or reboot the device.

To learn more, see [UWF Overlay location and size](uwfoverlay.md).

## Volumes

A volume is a logical unit that represents an area of persistent storage to the file system that is used by the OS. A volume can correspond to a single physical storage device, such as a hard disk, but volumes can also correspond to a single partition on a physical storage device with multiple partitions, or can span across multiple physical storage devices. For example, a collection of hard disks in a RAID array can be represented as a single volume to the OS.

When you configure UWF to protect a volume, you can specify the volume by using either a drive letter or the volume device identifier. To determine the device identifier for a volume, query the **DeviceID** property in the **Win32\_Volume** WMI class.

If you specify a volume using a drive letter, UWF uses *loose binding* to recognize the volume. By using loose binding, drive letters can be assigned to different volumes if the hardware or volume configuration changes. If you specify a volume using the volume device identifier, UWF uses *tight binding* to recognize the volume. By using tight binding, the device identifier is unique to the storage volume and is independent from the drive letter assigned to the volume by the file system.

## Exclusions

If you want to protect a volume with UWF while excluding specific files, folders, or registry keys from being filtered by UWF, you can add them to a [write filter exclusion](uwfexclusions.md) list.

## UWF servicing mode

When a device is protected with UWF, you must use UWF servicing mode commands to service the device and apply updates to an image. You can use UWF servicing mode to apply Windows updates, antimalware signature file updates, and custom software or third-party software updates.

For more information about how to use UWF servicing mode to apply software updates to your device, see [Service UWF-protected devices](service-uwf-protected-devices.md).

## Troubleshooting UWF

UWF uses Windows Event Log to log events, errors and messages related to overlay consumption, configuration changes, and servicing.

For more information about how to find event log information for troubleshooting problems with Unified Write Filter (UWF), see [Troubleshooting Unified Write Filter (UWF)](uwftroubleshooting.md).

## Related topics

[Unbranded Boot](unbranded-boot.md)

[Custom Logon](custom-logon.md)

[Shell Launcher](shell-launcher.md)
