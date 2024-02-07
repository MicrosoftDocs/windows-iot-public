---
title: Using Compact OS to optimize storage footprint
titleSuffix: Windows IoT Enterprise
ms.date: 01/08/2024
ms.topic: article
author: TerryWarwick
ms.author: twarwick
ms.service: windows-iot
ms.subservice: iot
description: Using Compact OS with Windows IoT Enterprise

---

# Using Compact OS with Windows IoT Enterprise

Applies to:  
✅ Windows 11 IoT Enterprise  
✅ Windows 10 IoT Enterprise  
✅ Windows 10 IoT Enterprise LTSC 2021  

 Compact OS installs the operating system files as compressed files and lets you run the operating system from the compressed files to save disk space.  Compact OS can be enabled or disabled on the fly and is supported on both UEFI-based and BIOS-based devices.

## Enabling the Compact OS feature

The Compact OS feature can be enabled while deploying Windows or at runtime after Windows is installed. You can enable the Compact OS feature in multiple ways. This article provides the most common methods for creating and managing the Compact OS feature. For more information, see [Compact OS, single-instancing, and image optimization](/windows-hardware/manufacture/desktop/compact-os).

### Deploy Compact OS using a WIM file

1. Boot your destination device with Windows PE based on Windows 10 or later.
1. Create a pagefile equal to 256 MB.

    ```cmd
    wpeutil createpagefile C:\pagefile /size=256
    ```

    where `C` is the Windows partition

1. Format and prepare the partitions, and then apply the image to a partition using DISM tool. The `/compact`     parameter enables Compact OS.

    ```cmd
    DISM /Apply-Image /ImageFile:install.wim /Index:1 /ApplyDir:D:\ /compact
    ```

### Deploy Compact OS from Windows Setup

Use an [answer file](/windows-hardware/customize/desktop/unattend/), and set the `Microsoft-Windows-Setup\ImageInstall\OSImage\Compact` setting to `True`.

### Enable Compact OS at runtime

If Windows IoT Enterprise already installed on your device, you can use the `compact.exe` command-line utility to query whether Compact OS is enabled or change the Compact OS configuration anytime.

In an elevated command Window:

To enable Compact OS:

```cmd
Compact /compactos:always
```

To query if Compact OS is enabled:

```cmd
Compact /compactos:query
```

To disable Compact OS:

```cmd
Compact /compactos:never
```

## Performance Impacts of Compact OS

The default compression algorithm is optimized for the most common use cases of Compact OS. For relatively new devices, you shouldn't observe much of a performance downside, especially if using a solid-state drive.

The actual performance impacts really depend on the relative performance of the storage device and the compute device.  Compression means fewer reads, which removes load from the storage device and improves I/O performance; and more decompression, which adds CPU load and decreases performance.  On a system with fast CPU and slow storage I/O, the performance might be better, because the device was I/O bound when reading files sequentially; but that might not be true on a system with different configuration. Measure the performance of your scenarios to evaluate the impact of enabling Compact OS is recommended.

The [Windows Assessment and Deployment Kit (Windows ADK)](/windows-hardware/get-started/adk-install) includes the Windows Assessment Toolkit and the Windows Performance Toolkit. These toolkits provide a complete solution for evaluating overall performance impacts of Compact OS. Typical performance factors that are related to Compact OS are:

- [Boot up and Shutdown time](/windows-hardware/test/assessments/onoff-transition-performance)
- App launch time

In addition to the Windows ADK, you can use the [diskspd](https://github.com/microsoft/diskspd) tool to measure disk i/o performance, such as:

- Disk i/o throughput
- CPU usage when performing disk reads

## Best practices for using Compact OS and UWF

[Unified Write Filter (UWF)](../Customize/Unified-Write-Filter.md) protects your storage devices by intercepting and redirecting any writes to the drive to a virtual overlay. UWF intercepts writes to storage and redirects them to the virtual overlay. Enabling or disabling Compact OS while UWF is enabled fills the overlay reducing performance. In addition, the overlay is cleared when the system is rebooted.  When Compact OS is enabled while UWF is already protecting the storage, rebooting the system reverts the Compact OS enabling.  Consider the following sequence guidance when using both Compact OS and UWF on a device:

- During deployment, enabling Compact OS must occur before UWF is enabled.
- To change state of Compact OS after deployment, first disable UWF then Enable or Disable Compact OS before re-enabling UWF.
- To change Compact OS configuration after deploying Compact OS and UWF use UWF servicing mode. For more information, see [Service UWF-protected devices](../Customize/uwf-servicing.md).

## More file compression options

Enabling Compact OS compresses OS files and some select set of program files, highly optimized for executables and read-only binary files.  For custom read-only program files added by OEMs, you can target and additionally compress them with Compact.exe /EXE options.  

```cmd
Compact.exe /C /S:"c:\Program Files (x86)\ target custom program folder" /EXE:XPRESS8K *.dll  
```

>[!NOTE]
>The `/EXE:<compression algorithm>` option is optimized for executables or read-only files similar to Compact OS.  If files compressed with this option are ever opened for write, they will automatically be decompressed.  The installer of these custom program files is responsible for detecting the files were compressed with "/EXE:XPRESS8K", and must re-compress them after overwriting them.

For writable files, you can use the traditional NTFS compression.  They remain compressed even if they're written to. Also, their performance overhead is higher than "/EXE:" option or Compact OS.

```cmd
Compact.exe /C /S:"c:\Program Files (x86)\target custom program folder" *writable*files*pattern*
```

>[!note]
>Windows IoT Enterprise OEMs are expected to conduct thorough tests to assess performance impact of applying such additional compression beyond Compact OS against their fixed scenarios.

## More Resources

- [Device Optimization Overview](Overview.md)
- [Compact OS, single-instancing, and image optimization](/windows-hardware/manufacture/desktop/compact-os)
