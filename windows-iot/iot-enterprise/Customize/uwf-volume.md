---
title: UWF\_Volume
description: UWF\_Volume
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 5e38e50c-c788-4d29-83c8-58b9a3e0f06d
author: TerryWarwick
ms.author: twarwick
ms.prod: windows-iot
ms.technology: iot
ms.date: 05/02/2017
ms.topic: article


---
# UWF\_Volume

This class manages a volume protected by Unified Write Filter (UWF).

## Syntax

```powershell
class UWF_Volume {
    [key, Read] boolean CurrentSession;
    [key, Read] string DriveLetter;
    [key, Read] string VolumeName;
    [Read, Write] boolean BindByDriveLetter;
    [Read] boolean CommitPending;
    [Read, Write] boolean Protected;

    UInt32 CommitFile([in] string FileFullPath);
    UInt32 CommitFileDeletion(string FileName);
    UInt32 Protect();
    UInt32 Unprotect();
    UInt32 SetBindByDriveLetter(boolean bBindByVolumeName);
    UInt32 AddExclusion(string FileName);
    UInt32 RemoveExclusion(string FileName);
    UInt32 RemoveAllExclusions();
    UInt32 FindExclusion([in] string FileName, [out] bFound);
    UInt32 GetExclusions([out, EmbeddedInstance("UWF_ExcludedFile")] string ExcludedFiles[]);

};
```

## Members

The following tables list the methods and properties that belong to this class.

### <a href="" id="mth"></a>Methods

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Method</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="uwf-volumeaddexclusion.md" data-raw-source="[UWF_Volume.AddExclusion](uwf-volumeaddexclusion.md)">UWF_Volume.AddExclusion</a></p></td>
<td><p>Adds a file or folder to the file exclusion list for a volume protected byUWF.</p></td>
</tr>
<tr class="even">
<td><p><a href="uwf-volumecommitfile.md" data-raw-source="[UWF_Volume.CommitFile](uwf-volumecommitfile.md)">UWF_Volume.CommitFile</a></p></td>
<td><p>Commits changes from the overlay to the physical volume for a specified file on a volume protected by Unified Write Filter (UWF).</p></td>
</tr>
<tr class="odd">
<td><p><a href="uwf-volumecommitfiledeletion.md" data-raw-source="[UWF_Volume.CommitFileDeletion](uwf-volumecommitfiledeletion.md)">UWF_Volume.CommitFileDeletion</a></p></td>
<td><p>Deletes a protected file from the volume, and commits the deletion to the physical volume.</p></td>
</tr>
<tr class="even">
<td><p><a href="uwf-volumefindexclusion.md" data-raw-source="[UWF_Volume.FindExclusion](uwf-volumefindexclusion.md)">UWF_Volume.FindExclusion</a></p></td>
<td><p>Determines whether a specific file or folder is in the exclusion list for a volume protected byUWF.</p></td>
</tr>
<tr class="odd">
<td><p><a href="uwf-volumegetexclusions.md" data-raw-source="[UWF_Volume.GetExclusions](uwf-volumegetexclusions.md)">UWF_Volume.GetExclusions</a></p></td>
<td><p>Retrieves a list of all file exclusions for a volume protected byUWF.</p></td>
</tr>
<tr class="even">
<td><p><a href="uwf-volumeprotect.md" data-raw-source="[UWF_Volume.Protect](uwf-volumeprotect.md)">UWF_Volume.Protect</a></p></td>
<td><p>Protects the volume after the next system restart, if UWF is enabled after the restart.</p></td>
</tr>
<tr class="odd">
<td><p><a href="uwf-volumeremoveallexclusions.md" data-raw-source="[UWF_Volume.RemoveAllExclusions](uwf-volumeremoveallexclusions.md)">UWF_Volume.RemoveAllExclusions</a></p></td>
<td><p>Removes all files and folders from the file exclusion list for a volume protected byUWF.</p></td>
</tr>
<tr class="even">
<td><p><a href="uwf-volumeremoveexclusion.md" data-raw-source="[UWF_Volume.RemoveExclusion](uwf-volumeremoveexclusion.md)">UWF_Volume.RemoveExclusion</a></p></td>
<td><p>Removes a specific file or folder from the file exclusion list for a volume protected byUWF.</p></td>
</tr>
<tr class="odd">
<td><p><a href="uwf-volumesetbindbydriveletter.md" data-raw-source="[UWF_Volume.SetBindByDriveLetter](uwf-volumesetbindbydriveletter.md)">UWF_Volume.SetBindByDriveLetter</a></p></td>
<td><p>Sets the <strong>BindByDriveLetter</strong> property, which indicates whether the UWF volume is bound to the physical volume by drive letter or by volume name.</p></td>
</tr>
<tr class="even">
<td><p><a href="uwf-volumeunprotect.md" data-raw-source="[UWF_Volume.Unprotect](uwf-volumeunprotect.md)">UWF_Volume.Unprotect</a></p></td>
<td><p>Disables UWF protection of the volume after the next system restart.</p></td>
</tr>
</tbody>
</table>

