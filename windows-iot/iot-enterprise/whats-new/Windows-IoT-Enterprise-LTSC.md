---
title: Windows IoT Enterprise LTSC
description: Learn about Windows IoT Enterprise LTSC.
ms.prod: windows-iot
author: TerryWarwick
ms.author: twarwick
ms.topic: article
ms.technology: iot
ms.date: 06/08/2023
---

# Windows IoT Enterprise LTSC

## Overview

Windows IoT Enterprise LTSC is designed for specialty devices and use cases where functionality and features remain constant for the life of the device.  These devices are typically found in industries including, but not limited to, banking, healthcare, hospitality, manufacturing and retail. Devices that require regulatory certification and devices that perform a critical business function can't accept feature updates for years at a time.  

We designed Windows IoT Enterprise LTSC with these use cases in mind. We support each Windows IoT Enterprise LTSC release for 10 years, and that features and functionality don't change over the course of that 10-year lifecycle.

Windows IoT Enterprise LTSC releases approximately every three years, and each release contains all the new capabilities and support included in Windows feature updates that have been released since the previous LTSC release.  LTSC releases are named with a specific year, such as Windows 10 IoT Enterprise LTSC 2021.

Windows IoT Enterprise LTSC releases receive 10 years of servicing and support. Upgrading from one version of Windows IoT Enterprise LTSC to the next version requires a new license.

## Availability

Windows IoT Enterprise LTSC is available for Windows IoT Enterprise device makers through an authorized [Windows IoT Distributor](https://aka.ms/IoTDistributorList) for building new devices. Windows IoT Enterprise is intended for fixed purpose devices with specific allowances and restrictions in the license agreement. For more information, see [Licensing and Usage](/windows/iot/iot-enterprise/commercialization/licensing) or contact an authorized [Windows IoT Distributor](https://aka.ms/IoTDistributorList) for further assistance.

Windows IoT Enterprise LTSC releases follow the [Fixed Lifecycle Policy](/lifecycle/policies/fixed).

| Release                             | Version | Availability | End of Servicing | Update History | Update Catalog |
| ----------------------------------- | ------- | ------------ | ---------------- | -------------- | -------------- |
| Windows&nbsp;11&nbsp;IoT&nbsp;Enterprise&nbsp;LTSC&nbsp;2024 | TBD   | TBD | TBD | TBD | TBD |
| Windows&nbsp;10&nbsp;IoT&nbsp;Enterprise&nbsp;LTSC&nbsp;2021 | 19044   | 2021/11/16 | 2032/01/13 | [LTSC&nbsp;2021(21H2) update&nbsp;history](https://support.microsoft.com/help/5008339)  | [Updates&nbsp;for&nbsp;x64](https://www.catalog.update.microsoft.com/Search.aspx?q=Cumulative%20Update%20for%20Windows%2010%20Version%2021H2%20for%20x64) [Updates&nbsp;for&nbsp;Arm64](https://www.catalog.update.microsoft.com/Search.aspx?q=Cumulative%20Update%20for%20Windows%2010%20Version%2021H2%20for%20Arm64) |
| Windows&nbsp;10&nbsp;IoT&nbsp;Enterprise&nbsp;LTSC&nbsp;2019 | 17763   | 2018/11/13 | 2029/01/09 | [LTSC&nbsp;2019(1809) update&nbsp;history](https://support.microsoft.com/help/4464619)   | [Updates&nbsp;for&nbsp;x64](https://www.catalog.update.microsoft.com/Search.aspx?q=Cumulative%20Update%20for%20Windows%2010%20Version%201809%20for%20x64) [Updates&nbsp;for&nbsp;Arm64](https://www.catalog.update.microsoft.com/Search.aspx?q=Cumulative%20Update%20for%20Windows%2010%20Version%201809%20for%20Arm64) |
| Windows&nbsp;10&nbsp;IoT&nbsp;Enterprise&nbsp;LTSC&nbsp;2016 | 14393   | 2016/08/02 | 2026/10/13 | [LTSC&nbsp;2016(1607) update&nbsp;history](https://support.microsoft.com/help/4000825)  | [Updates&nbsp;for&nbsp;x64](https://www.catalog.update.microsoft.com/Search.aspx?q=Cumulative%20Update%20for%20Windows%2010%20Version%201607%20for%20x64)  [Updates&nbsp;for&nbsp;x86](https://www.catalog.update.microsoft.com/Search.aspx?q=Cumulative%20Update%20for%20Windows%2010%20Version%201607%20for%20x86) |
| Windows&nbsp;10&nbsp;IoT&nbsp;Enterprise&nbsp;LTSC&nbsp;2015 | 10240   | 2015/07/29 | 2025/10/14 | [LTSC&nbsp;2015(1507) update&nbsp;history](https://support.microsoft.com/help/4000823)  | [Updates&nbsp;for&nbsp;x64](https://www.catalog.update.microsoft.com/Search.aspx?q=Cumulative%20Update%20for%20Windows%2010%20Version%201507%20for%20x64)  [Updates&nbsp;for&nbsp;x86](https://www.catalog.update.microsoft.com/Search.aspx?q=Cumulative%20Update%20for%20Windows%2010%20Version%201507%20for%20x86) |

For more information, see [Windows IoT Enterprise LTSC support lifecycle](/lifecycle/products/?terms=Windows%20IoT%20Enterprise%20LTS).

## Considerations

The LTSC is designed for devices and use cases where features and functionality don't change. It provides 10-years of security servicing to a static feature set. As part of this offering

| Area | Description |
| --- | --- |
| **Silicon support** | Windows IoT Enterprise LTSC is supported for security, reliability, and compatibility on the latest silicon available at the time of release.  Previous silicon generations may still in support by the Silicon Vendor (SV) or Original Equipment Manufacturer (OEM). </br></br>When you utilize the LTSC, you must factor hardware into your decision, making sure you have a long-term supply of components for the expected life of your devices. If the hardware your device is using needs to be replaced in five years, do you have a replacement supply to support the version you're running?</br></br>For more information, see [Windows IoT Enterprise processor list](/windows/iot/iot-enterprise/hardware/hardware_requirements#processor) |
| **API support** | Windows IoT Enterprise LTSC is designed to support the latest application APIs and driver interfaces available at the time of release.  These interfaces don't change during the life-cycle of the LTSC. Access to updated interfaces requires updating to a successor release that contains the updated interfaces. |
| **Best security** | Windows IoT Enterprise LTSC, with the latest cumulative update distributed monthly installed, provides the most secure environment for the most demanding industrial devices. |
| **Best stability** | Windows IoT Enterprise LTSC, with the latest cumulative update distributed monthly installed, has the latest performance and stability improvements. |
| **Greatest hardware choice** | New devices target and ship with the latest Windows release to light up new hardware capabilities and improvements. |
