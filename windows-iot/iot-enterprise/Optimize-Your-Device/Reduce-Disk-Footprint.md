---
title: Reduce Disk Footprint
author: twarwick
ms.author: twarwick
ms.date: 12/20/2022
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Windows IoT Enterprise features to assist with reducing storage
keywords: IoT Enterprise, FAQ
---

# Reduce Disk Footprint
The following article reviews the various features that are available to assist OEMs to optimize their image to meet the Windows IoT Enterprise LTSC [minimum storage requirement](/windows/iot/iot-enterprise/hardware-guidance/hardware_requirements) of 16 GB.

## Compact OS
Compact OS installs the operating system files as compressed files. Compact OS is supported on both UEFI-based and BIOS-based devices. When running Compact OS, Windows update can replace or remove individual files as needed to help maintain the drive footprint size over time.

Learn more about [how to enable Compact OS](/windows-hardware/manufacture/desktop/iot-ent-optimize-images?view=windows-11&preserve-view=true) and [how to check if you're running Compact OS](/windows-hardware/manufacture/desktop/compact-os?view=windows-11#check-if-youre-running-compact-os&preserve-view=true).

## Single-instancing of PPKGs
When you add new Windows desktop applications to a device, you'll capture these changes into a compressed provisioning package for use by the automatic recovery tools. Rather than maintaining both the original files and the provisioning package, you can use DISM to remove the original files, and run directly from the compressed provisioning package instead. This process is known as [single-instancing the image](/windows-hardware/manufacture/desktop/compact-os?view=windows-11#single-instancing-of-provisioning-packages&preserve-view=true).

While single-instancing is supported on both solid-state drives and rotational drives, for performance reasons, you should only use single-instancing on devices with solid-state drives.

## Remove Features On Demand (FoD) Packages
Removing all [preinstalled FoDs](/windows-hardware/manufacture/desktop/features-on-demand-v2--capabilities?view=windows-11&preserve-view=true) can save you more than 300 MB of disk space, review [how to remove FoDs](/windows-hardware/manufacture/desktop/iot-ent-optimize-images?view=windows-11#remove-features-on-demand-fod-packages&preserve-view=true).

## Clean up Component Store
After installing an update, the old versions of OS files are still kept in the component store for a certain period time. You can use the DISM.exe tool to [clean up the store](/windows-hardware/manufacture/desktop/iot-ent-optimize-images?view=windows-11#clean-up-component-store&preserve-view=true) immediately.

## Disable Hibernation
Hibernation creates hiberfil.sys file, whose max size could be as large as the physical RAM. With 16 GB physical RAM, hiberfil.sys file could take up about 16 GB of your disk space. If your device doesn't need hibernation, you can [disable it](/windows-hardware/manufacture/desktop/iot-ent-optimize-images?view=windows-11#disable-hibernation&preserve-view=true).

## Disable the Page File
Disabling the Page file can save several GBs depending on physical RAM size and default memory manager setting. Learn how to [disable the page file from the registry](/windows-hardware/manufacture/desktop/iot-ent-optimize-images?view=windows-11#disable-the-page-file&preserve-view=true).

## Remove Unnecessary Drivers
You can remove drivers from an offline image. To learn more, review [add and remove drivers](/windows-hardware/manufacture/desktop/add-and-remove-drivers-to-an-offline-windows-image?view=windows-11&preserve-view=true)

## More File Compression
Enabling Compact OS will compress OS files and some select set of program files, highly optimized for executables and read-only binary files. For custom read-only program files added by OEMs, you can target and [additionally compress](/windows-hardware/manufacture/desktop/iot-ent-optimize-images?view=windows-11#additional-file-compression&preserve-view=true) them with Compact.exe /EXE options.

## Removable Packages
The [removable packages feature](/windows/iot/iot-enterprise/optimize-your-device/removable-packages) will enable Windows IoT Enterprise device builders to use DISM to permanently remove specific optional packages that may not be needed for the OEM’s device use case, such as printer drivers and fonts. These packages are explicitly tagged as 'OEM removable' by Microsoft and ensure feature OS updates don't restore the removed packages. Removing packages helps OEMs optimize their device and reduce their overall disk footprint.

## Guidance
Review our [size requirements and considerations](/windows-hardware/manufacture/desktop/compact-os?view=windows-11#size-requirements-and-considerations&preserve-view=true) that provide insight on how to configure your device's [hard drive](/windows-hardware/manufacture/desktop/compact-os?view=windows-11#hard-drive&preserve-view=true), manage [ram](/windows-hardware/manufacture/desktop/compact-os?view=windows-11#ram-pagefilesys-and-hiberfilsys&preserve-view=true), [language packs and features on demand](/windows-hardware/manufacture/desktop/compact-os?view=windows-11#language-packs-and-features-on-demand&preserve-view=true), [Windows optional features](/windows-hardware/manufacture/desktop/compact-os?view=windows-11#windows-optional-features&preserve-view=true), [applications](/windows-hardware/manufacture/desktop/compact-os?view=windows-11#applications&preserve-view=true) and [user data](/windows-hardware/manufacture/desktop/compact-os?view=windows-11#user-data&preserve-view=true).  

Once you've created a final image and deploy to your target device, we recommend that you thoroughly test the scenarios to ensure that your device provides a solid user experience.

## More Resources
- [Removable Packages](/windows/iot/iot-enterprise/Optimize-Your-Device/Removable-Packages-Details/Removable-Packages.md)
- [Device Optimization Overview](/windows/iot/iot-enterprise/Optimize-Your-Device/Overview.md)
