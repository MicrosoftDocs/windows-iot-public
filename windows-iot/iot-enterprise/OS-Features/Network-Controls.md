---
title: Network Service Controls
author: TerryWarwick
ms.author: twarwick
ms.date: 03/30/2023
ms.topic: article
ms.service: windows-iot
ms.subservice: iot
description: Learn about the Network Service Controls features of Windows IoT Enterprise.
keywords: IoT Enterprise, zero exhaust, Network service controls
---

# Network Service Controls

> [!NOTE]
>
> Microsoft is [increasing transparency](https://blogs.microsoft.com/on-the-issues/2019/04/30/increasing-transparency-and-customer-control-over-data/) by categorizing the data we collect as required or optional. For more information, see [Changes to Windows diagnostic data](/windows/privacy/changes-to-windows-diagnostic-data-collection).

Learn how to manage various network service control options in Windows IoT Enterprise. If you want to minimize connections from Windows to Microsoft services, or configure privacy settings, there are a number of [settings](/windows/privacy/manage-connections-from-windows-operating-system-components-to-microsoft-services) for consideration.

This [list](/windows/privacy/manage-connections-from-windows-operating-system-components-to-microsoft-services#settings-for-windows-10-enterprise-edition) displays the network connections to Microsoft services by default and shows you how to configure these settings to control the data that is sent to Microsoft.

> [!TIP]
>
> Microsoft strongly recommends customers to not turn off all network connections **unless absolutely necessary** as crucial security patches and updates may be missed, leaving devices vulnerable. Instead it is recommended customers manage their network service controls and pick and choose which connections (if any) to disable.

## Additional Resources

* [Manage Settings for Windows IoT Enterprise](/windows/privacy/manage-connections-from-windows-operating-system-components-to-microsoft-services#settings-for-windows-10-enterprise-edition)
* [Configure Windows diagnostic data in your organization](/windows/privacy/configure-windows-diagnostic-data-in-your-organization)
* [TPMPolicy CSP](/windows/client-management/mdm/tpmpolicy-csp#:~:text=Zero%20exhaust%20is%20defined%20as%20no%20network%20traffic,IP%20addresses%20unless%20directly%20intended%20by%20the%20user.)
