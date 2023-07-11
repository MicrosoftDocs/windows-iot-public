---
title: UWF\_RegistryFilter
description: UWF\_RegistryFilter
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 2511deb5-4103-4f3e-9f3b-dfa6b40516f7


ms.date: 05/02/2017
ms.topic: article


---
# UWF\_RegistryFilter

Adds or removes registry exclusions from Unified Write Filter (UWF) filtering, and also commits registry changes.

## Syntax

```powershell
class UWF_RegistryFilter{
    [key, Read] boolean CurrentSession;
    [Read, Write] boolean PersistDomainSecretKey;
    [Read, Write] boolean PersistTSCAL;

    UInt32 AddExclusion(
        string RegistryKey
    );
    UInt32 RemoveExclusion(
        string RegistryKey
    );
    UInt32 FindExclusion(
        [in] string RegistryKey,
        [out] boolean bFound
    );
    UInt32 GetExclusions(
        [out, EmbeddedInstance("UWF_ExcludedRegistryKey")] string ExcludedKeys[]
    );
    UInt32 CommitRegistry(
        [in] string RegistryKey,
        [in] string ValueName
    );
    UInt32 CommitRegistryDeletion(
        string Registrykey,
        string ValueName
    );
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
<td><p><a href="uwf-registryfilteraddexclusion.md" data-raw-source="[UWF_RegistryFilter.AddExclusion](uwf-registryfilteraddexclusion.md)">UWF_RegistryFilter.AddExclusion</a></p></td>
<td><p>Adds a registry key to the registry exclusion list for UWF.</p></td>
</tr>
<tr class="even">
<td><p><a href="uwf-registryfiltercommitregistry.md" data-raw-source="[UWF_RegistryFilter.CommitRegistry](uwf-registryfiltercommitregistry.md)">UWF_RegistryFilter.CommitRegistry</a></p></td>
<td><p>Commits changes to the specified registry key and value.</p></td>
</tr>
<tr class="odd">
<td><p><a href="uwf-registryfiltercommitregistrydeletion.md" data-raw-source="[UWF_RegistryFilter.CommitRegistryDeletion](uwf-registryfiltercommitregistrydeletion.md)">UWF_RegistryFilter.CommitRegistryDeletion</a></p></td>
<td><p>Deletes the specified registry key or registry value and commits the deletion.</p></td>
</tr>
<tr class="even">
<td><p><a href="uwf-registryfilterfindexclusion.md" data-raw-source="[UWF_RegistryFilter.FindExclusion](uwf-registryfilterfindexclusion.md)">UWF_RegistryFilter.FindExclusion</a></p></td>
<td><p>Determines whether a specific registry key is excluded from being filtered by UWF.</p></td>
</tr>
<tr class="odd">
<td><p><a href="uwf-registryfiltergetexclusions.md" data-raw-source="[UWF_RegistryFilter.GetExclusions](uwf-registryfiltergetexclusions.md)">UWF_RegistryFilter.GetExclusions</a></p></td>
<td><p>Retrieves all registry key exclusions from a system that is protected by UWF.</p></td>
</tr>
<tr class="even">
<td><p><a href="uwf-registryfilterremoveexclusion.md" data-raw-source="[UWF_RegistryFilter.RemoveExclusion](uwf-registryfilterremoveexclusion.md)">UWF_RegistryFilter.RemoveExclusion</a></p></td>
<td><p>Removes a registry key from the registry exclusion list for Unified Write Filter (UWF).</p></td>
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
<td><p><strong>CurrentSession</strong></p></td>
<td><p>Boolean</p></td>
<td><p>[key, read]</p></td>
<td><p>Indicates which session the object contains settings for.</p>
<p><strong>True</strong> if settings are for the current session; <strong>False</strong> if settings are for the next session that follows a restart.</p></td>
</tr>
<tr class="even">
<td><p><strong>PersistDomainSecretKey</strong></p></td>
<td><p>Boolean</p></td>
<td><p>[read, write]</p></td>
<td><p>Indicates if the domain secret registry key is in the registry exclusion list. If the registry key is not in the exclusion list, changes are not persisted after a restart.</p>
<p>Set to <strong>True</strong> to include in the exclusion list; otherwise, set to <strong>False</strong>.</p></td>
</tr>
<tr class="odd">
<td><p><strong>PersistTSCAL</strong></p></td>
<td><p>Boolean</p></td>
<td><p>[read, write]</p></td>
<td><p>Indicates if the Terminal Server Client Access License (TSCAL) registry key is in the UWF registry exclusion list. If the registry key is not in the exclusion list, changes are not persisted after a restart.</p>
<p>Set to <strong>True</strong> to include in the exclusion list; otherwise, set to <strong>False</strong>.</p></td>
</tr>
</tbody>
</table>

### Remarks

Additions or removals of registry exclusions, including changes to the values of **PersistDomainSecretKey** and **PersistTSCAL**, take effect after the next restart in which UWF is enabled.

You can only add registry keys in the HKLM registry root to the UWF registry exclusion list.

You can also use **UWF\_RegistryFilter** to exclude the domain secret registry key and the TSCAL registry key from UWF filtering.

### Example

The following example demonstrates how to manage UWF registry exclusions by using the Windows Management Instrumentation (WMI) provider in a PowerShell script.

The PowerShell script creates four functions, and then demonstrates how to use them.

The first function, **Get-RegistryExclusions**, displays a list of UWF registry exclusions for both the current session and the next session that follows a restart.

The second function, **Add-RegistryExclusion**, adds a registry entry to the UWF registry exclusion list after you restart the device.

The third function, **Remove-RegistryExclusion**, removes a registry entry from the UWF exclusion list after you restart the device.

The fourth function, **Clear-RegistryExclusions**, removes all UWF registry exclusions. You must restart the device before UWF stops filtering the exclusions.

```powershell
$COMPUTER = "EMBEDDEDDEVICE"
$NAMESPACE = "root\standardcimv2\embedded"

