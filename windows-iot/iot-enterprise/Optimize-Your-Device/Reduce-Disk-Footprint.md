---
title: Reduce Disk Footprint
author: rsameser
ms.author: riameser
ms.date: 5/16/2022
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Windows IoT Enterprise features to assist with reducing storage
keywords: IoT Enterprise, FAQ
---

# Reduce Disk Footprint
The following article reviews the various features that are available to assist OEMs to optimize their image to meet the Windows IoT Enterprise LTSC 2021 [minimum storage requirements](/windows/iot/iot-enterprise/hardware-guidance/hardware_requirements) of 16 GB.

## Compact OS
Compact OS installs the operating system files as compressed files. Compact OS is supported on both UEFI-based and BIOS-based devices. When running Compact OS, Windows update can replace or remove individual files as needed to help maintain the drive footprint size over time.

Learn more about [how to enable Compact OS](/windows-hardware/manufacture/desktop/iot-ent-optimize-images?view=windows-11&preserve-view=true) and [how to check if you're running Compact OS](/windows-hardware/manufacture/desktop/compact-os?view=windows-11#check-if-youre-running-compact-os).

## Single-instancing of PPKGs
When you add new Windows desktop applications to a device, you'll capture these changes into a compressed provisioning package for use by the automatic recovery tools. Rather than maintaining both the original files and the provisioning package, you can use DISM to remove the original files, and run from directly from the compressed provisioning package instead. This is known as single-instancing the image.

While single-instancing is supported on both solid-state drives and rotational drives, for performance reasons, you should only use single-instancing on devices with solid-state drives.

To learn more review [Single-instancing of provisioning packages](/windows-hardware/manufacture/desktop/compact-os?view=windows-11#single-instancing-of-provisioning-packages).


## Remove Features On Demand (FoD) Packages
Removing all [preinstalled FoDs](/windows-hardware/manufacture/desktop/features-on-demand-v2--capabilities?view=windows-11) can save you more than 300MB of disk space, review [how to remove FoDs](/windows-hardware/manufacture/desktop/iot-ent-optimize-images?view=windows-11#remove-features-on-demand-fod-packages).

## Clean up Component Store
After installing an update, the old versions of OS files are still kept in the component store for a certain period time. You can use the DISM.exe tool to [clean up the store](/windows-hardware/manufacture/desktop/iot-ent-optimize-images?view=windows-11#clean-up-component-store) immediately.

## Disable Hibernation
Hibernation creates hiberfil.sys file, whose max size could be as big as the physical RAM. If you have 16GB physical RAM, hiberfil.sys file could take up about 16GB of your disk space. If your device doesn't need hibernation, you can [disable it](/windows-hardware/manufacture/desktop/iot-ent-optimize-images?view=windows-11#disable-hibernation).

## Disable the Page File
Disabling the Page file can save several GBs depending on physical RAM size and default memory manager setting. Learn how to [disable the page file from the registry](/windows-hardware/manufacture/desktop/iot-ent-optimize-images?view=windows-11#disable-the-page-file).

## Remove Unnecessary Drivers
You can remove drivers from an offline image. To learn more, review [add and remove drivers](/windows-hardware/manufacture/desktop/add-and-remove-drivers-to-an-offline-windows-image?view=windows-11)

## Additional File Compression
Enabling Compact OS will compress OS files and some select set of program files, highly optimized for executables and read-only binary files. For custom read-only program files added by OEMs, you can target and [additionally compress](/windows-hardware/manufacture/desktop/iot-ent-optimize-images?view=windows-11#additional-file-compression) them with Compact.exe /EXE options.

## Removable Packages
The [removable packages feature](/windows/iot/iot-enterprise/optimize-your-device/removable-packages) enables Windows IoT Enterprise device builders to use DISM to permanently remove specific optional packages that may not be needed for the OEM’s device use case, such as printer drivers and fonts. These packages are explicitly tagged as 'OEM removable' by Microsoft and ensure that feature OS updates do not restore the removed packages. This helps OEMs optimize their device and reduce their overall disk footprint.

## Guidance
Please review our [size requirements and considerations](/windows-hardware/manufacture/desktop/compact-os?view=windows-11#size-requirements-and-considerations) which provide insight on how to configure your device's [hard drive](/windows-hardware/manufacture/desktop/compact-os?view=windows-11#hard-drive), manage [ram](/windows-hardware/manufacture/desktop/compact-os?view=windows-11#ram-pagefilesys-and-hiberfilsys), [language packs and features on demand](/windows-hardware/manufacture/desktop/compact-os?view=windows-11#language-packs-and-features-on-demand), [Windows optional features](/windows-hardware/manufacture/desktop/compact-os?view=windows-11#windows-optional-features), [applications](/windows-hardware/manufacture/desktop/compact-os?view=windows-11#applications) and [user data](/windows-hardware/manufacture/desktop/compact-os?view=windows-11#user-data).  

Once you have created a final image and deploy to your target device, we recommend that you thoroughly test the scenarios to ensure that your device provides a good user experience.
