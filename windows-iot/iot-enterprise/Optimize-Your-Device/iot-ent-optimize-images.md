---
description: How to optimize an IoT Enterprise image
title: Optimize a Windows 10 IoT Enterprise image
ms.date: 12/10/2018
ms.topic: article
author: TerryWarwick
ms.author: twarwick
ms.prod: windows-iot
ms.technology: iot

---

# Optimize a Windows 10 IoT Enterprise image

Windows 10 IoT Enterprise is constantly improving by adding features, like Window AI and Windows Subsystem for Linux 2, that empower businesses to achieve more by providing intelligent solutions to complex problems. With all this progress has come an issue that we've been hearing about from our partners and customers, namely that the OS is simply getting too big.  This is especially problematic for devices with limited disk space; many dedicated devices fall into this category, like thin clients, gaming devices and medical equipment. Image size can also impact boot and deployment time. We've been working on this and now have some ways to reduce the size of Windows 10 IoT Enterprise.

Windows 10 introduced new features that take two separate and independent approaches to reduce the OS footprint:

- The [Compact OS](compact-os.md) feature, when enabled, compresses the files for the entire operating system and lets you run it from the compressed files.  
- The recovery enhancement feature removed the requirement for a separate static recovery image for system reset.  

These two features, on a typical 64-bit Windows system, saves around 6 GB disk space.  This topic focuses on the Compact OS feature in Windows 10 and tell you how to compress the OS files to save disk space, as well as share some best practices to help further reduce image footprint.  

![Chart showing how much space can be saved](images/iot-ent-space-saving-chart.png)
 
## Windows 10 Compact OS feature

Before talking about the Compact OS feature, let's take a quick look at the [WIMBoot feature](https://blogs.windows.com/buildingapps/2014/08/21/ensuring-compatibility-of-desktop-applications-with-wimboot-systems).  WIMBoot stands for Windows Image Boot, and was introduced in a Windows 8.1 Update. It's a deployment option available for UEFI systems to save disk space on devices.  The basic idea of WIMBoot is that the OS image is compressed by default and is only de-compressed if it needs to be modified in any way.  WIMBoot uses the compressed OS WIM file in the recovery partition as the basis, it boots and runs Windows directly out of the WIM file.  The OS WIM in the recovery partition is immutable, and access to the WIM file is managed by a file system filter.  Since the WIM file is immutable, when a file compressed in WIM is opened with write access, it causes the file to be replaced with a full uncompressed version stored on the disk to enable writing to the file .

The WIMBoot feature has a couple of issues.  First, WIMBoot wasn't something that could be easily done. It had to be done at deployment time when the system image was put onto the computer, it was mostly done by OEMs or system administrators. The other issue was when there were security updates to the operating system, more and more system files would be replaced with a full uncompressed versions and over time Windows would grow to fill more and more of the drive space, the benefit of the WIMBoot partition would become less and less.

Windows 10 Compact OS is the evolution of WIMBoot. Similar to WIMBoot, Compact OS installs the operating system files as compressed files and lets you run the operating system from the compressed files to save disk space.  Unlike WIMBoot, Compact OS moved away from the WIM file in the recovery partition and compresses system files on a per-file basis.  Because the files are no longer combined into a single WIM file, Windows update can replace or remove individual files as needed to help maintain the drive footprint size over time.  Compact OS can be enabled or disabled on the fly and is supported on both UEFI-based and BIOS-based devices.

### Using the Compact OS feature

The Compact OS feature can be enabled while deploying Windows or at runtime after Windows is installed. You can enable the Compact OS feature in a couple of ways. Below lists the most common methods. You can check [this page](compact-os.md) for a complete list of methods to deploy Compact OS feature.

#### Deploy Compact OS using a WIM file

1. Boot your destination device with the Windows 10 version of Windows PE.
2. Create a pagefile equal to 256 MB.

    ```cmd
	wpeutil createpagefile C:\pagefile /size=256
    ```

    where `C` is the Windows partition

3. Format and prepare the partitions, and then apply the image to a partition using DISM tool. The `/compact`     parameter enables Compact OS.

    ```cmd
    DISM /Apply-Image /ImageFile:install.wim /Index:1 /ApplyDir:D:\ /compact
	```

#### Deploy Compact OS from Windows Setup

Use an [answer file](/windows-hardware/customize/desktop/unattend/), and set the `Microsoft-Windows-Setup\ImageInstall\OSImage\Compact` setting to `True`.

#### Enable Compact OS at runtime

If you've already installed Windows 10 on your computer, you can use the `compact.exe` tool to query whether Compact OS is enabled and change it at any time.

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

### Performance Impacts of Compact OS

Extensive analysis and tuning were done for the compression algorithm of the Compact OS feature.  For most recent devices (including low-end ones) you shouldn't observe much of a performance downside.