### <a href="" id="pro"></a>Properties

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th>Property</th>
<th>Data type</th>
<th>Qualifiers</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>BindByDriveLetter</strong></p></td>
<td><p>Boolean</p></td>
<td><p>[read, write]</p></td>
<td><p>Indicates the type of binding that the volume uses.</p>
<p>Set to <strong>True</strong> to bind the volume by <strong>DriveLetter</strong>(loose binding); set to <strong>False</strong> to bind the volume by <strong>VolumeName</strong> (tight binding).</p></td>
</tr>
<tr class="even">
<td><p><strong>CommitPending</strong></p></td>
<td><p>Boolean</p></td>
<td><p>[read]</p></td>
<td><p>Reserved for Microsoft use.</p></td>
</tr>
<tr class="odd">
<td><p><strong>CurrentSession</strong></p></td>
<td><p>Boolean</p></td>
<td><p>[key, read]</p></td>
<td><p>Indicates which session the object contains settings for.</p>
<p><strong>True</strong> if settings are for the current session; <strong>False</strong> if settings are for the next session that follows a restart.</p></td>
</tr>
<tr class="even">
<td><p><strong>DriveLetter</strong></p></td>
<td><p>string</p></td>
<td><p>[key, read]</p></td>
<td><p>The drive letter of the volume. If the volume does not have a drive letter, this value is <strong>NULL</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>Protected</strong></p></td>
<td><p>Boolean</p></td>
<td><p>[read, write]</p></td>
<td><p>If <strong>CurrentSession</strong> is <strong>true</strong>, indicates whether the volume is currently protected by UWF.</p>
<p>If <strong>CurrentSession</strong> is <strong>false</strong>, indicates whether the volume is protected in the next session after the device restarts.</p></td>
</tr>
<tr class="even">
<td><p><strong>VolumeName</strong></p></td>
<td><p>string</p></td>
<td><p>[key, read]</p></td>
<td><p>The unique identifier of the volume on the current system. The <strong>VolumeName</strong> is the same as the <strong>DeviceID</strong> property of the <a href="/previous-versions/windows/desktop/legacy/aa394515(v=vs.85)" data-raw-source="[Win32_Volume](/previous-versions/windows/desktop/legacy/aa394515(v=vs.85))">Win32_Volume</a> class for the volume.</p></td>
</tr>
</tbody>
</table>

### Remarks

You must use an administrator account to change any properties or call any methods that change the configuration settings.

### Turn UWF protection on or off

The following example demonstrates how to protect or unprotect a volume with UWF by using the Windows Management Instrumentation (WMI) provider in a PowerShell script.

The PowerShellscript creates a function, **Set-ProtectVolume**, that turns UWF protection on or off for a volume. The script then demonstrates how to use the function.

```powershell
$COMPUTER = "localhost"
$NAMESPACE = "root\standardcimv2\embedded"

# Define common parameters

$CommonParams = @{"namespace"=$NAMESPACE; "computer"=$COMPUTER}

# Create a function to protect or unprotect a volume based on the drive letter of the volume

function Set-ProtectVolume($driveLetter, [bool] $enabled) {

# Each volume has two entries in UWF_Volume, one for the current session and one for the next session after a restart
# You can only change the protection status of a drive for the next session

    $nextConfig = Get-WMIObject -class UWF_Volume @CommonParams |
        where {
            $_.DriveLetter -eq "$driveLetter" -and $_.CurrentSession -eq $false
        };

# If a volume entry is found for the drive letter, enable or disable protection based on the $enabled parameter

    if ($nextConfig) {

        Write-Host "Setting drive protection on $driveLetter to $enabled"

        if ($Enabled -eq $true) {
            $nextConfig.Protect() | Out-Null;
        } else {
            $nextConfig.Unprotect() | Out-Null;
        }
    }

# If the drive letter does not match a volume, create a new UWF_volume instance

    else {
    Write-Host "Error: Could not find $driveLetter. Protection is not enabled."
    }
}

# The following sample commands demonstrate how to use the Set-ProtectVolume function
# to protect and unprotect volumes

Set-ProtectVolume "C:" $true
Set-ProtectVolume "D:" $true

Set-ProtectVolume "C:" $false
```

### Manage UWF file and folder exclusions

The following example demonstrates how to manage UWF file and folder exclusions by using the WMI provider in a PowerShell script. The PowerShell script creates four functions, and then demonstrates how to use them.

The first function, **Get-FileExclusions**, displays a list of UWF file exclusions that exist on a volume. Exclusions for both the current session and the next session that follows a restart are displayed.

The second function, **Add-FileExclusion**, adds a file or folder to the UWF exclusion list for a given volume. The exclusion is added for the next session that follows a restart.

The third function, **Remove-FileExclusion**, removes a file or folder from the UWF exclusion list for a given volume. The exclusion is removed for the next session that follows a restart.

The fourth function, **Clear-FileExclusions**, removes all UWF file and folder exclusions from a given volume. The exclusions are removed for the next session that follows a restart.

