---
title: Using Compact OS
titleSuffix: Windows IoT Enterprise
ms.date: 01/03/2024
ms.topic: article
author: TerryWarwick
ms.author: twarwick
ms.prod: windows-iot
ms.technology: iot
description: Using Compact OS with Windows IoT Enterprise

---

# Using Compact OS with Windows IoT Enterprise

 Compact OS installs the operating system files as compressed files and lets you run the operating system from the compressed files to save disk space.  Compact OS can be enabled or disabled on the fly and is supported on both UEFI-based and BIOS-based devices.

## Enabling the Compact OS feature

The Compact OS feature can be enabled while deploying Windows or at runtime after Windows is installed. You can enable the Compact OS feature in a couple of ways. Below lists the most common methods. For more information, see [Compact OS, single-instancing, and image optimization](/windows-hardware/manufacture/desktop/compact-os).

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

If you've already installed Windows IoT Enterprise on your computer, you can use the `compact.exe` tool to query whether Compact OS is enabled and change it at any time.

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

Extensive analysis and tuning were done for the compression algorithm of the Compact OS feature.  For most recent devices (including low-end ones) you shouldn't observe much of a performance downside.

The actual performance impacts really depend on the relative performance of the storage device and the compute device.  Compression means fewer reads, which removes load from the storage device and improves I/O performance; and more decompression, which adds CPU load and decreases performance.  On a system with fast CPU and slow storage I/O, the performance might be better, because the device was I/O bound when reading files sequentially; but that may not be true on a system with different configuration. Because of this, it's strongly recommended to measure the performance running your scenarios on your devices to evaluate the actual impacts of enabling Compact OS feature.

The [Windows Assessment and Deployment Kit (Windows ADK)](/windows-hardware/get-started/adk-install) includes the Windows Assessment Toolkit and the Windows Performance Toolkit. These toolkits provide a complete solution for evaluating overall performance impacts of Compact OS. Typical performance factors that are related to Compact OS are:

- [Boot up and Shutdown time](/windows-hardware/test/assessments/onoff-transition-performance)
- App launch time

In addition to the Windows ADK, you can use the [diskspd](https://gallery.technet.microsoft.com/DiskSpd-A-Robust-Storage-6ef84e62) tool to measure disk i/o performance, such as:

- Disk i/o throughput
- CPU usage when performing disk reads

## Best practices for using Compact OS and UWF

[Unified Write Filter (UWF)](../Customize/Unified-Write-Filter.md) is an optional Windows IoT Enterprise feature that helps to protect your drives by intercepting and redirecting any writes to the drive (e.g. settings changes and saved data) to a virtual overlay. The virtual overlay is a temporary location that is usually cleared during a reboot or when a guest user logs off. When enabling both Compact OS and UWF on a device, you need to consider the order of enabling these two features to make sure both features work properly:

- Enable/Disable Compact OS when UWF is disabled. Enabling or disabling Compact OS means compressing/decompressing the system files.  Since UWF intercepts and redirects any writes to the driver, enabling/disabling Compact OS when UWF is enabled will inflate the overlay and, in many cases, fill the overlay so the system no longer works.  This is no different than changing a lot of files on a regular system with UWF enabled.
- For deployment, the sequence of enabling Compact OS and UWF is to first enable CompactOS and then enable UWF.
- Use UWF servicing mode for any Compact OS configuration changes after deployment. You can follow the instructions in Apply OEM updates to UWF-protected devices to modify the UWF master servicing script to call a custom OEM script and add the Compact OS configuration to the custom OEM script to perform the Compact OS configuration change during UWF servicing mode.

## Additional File Compression

Enabling Compact OS will compress OS files and some select set of program files, highly optimized for executables and read-only binary files.  For custom read-only program files added by OEMs, you can target and additionally compress them with Compact.exe /EXE options.  

```cmd
Compact.exe /C /S:"c:\Program Files (x86)\ target custom program folder" /EXE:XPRESS8K *.dll  
```

>[!NOTE]
>The `/EXE:<compression algorithm>` option is optimized for executables or read-only files similar to Compact OS.  If files compressed with this option are ever opened for write, they will automatically be decompressed.  The installer of these custom program files is responsible for detecting the files were compressed with "/EXE:XPRESS8K", and must re-compress them after overwriting them.

For writable files, you can use the traditional NTFS compression.  They remain compressed even if they are written to. Also, their performance overhead is higher than "/EXE:" option or Compact OS.

```cmd
Compact.exe /C /S:"c:\Program Files (x86)\target custom program folder" *writable*files*pattern*
```

>[!note]
>Windows IoT Enterprise OEMs are expected to conduct thorough tests to assess perf impact of applying such additional compression beyond Compact OS against their fixed scenarios.

## More Resources

- [Device Optimization Overview](Overview.md)
- [Compact OS, single-instancing, and image optimization](/windows-hardware/manufacture/desktop/compact-os)
