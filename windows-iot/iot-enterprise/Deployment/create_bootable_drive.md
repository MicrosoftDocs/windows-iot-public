---
title: Create A Bootable Windows IoT Enterprise Flash Drive  
description: How to create a bootable Flash Drive to Install Windows IoT Enterprise on a PC 
author: trumanbrown-msft 
ms.author: trumanbrown
ms.topic: how-to 
ms.date: 05/18/2023
ms.prod: windows-iot 
ms.custom: template-how-to 
---

# Create Bootable Installation Media using a Flash Drive

In this tutorial, you learn how to create bootable installation media (USB Drive, SD card) that installs Windows IoT Enterprise (10 or 11) onto a destination PC. You learn how to format the drive, how to copy the Windows IoT Enterprise ISO/DVD files to the media drive, and how to split up the Windows image file if it's too large.

## What You Need

- **Windows installation media**. This media could be an installation .ISO or DVD
  - Refer to the following guide on how to download a Windows IoT Enterprise image:
        - [Windows IoT Enterprise Downloads | Microsoft Learn](https://learn.microsoft.com/windows/iot/iot-enterprise/downloads)
- **Media drive with at least 5GB free space**. This drive will be formatted, so make sure it doesn't have any important files on it.
- **Technician PC** - Windows PC that is used to format the media flash drive
- **Destination PC** - A PC that you'll install Windows on

## Format the Media Drive

In this section, you learn how to format the media drive using diskpart.  

1. Insert the media flash drive to the technician PC
2. Open a Command Prompt with Administrator privileges  
   1. Search **Command Prompt** in Windows search bar and select **Run as Administrator**

3. Start the diskpart program with the following command:

    ```cmd
    diskpart
    ```

    :::image type="content" source="media/diskpart-cmd.png" alt-text="diskpart result":::

4. List the available disks with the following command:

    ```cmd
    list disk
    ```

    :::image type="content" source="media/list-disk-cmd.png" alt-text="list disk result":::

5. Select the appropriate disk that you wish to format. Typically Disk 0 is your main drive with Windows installed, so do NOT select that disk. **Ensure you choose the correct disk, you will wipe all of the data on it.**

    ```cmd
    select disk <disk_number>
    ```

    :::image type="content" source="media/select-disk-cmd.png" alt-text="select disk result":::

6. Clean the selected disk. This wipes the drive.

    ```cmd
    clean
    ```

    :::image type="content" source="media/clean-cmd.png" alt-text="clean result":::

7. Create a primary partition for the disk.

    ```cmd
    create partition primary
    ```

    :::image type="content" source="media/create-partition-cmd.png" alt-text="create partition result":::

8. Select the primary partition you created.

    ```cmd
    select partition 1
    ```

    :::image type="content" source="media/select-partition-cmd.png" alt-text="select partition result":::

9. Mark the partition you selected as active

    ```cmd
    active
    ```

    :::image type="content" source="media/active-cmd.png" alt-text="active result":::

10. Format the drive into NTFS format

    ```cmd
    format fs=ntfs quick
    ```

    :::image type="content" source="media/format-cmd.png" alt-text="format result":::

11. Assign the disk a letter to be used later.

    ```cmd
    assign
    ```

    :::image type="content" source="media/assign-cmd.png" alt-text="assign result":::

12. Exit the dispart application.

    ```cmd
    exit
    ```

    :::image type="content" source="media/exit-cmd.png" alt-text="exit result":::

## Copy Windows IoT ISO/DVD Files to the Media Drive

1. Navigate to your downloaded Windows IoT Enterprise ISO/DVD
1. Mount the image by either double clicking or right clicking and selecting **Mount**
1. Once mounted, copy all contents from the ISO/DVD and paste them into the formatted media Drive using either file explorer or the command prompt
    1. **Using File Explorer**: Press CTRL-A or select and drag to select all files/folders in the mounted ISO/DVD. Then, copy/paste or drag those selected files into the drive.
    2. **Using Command Prompt**: Run the command

    ```cmd
    robocopy <Mounted_ISO> <Media_Drive> /e
    ```  

    This may take many minutes.  
    :::image type="content" source="media/robocopy-result.png" alt-text="robocopy result":::

> [!IMPORTANT]
> The install.wim file may be too large to copy onto the drive, as shown in the next picture. If so, skip to the [**Split Windows Image into Smaller Files**](#split-windows-image-into-smaller-files-if-necessary)
> :::image type="content" source="media/wim-too-large.png" alt-text="file too large result":::

## Split Windows Image into Smaller Files (If necessary)

1. Copy everything except the Windows image file (sources\install.wim) to the drive (either drag and drop, or use this command with the command prompt.
    1. Open the command prompt by searching **Command Prompt** in Windows search bar, and run the following command, changing the drive letters (e:, d:, etc.) as needed

    ```cmd
    robocopy <Mounted_ISO> <Media_Drive> /s /max:3800000000
    ```

    :::image type="content" source="media/robocopy-large-result.png" alt-text="robocopy large result":::
    2. This command copies all files less than 3.8 GB from the mounted ISO to the flash drive (everything except the install.wim)
2. Open a Command Prompt with Administrator privileges
    1. Search Command Prompt in Windows search bar and select Run as Administrator
3. Run the following command to split the windows image into a set of smaller .swm files and copy them to the drive. Ensure there are no file explorer sessions open within the media drive or the mounted ISO.

    ```cmd
    Dism /Split-Image /ImageFile:<Mounted_ISO>:\sources\install.wim /SWMFile:<Media_Drive>:\sources\install.swm /FileSize:3800
    ```

     1. \<Mounted_ISO\>:\sources\install.wim is the large install.wim file from the mounted ISO/DVD
     2. \<Media_Drive\>:\sources\install.swm is the destination name and the location for the split .swm files on the media Drive. The first split .swm file is named install.swm. The file names for the next files include numbers, for example, install2.swm file, install3.swm file, and so on.
     3. 3800 is the maximum size in MB for each of the split .swm files to be created.  
     :::image type="content" source="media/dism-cmd.png" alt-text="dism result":::
     4. **This can take up to 20 minutes, do not close out the command prompt session**
4. You should now see all the ISO/DVD files on your Media Drive.

## Install Windows IoT To The Destination PC

1. Connect the media drive to the destination PC
2. Turn on the PC and press the key that opens the boot-device selection menu for the computer, such as the Esc/F10/F12 keys. Select the option that boots the PC from the media drive.
3. Windows Setup starts. Follow the on-screen instructions to install Windows

## Additional Resources

- [Create Installation Media for Windows](https://support.microsoft.com/en-us/windows/create-installation-media-for-windows-99a58364-8c02-206f-aa6f-40c3b507420d)