```powershell
$COMPUTER = "localhost"
$NAMESPACE = "root\standardcimv2\embedded"

# Define common parameters

$CommonParams = @{"namespace"=$NAMESPACE; "computer"=$COMPUTER}

function Get-FileExclusions($driveLetter) {

# This function lists the UWF file exclusions for a volume, both
# for the current session as well as the next session after a restart 

# $driveLetter is the drive letter of the volume

# Get the UWF_Volume configuration for the current session

    $currentConfig = Get-WMIObject -class UWF_Volume @CommonParams |
        where {
            $_.DriveLetter -eq "$driveLetter" -and $_.CurrentSession -eq $true
        };

# Get the UWF_Volume configuration for the next session after a restart

    $nextConfig = Get-WMIObject -class UWF_Volume @CommonParams |
        where {
            $_.DriveLetter -eq "$driveLetter" -and $_.CurrentSession -eq $false
        };

# Display file exclusions for the current session

    if ($currentConfig) {

        Write-Host "The following files and folders are currently excluded from UWF filtering for $driveLetter";

        $currentExcludedList = $currentConfig.GetExclusions()

        if ($currentExcludedList) {
            foreach ($fileExclusion in $currentExcludedList.ExcludedFiles)  {
                Write-Host "  " $fileExclusion.FileName
            }
        } else {
            Write-Host "  None"
        }
    } else {
        Write-Error "Could not find drive $driveLetter";
}

# Display file exclusions for the next session after a restart

    if ($nextConfig) {

        Write-Host ""
        Write-Host "The following files and folders will be excluded from UWF filtering for $driveLetter after the next restart:";

        $nextExcludedList = $nextConfig.GetExclusions()

        if ($nextExcludedList) {
            foreach ($fileExclusion in $nextExcludedList.ExcludedFiles)  {
                Write-Host "  " $fileExclusion.FileName
            }
        } else {
            Write-Host "  None"
        }

        Write-Host ""
    }
}

function Add-FileExclusion($driveLetter, $exclusion) {

# This function adds a new UWF file exclusion to a volume
# The new file exclusion takes effect the next time the device is restarted and UWF is enabled

# $driveLetter is the drive letter of the volume
# $exclusion is the path and filename of the file or folder exclusion

# Get the configuration for the next session for the volume

    $nextConfig = Get-WMIObject -class UWF_Volume @CommonParams |
        where {
            $_.DriveLetter -eq "$driveLetter" -and $_.CurrentSession -eq $false
        };

# Add the exclusion

    if ($nextConfig) {
        $nextConfig.AddExclusion($exclusion) | Out-Null;
        Write-Host "Added exclusion $exclusion for $driveLetter";
    } else {
        Write-Error "Could not find drive $driveLetter";
    }
}

function Remove-FileExclusion($driveLetter, $exclusion) {

# This function removes a UWF file exclusion from a volume
# The file exclusion is removed the next time the device is restarted

# $driveLetter is the drive letter of the volume
# $exclusion is the path and filename of the file or folder exclusion

# Get the configuration for the next session for the volume

    $nextConfig = Get-WMIObject -class UWF_Volume @CommonParams |
        where {
            $_.DriveLetter -eq "$driveLetter" -and $_.CurrentSession -eq $false
        };

# Try to remove the exclusion

    if ($nextConfig) {
        try {
            $nextConfig.RemoveExclusion($exclusion) | Out-Null;
            Write-Host "Removed exclusion $exclusion for $driveLetter";
        } catch {
            Write-Host "Could not remove exclusion $exclusion on drive $driveLetter"
        }
    } else {
        Write-Error "Could not find drive $driveLetter";
    }
}

function Clear-FileExclusions($driveLetter) {

# This function removes all UWF file exclusions on a volume
# The file exclusions are removed the next time the device is restarted

# $driveLetter is the drive letter of the volume

# Get the configuration for the next session for the volume

    $nextConfig = Get-WMIObject -class UWF_Volume @CommonParams |
        where {
            $_.DriveLetter -eq "$driveLetter" -and $_.CurrentSession -eq $false
        };

# Remove all file and folder exclusions

    if ($nextConfig) {
        $nextConfig.RemoveAllExclusions() | Out-Null;
        Write-Host "Cleared all exclusions for $driveLetter";
    } else {
        Write-Error "Could not clear exclusions for drive $driveLetter";
    }
}

# Some examples of using the functions

Clear-FileExclusions "C:"

Add-FileExclusion "C:" "\Users\Public\Public Documents"
Add-FileExclusion "C:" "\myfolder\myfile.txt"

Get-FileExclusions "C:"

Remove-FileExclusion "C:" "\myfolder\myfile.txt"

Get-FileExclusions "C:"
```

## Requirements

| Windows Edition       | Supported |
|:----------------------|:----------|
| Windows 10 Home       | No        |
| Windows 10 Pro        | No        |
| Windows 10 Enterprise | Yes       |
| Windows 10 Education  | Yes       |

## Related topics

[Unified Write Filter](unified-write-filter.md)