The actual performance impacts really depend on the relative performance of the storage device and the compute device.  Compression means fewer reads, which removes load from the storage device and improves I/O performance; and more decompression, which adds CPU load and decreases performance.  On a system with fast CPU and slow storage I/O, the performance might be better, because the device was I/O bound when reading files sequentially; but that may not be true on a system with different configuration. Because of this, it's strongly recommended to measure the performance running your scenarios on your devices to evaluate the actual impacts of enabling Compact OS feature.

The [Windows Assessment and Deployment Kit (Windows ADK)](/windows-hardware/get-started/adk-install) includes the Windows Assessment Toolkit and the Windows Performance Toolkit. These toolkits provide a complete solution for evaluating overall performance impacts of Compact OS. Typical performance factors that are related to Compact OS are:

- [Boot up and Shutdown time](/windows-hardware/test/assessments/onoff-transition-performance)
- App launch time

In addition to the Windows ADK, you can use the [diskspd](https://gallery.technet.microsoft.com/DiskSpd-A-Robust-Storage-6ef84e62) tool to measure disk i/o performance, such as:

- Disk i/o throughput
- CPU usage when performing disk reads

### Best practices for using Compact OS and UWF

[Unified Write Filter (UWF)](/windows-hardware/customize/enterprise/unified-write-filter) is an optional Windows 10 IoT Enterprise feature that helps to protect your drives by intercepting and redirecting any writes to the drive (e.g. settings changes and saved data) to a virtual overlay. The virtual overlay is a temporary location that is usually cleared during a reboot or when a guest user logs off. When enabling both Compact OS and UWF on a device, you need to consider the order of enabling these two features to make sure both features work properly:

- Enable/Disable Compact OS when UWF is disabled. Enabling or disabling Compact OS means compressing/decompressing the system files.  Since UWF intercepts and redirects any writes to the driver, enabling/disabling Compact OS when UWF is enabled will inflate the overlay and, in many cases, fill the overlay so the system no longer works.  This is no different than changing a lot of files on a regular system with UWF enabled.
- For deployment, the sequence of enabling Compact OS and UWF is to first enable CompactOS and then enable UWF.
- Use UWF servicing mode for any Compact OS configuration changes after deployment. You can follow the instructions in Apply OEM updates to UWF-protected devices to modify the UWF master servicing script to call a custom OEM script and add the Compact OS configuration to the custom OEM script to perform the Compact OS configuration change during UWF servicing mode.

## Additional ways to reduce disk footprint

Consider the following actions to further reduce the disk footprint and keep disk footprint optimized.

### Single Instancing of PPKGs

Enable Single-instancing for LoB apps. Single-instancing allows you to run your LoB apps directly from the compressed provisioning package.  For more details about single-instancing, check the [Single-instancing of provisioning packages](./compact-os.md#single-instancing-of-provisioning-packages).

### Remove Features On Demand (FoD) Packages

Review [preinstalled FoDs](features-on-demand-v2--capabilities.md), uninstall unused FoDs, or not pre-install unwanted FoDs.

Based on Windows 10 IoT Enterprise 2019 LTSC, preinstalled FoDs packages are:

```cmd
Microsoft-Windows-Hello-Face-Migration-Package~31bf3856ad364e35~amd64~~10.0.17763.1
Microsoft-Windows-Hello-Face-Package~31bf3856ad364e35~amd64~~10.0.17763.1
Microsoft-Windows-InternetExplorer-Optional-Package~31bf3856ad364e35~amd64~~11.0.17763.1
Microsoft-Windows-MediaPlayer-Package~31bf3856ad364e35~amd64~~10.0.17763.1
Microsoft-Windows-QuickAssist-Package~31bf3856ad364e35~amd64~~10.0.17763.1
Microsoft-Windows-TabletPCMath-Package~31bf3856ad364e35~amd64~~10.0.17763.1
OpenSSH-Client-Package~31bf3856ad364e35~amd64~~10.0.17763.1
Microsoft-Windows-LanguageFeatures-Basic-en-us-Package~31bf3856ad364e35~amd64~~10.0.17763.1
Microsoft-Windows-LanguageFeatures-Handwriting-en-us-Package~31bf3856ad364e35~amd64~~10.0.17763.1
Microsoft-Windows-LanguageFeatures-OCR-en-us-Package~31bf3856ad364e35~amd64~~10.0.17763.1
Microsoft-Windows-LanguageFeatures-Speech-en-us-Package~31bf3856ad364e35~amd64~~10.0.17763.1
Microsoft-Windows-LanguageFeatures-TextToSpeech-en-us-Package~31bf3856ad364e35~amd64~~10.0.17763.1
```

Please note that the bottom 5 [Language Feature FoD packages](features-on-demand-language-fod.md) will be automatically reinstalled after uninstallation unless the following scheduled task is disabled:

```cmd
\Microsoft\Windows\LanguageComponentsInstaller\Installation
```

Removing all above preinstalled FoDs can save you more than **300MB** of disk space.

### Clean up Component Store

After installing an update, the old versions of OS files are still kept in the component store for a certain period time.  You can use the DISM.exe tool to clean up the store immediately:

```cmd
Dism.exe /online /Cleanup-Image /StartComponentCleanup
```

As a reference, cleaning up the component store (with CompactOS enabled) after installing [KB4523205 LCU update](https://support.microsoft.com/help/4523205/windows-10-update-kb4523205) freed up 1GB of disk space.

You can further reduce the component store size by using the `/ResetBase` option:

```cmd
Dism.exe /online /Cleanup-Image /StartComponentCleanup /ResetBase
```

>[!Note]
>After cleaning up the component store with the ResetBase option, you will no longer be able to uninstall any of the previously installed updates.  The ResetBase option freed up additional 110MB of disk space on the reference update.

See [Clean Up the WinSxS Folder](./clean-up-the-winsxs-folder.md) for more details.

### Disable Hibernation

Hibernation creates hiberfil.sys file, whose max size could be as big as the physical RAM. If you have 16GB physical RAM, hiberfil.sys file could take up about 16GB of your disk space.
If your device doesn't need hibernation, you can disable it:

```cmd
Powercfg.exe /hibernate off
```

If disabling hibernation entirely isn't an option, you can still reduce the size of hiberfil.sys file by compressing the RAM contents.  See [here for more details](/windows-hardware/design/device-experiences/powercfg-command-line-options#option_hibernate).

### Disable the Page File

Disabling the Page file can save several GBs depending on physical RAM size and default memory manager setting. In general, with page file disabled, there's a minimum of **4GB** physical RAM requirement for installing a Quality Update. In addition to meeting the physical RAM requirement, Windows 10 IoT Enterprise OEMs are expected to test their supported scenarios rigorously to ensure the RAM can handle their workload without a page file.  

To disable the page file from the registry, you can set an empty string for the following registry value:

```reg
HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\Session Manager\Memory Management

PagingFiles    REG_MULTI_SZ   <empty string>
```

### Remove Unnecessary Drivers

You can remove drivers from an offline image.

To mount the offline image, run the following command from an elevated command prompt:

```cmd
Dism.exe /Mount-Image /ImageFile:c:\images\install.wim /MountDir:c:\offline
```

Remove specific drivers from the image:

```cmd
Dism.exe /Image:c:\offline /Remove-Driver /Driver:OEM1.inf /Driver:OEM2:inf
```

See [add and remove drivers](./add-and-remove-drivers-to-an-offline-windows-image.md) to learn more about adding and removing drivers.

### Additional File Compression

Enabling Compact OS will compress OS files and some select set of program files, highly optimized for executables and read-only binary files.  For custom read-only program files added by OEMs, you can target and additionally compress them with Compact.exe /EXE options.  

```cmd
Compact.exe /C /S:"c:\Program Files (x86)\ target custom program folder" /EXE:XPRESS8K *.dll  
```

>[!note]
>The `/EXE:<compression algorithm>` option is optimized for executables or read-only files similar to Compact OS.  If files compressed with this option are ever opened for write, they will automatically be decompressed.  The installer of these custom program files is responsible for detecting the files were compressed with "/EXE:XPRESS8K", and must re-compress them after overwriting them.

For writable files, you can use the traditional NTFS compression.  They remain compressed even if they are written to. Also, their performance overhead is higher than "/EXE:" option or Compact OS.

```cmd
Compact.exe /C /S:"c:\Program Files (x86)\target custom program folder" *writable*files*pattern*
```

>[!note]
>Windows 10 IoT Enterprise OEMs are expected to conduct thorough tests to assess perf impact of applying such additional compression beyond Compact OS against their fixed scenarios.

## Test your scenarios

The above guidelines may help you optimize your image and reduce the disk footprint. Based on Windows 10 IoT Enterprise LTSC 2019 evaluation edition, disk footprint for the minimal baseline OS configuration looks like the following table: 
 
| Disk Budget Item (size in MBs) |	Out-of-box Default |	Min Baseline |
| --- | --- | --- |
| Windows OS including WinSxS and SoftwareDistribution |	7377 |	5043 |
| Drivers |	355 |	184 |
| Program Files and Program Data |	665 |	565 |
| User Data |	75 |	75 |
| Recovery Environment |	442 |	0 |
| Page File and SwapFile |	2176 |	0 |
| EFI system partition |	100 |	100 |
| MSR partition	 |	16 | 16 |
| Others  |	126 |	108 |
| Total |	11GB |  	5.8GB |

>[!note]
>This minimal baseline was configured through removing all preinstalled FoD packages, disabling the page file, removing WinRE, and enabling Compact OS. It was captured on a virtual machine with minimum drivers. The actual size for drivers could vary per devices. You also need to reserve additonal space for taking updates.  

Once you have created a final image and deploy to your target device, we recommend that you thoroughly test the scenarios to ensure that your device provides a good user experience.