# Define common parameters

$CommonParams = @{"namespace"=$NAMESPACE; "computer"=$COMPUTER}

function Get-RegistryExclusions() {

# This function lists the UWF registry exclusions, both
# for the current session as well as the next session after a restart.


# Get the UWF_RegistryFilter configuration for the current session

    $currentConfig = Get-WMIObject -class UWF_RegistryFilter @CommonParams |
        where {
            $_.CurrentSession -eq $true
        };

# Get the UWF_RegistryFilter configuration for the next session after a restart

    $nextConfig = Get-WMIObject -class UWF_RegistryFilter @CommonParams |
        where {
            $_.CurrentSession -eq $false
        };

# Display registry exclusions for the current session

    if ($currentConfig) {

        Write-Host ""
        Write-Host "The following registry entries are currently excluded from UWF filtering:";

        $currentExcludedList = $currentConfig.GetExclusions()

        if ($currentExcludedList.ExcludedKeys) {
            foreach ($registryExclusion in $currentExcludedList.ExcludedKeys)  {
                Write-Host "  " $registryExclusion.RegistryKey
            }
        } else {
            Write-Host "  None"
        }
    } else {
        Write-Error "Could not retrieve UWF_RegistryFilter.";
}

# Display registry exclusions for the next session after a restart

    if ($nextConfig) {

        Write-Host ""
        Write-Host "The following registry entries will be excluded from UWF filtering after the next restart:";

        $nextExcludedList = $nextConfig.GetExclusions()

        if ($nextExcludedList.ExcludedKeys) {
            foreach ($registryExclusion in $nextExcludedList.ExcludedKeys)  {
                Write-Host "  " $registryExclusion.RegistryKey
            }
        } else {
            Write-Host "  None"
        }
        Write-Host ""
    }
}

function Add-RegistryExclusion($exclusion) {

# This function adds a new UWF registry exclusion.
# The new registry exclusion takes effect the next time the device is restarted and UWF is enabled.

# $exclusion is the path of the registry exclusion

# Get the UWF_RegistryFilter configuration for the next session after a restart

    $nextConfig = Get-WMIObject -class UWF_RegistryFilter @CommonParams |
        where {
            $_.CurrentSession -eq $false
        };

# Add the exclusion

    if ($nextConfig) {
        $nextConfig.AddExclusion($exclusion) | Out-Null;
        Write-Host "Added exclusion $exclusion.";
    } else {
        Write-Error "Could not retrieve UWF_RegistryFilter";
    }
}

function Remove-RegistryExclusion($exclusion) {

# This function removes a UWF registry exclusion.
# The registry exclusion is removed the next time the device is restarted

# $exclusion is the path of the registry exclusion

# Get the UWF_RegistryFilter configuration for the next session after a restart

    $nextConfig = Get-WMIObject -class UWF_RegistryFilter @CommonParams |
        where {
            $_.CurrentSession -eq $false
        };

# Try to remove the exclusion

    if ($nextConfig) {
        try {
            $nextConfig.RemoveExclusion($exclusion) | Out-Null;
            Write-Host "Removed exclusion $exclusion.";
        } catch {
            Write-Host "Could not remove exclusion $exclusion."
        }
    } else {
        Write-Error "Could not retrieve UWF_RegistryFilter";
    }
}

function Clear-RegistryExclusions() {

# This function removes all UWF registry exclusions
# The registry exclusions are removed the next time the device is restarted

# Get the configuration for the next session

    $nextConfig = Get-WMIObject -class UWF_RegistryFilter @CommonParams |
        where {
            $_.CurrentSession -eq $false
        };

# Remove all registry exclusions

    if ($nextConfig) {

        Write-Host "Removing all registry exclusions:";

        $nextExcludedList = $nextConfig.GetExclusions()

        if ($nextExcludedList) {
            foreach ($registryExclusion in $nextExcludedList.ExcludedKeys)  {
                Write-Host "Removing:" $registryExclusion.RegistryKey
                $nextConfig.RemoveExclusion($registryExclusion.RegistryKey) | Out-Null
            }
        } else {
            Write-Host "No registry exclusions to remove."
        }
        Write-Host ""
    }
}

# Some examples of using the functions

Clear-RegistryExclusions

Get-RegistryExclusions

Add-RegistryExclusion "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Internet Explorer"
Add-RegistryExclusion "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\DateTime\Servers\(Default)"

Get-RegistryExclusions

Remove-RegistryExclusion "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Internet Explorer"

Get-RegistryExclusions

Clear-RegistryExclusions
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
