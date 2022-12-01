Sysprep /Audit

### Step 1. Measure the original size of the Windows Component Store using DISM 
>From an elevated command prompt, run:
>```
>Dism.exe /Online /Cleanup-Image /AnalyzeComponentStore
>```
>More Info: [Determine the Actual Size of the WinSxS Folder](https://learn.microsoft.com/windows-hardware/manufacture/desktop/determine-the-actual-size-of-the-winsxs-folder?view=windows-10)

### Step 2. Install the Latest Cumulative Update (LCU)
> Select *Start*  > *Settings*  > *Windows Update* and apply all updates that are advertised to your device.  Restart after the update(s) are applied if prompted to do so.

### Step 3. After LCU installation, measure the size of the Windows Component Store using DISM again.  
>From an elevated command prompt, run:
>```
>Dism.exe /Online /Cleanup-Image /AnalyzeComponentStore
>```
>More Info: [Determine the Actual Size of the WinSxS Folder](https://learn.microsoft.com/windows-hardware/manufacture/desktop/determine-the-actual-size-of-the-winsxs-folder?view=windows-10)

### Step 4. Clean up the Windows Component Store with ResetBase   
>  Using the /ResetBase parameter together with the /StartComponentCleanup parameter of DISM.exe on a running version of Windows 10 or later removes all superseded versions of every component in the component store.  
>
> From an elevated command prompt, run:
>```
>Dism.exe /online /Cleanup-Image /StartComponentCleanup /ResetBase
>```
>More Info: [Clean Up the WinSxS Folder](https://learn.microsoft.com/windows-hardware/manufacture/desktop/clean-up-the-winsxs-folder?view=windows-10)

### Step 5. After cleaning up the Windows Component Store, measure the size of the Windows Component Store using DISM again.
>From an elevated command prompt, run:
>```
>Dism.exe /Online /Cleanup-Image /AnalyzeComponentStore
>```
>More Info: [Determine the Actual Size of the WinSxS Folder](https://learn.microsoft.com/windows-hardware/manufacture/desktop/determine-the-actual-size-of-the-winsxs-folder?view=windows-10)

---
## Offline Removal of Packages
## Additional Resources
Windows 10
* [Manage the Component Store](https://learn.microsoft.com/windows-hardware/manufacture/desktop/manage-the-component-store?view=windows-10)
* 
* 
* [Reduce the Size of the Component Store in an Offline Windows Image](https://learn.microsoft.com/windows-hardware/manufacture/desktop/reduce-the-size-of-the-component-store-in-an-offline-windows-image?view=windows-10)
* [Take Inventory of an Image or Component usign DISM](https://learn.microsoft.com/windows-hardware/manufacture/desktop/take-inventory-of-an-image-or-component-using-dism?view=windows-10)

Removable Packages
* [Removable Packages Blog](https://aka.ms/RemovablePackagesBlog)
* [Removable Packages Script](https://aka.ms/RemovablePackagesScript)
* [Reduce Disk Footprint](/windows/iot/iot-enterprise/optimize-your-device/reduce-disk-footprint)

