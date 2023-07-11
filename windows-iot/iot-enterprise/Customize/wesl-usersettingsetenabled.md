---
title: WESL\_UserSetting.SetEnabled
description: WESL\_UserSetting.SetEnabled
MSHAttr:
- 'PreferredSiteName:MSDN'
- 'PreferredLib:/library/windows/hardware'
ms.assetid: 8dc373fe-37f9-45ca-bb0a-38f0e54feef1


ms.date: 05/02/2017
ms.topic: article


---
# WESL\_UserSetting.SetEnabled

This method enables or disables Shell Launcher.

## Syntax

```powershell
[Static] uint32 SetEnabled(
    [In, Required] boolean Enabled
);
```

## Parameters

<a href="" id="enabled"></a>*Enabled*  
\[in, required\] A Boolean value that indicates whether to enable or disable Shell Launcher.

## Return Value

Returns an HRESULT value that indicates [WMI status](/windows/win32/wmisdk/wmi-non-error-constants) or a [WMI error](/windows/win32/wmisdk/wmi-error-constants).

## Remarks

This method enables or disables Shell Launcher by modifying the **Shell** value in the registry key **HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Windows NT\\CurrentVersion\\Winlogon**. If Unified Write Filter (UWF) is enabled, you may need to disable UWF or commit this registry key by using [UWF\_RegistryFilter.CommitRegistry](uwf-registryfiltercommitregistry.md) in order to enable or disable Shell Launcher.

Enabling or disabling Shell Launcher does not take effect until a user signs in.

## Requirements

| Windows Edition       | Supported |
|:----------------------|:----------|
| Windows 10 Home       | No        |
| Windows 10 Pro        | No        |
| Windows 10 Enterprise | Yes       |
| Windows 10 Education  | Yes       |

## Related topics

[WESL\_UserSetting](wesl-usersetting.md)

[Shell Launcher](shell-launcher.md)