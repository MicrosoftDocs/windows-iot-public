---
description: Sysprep, capture, and deploy
title: Sysprep, capture, and deploy
ms.date: 12/10/2018
ms.topic: article
author: TerryWarwick
ms.author: twarwick
ms.prod: windows-iot
ms.technology: iot

---

# Lab 4: Sysprep, capture, and deploy

Now that the reference IoT device has been customized with software and settings, the system will be prepared for mass deployment using Sysprep and then captured to a WIM using DISM. This is the WIM image used during manufacturing to deploy to new systems. 
 
>[!Note] 
>The steps below use a combination of WinPE and DISM to complete the capture process. These tools are freely available from Microsoft. Some tools, like DISM, are included with all Windows installations. Many 3rd party tools also offer image capture and deployment that might work better for your deployment strategy. Choose the tool that is right for your device scenario.
 
For a fully automated approach to these steps consider using the [Windows 10 IoT Enterprise deployment framework](https://github.com/ms-iot/windows-iotent-deploy). 

## Prerequisites 

- Complete at least [Lab 1a](iot-ent-create-a-basic-image.md). This lab covers how to capture the image you created.

- The ADK with the WinPE add-on installed on your technician PC. See [Get the tools you need](iot-ent-get-the-tools-you-need.md) for more information.

## Run Sysprep to complete the Audit process

In [lab 1a](iot-ent-create-a-basic-image.md) you put the system into audit mode, which is a special setup mode where a device maker can pre-install software and configure settings on a reference IoT device. When you've made your customizations in audit mode, you can capture an image of your customized reference device. While audit mode isn't specifically required, it does provide a scenario where the IoT device can be customized online prior to OOBE.

**Sysprep the reference IoT device**

While booted into audit mode on the reference IoT device, run Sysprep from an Administrative Command Prompt to prepare the image for capture:
        
```
C:\Windows\System32\Sysprep\Sysprep.exe /generalize /oobe /shutdown
```

After Sysprep prepares the image, the reference device will shut down. The next time the device boots, it will boot into OOBE.

>[!Caution]
>Don't power the reference IoT device back on until you're ready to capture an image. If the device boots, you'll have to go through the Sysprep process again.
  
## Capture your device image

### Create a WinPE USB drive

In this section, we'll show you how to create a bootable WinPE USB drive. You can use this USB key for both capturing and deploying your image. 

The process outlined in the next steps can be scripted to make capturing and deploying images easier. For a fully automated scenario, see the [Windows 10 IoT Enterprise deployment framework](https://github.com/ms-iot/windows-iotent-deploy)

1. Insert a USB drive into the Technician PC.
    
    >[!Note]
    >Use a drive that's at least 16GB
 
2. On the technician PC, open the **Deployment and Imaging Tools Environment** as administrator. You can find a shortcut to the Deployment and Imaging Tools under Windows Kits in the Start Menu.
 
3. Copy the WinPE files to a working folder:

    ```
    copype amd64 C:\WinPE 
    ```

    This command copies the 64bit WinPE files to C:\WinPE. Note: The destination folder will be created automatically.
 
4. Copy the WinPE files to your USB key.

    ```
    makewinpemedia /ufd C:\WinPE D:
    ```
    Where D: is the USB drive. This command will format the USB drive and erase any data that's on it.

5. Move the USB flash drive from the Technician PC to the reference IoT device. 
 
### Boot the IoT reference device to WinPE and capture the Windows 10 IoT Enterprise OS image

The following steps will capture a WIM image from the reference IoT device's hard drive. This WIM can be used in development or in production. It's common to capture OS images during different stages of the development process. For example, the steps below could be followed to capture a base image of the OS with default apps installed. A later image could be captured with additional end customer apps installed. 
 
1. Boot the reference IoT device from the bootable WinPE USB flash drive. The sequence to select which media to boot from is different from device to device. Consult the documentation for the IoT reference device in order to determine which key to press during boot in order to select the USB flash device as the boot target.
    >[!Important]
    >Don't boot your device until you know which key brings up the device's boot menu. The imaged IoT device is in a Sysprepped state and should not be allowed to boot back into Windows 10 IoT Enterprise.
    
    The system will boot to the WinPE, where you'll see a Command prompt. 
 
2. From the WinPE Command prompt, use DISM to capture an image of the Windows partition: 

    ```
    DISM /capture-image /imagefile:C:\IoTOS.wim /CaptureDir:C:\ /Name:"Windows 10 IoT Enterprise"
    ```
    
    DISM will capture an image of the OS partition and store it on C: drive.

    >[!Note]
    >Your device will have more than one partition, but you only need to capture the Windows partition. Refer to the deployment lab steps on how to re-create the system partition dynamically during deployment. 
 
    **Why are we capturing the image to the C:\ drive?**
    - We temporarily capture the OS image to the C:\ drive because of the size of the captured image. Our USB drive is formatted as Fat32 which has a 4GB file size limit and the OS image is likely to be larger than 4GB. In the next step we'll split the image into smaller files so you can fit your entire image on a single FAT32-partitioned USB drive.
     
    Windows supports multiple partitions on a flash drive which could allow you to have a drive with one Fat32 WinPE partition, and one NTFS partition where you could store a larger captured WIM file. Keep in mind, the default compression for DISM is fast, which speeds up the capture process however results in a larger WIM file. 

    If the image being captured is close to 4GB, try using DISM's `/Compress:max` option, which may remove the need to have the intermediate step of capturing the WIM to the OS partition and then using /Split-image to split it.
 
3. Split the WIM file captured to the C:\ drive into 4GB files and copy to the USB flash drive. From the WinPE command prompt:

   ```
   Dism /Split-Image /ImageFile:C:\IoTOS.wim /SWMFile:D:\IoTOS.swm /FileSize:4000 
   ```
   This command splits the OS image into 4GB chunks.

   Once the OS image is captured to the USB flash drive, it can be combined back into a single WIM on the Technician PC or kept as individual *.swm files. In this lab, we'll use the .SWM files to deploy the image from the USB drive.
 
 
 
 ## Deploy the captured WIM image from WinPE 
 
In this section, we show you how to deploy a WIM image from WinPE. The reference IoT device that we've been creating in these labs should already be in a deployed state; it's been captured in a Sysprepped state and, when deployed, will boot into OOBE. Use the steps below image a clean system. For this lab series, you can move on to [lab 5](iot-ent-shell-launcher-app-launcher.md) from here, since the reference IoT device will be powered on and OOBE completed. 
 
### Use the WinPE USB drive to deploy to new systems 
 
1. Boot the reference IoT device from the USB flash drive. The button or keypress sequence to select which media to boot differs from device to device. Consult your IoT device's documentation to determine which key to press during boot in order to select the USB flash device as the boot target.
    
2. Format the device. From the WinPE command prompt:
     
    ```
    select disk 0 
    clean 
    convert gpt 
    create partition efi size=100 
    format quick fs=fat32 label="System" 
    assign letter="S" 
    create partition msr size=16 
    create partition primary 
    format quick fs=ntfs label="Windows" 
    assign letter="W" 
    ```
 
    >[!Note] 
    >The above Diskpart commands don't create a recovery partition. If you need to configure a recovery partition, see [Configure UEFI/GPT-based hard drive partitions](/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions).
    
3. Deploy the WIM image to the W: drive created in the previous step. From the WinPE command prompt: 

    ```
    DISM /Apply-Image /ImageFile:D:\IoTOS.swm /SWMFile:IoTOS*.swm /ApplyDir:W:\ /Index:1 and press Enter
    ```
 
4. Configure the default BCD on the system. This is a required step as the disk was freshly partitioned and formatted which requires a new BCD. From the WinPE Command Prompt:   
    
    ```
    W:\Windows\System32\bcdboot W:\Windows /s S:
    ```

5. Reboot the system by typing wpeutil reboot at the WinPE Command Prompt. The IoT device will reboot into OOBE.

## Next steps

Now that you've captured and deployed a Windows image, you can configure Windows to launch to a custom Shell. Lab 5 covers how to configure Shell launcher or Assigned Access.

>[!div class="nextstepaction"]
>[Go to lab 5](iot-ent-shell-launcher-app-launcher.md)
