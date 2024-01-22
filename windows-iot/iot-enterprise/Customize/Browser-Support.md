---
title: Browser Support
author: TerryWarwick
ms.author: twarwick
ms.date: 03/30/2023
ms.topic: article
ms.service: windows-iot
ms.subservice: iot
description: Learn about browser support in Kiosk Mode
keywords: Lockdown, Kiosks, Kiosk Mode, Browser
---

# Browser Support

Today, you can use two browsers, Internet Explorer 11 and [Microsoft Edge](/deployedge/microsoft-edge-configure-kiosk-mode) to create an assigned access single-app or multi-app kiosk experience.

## Microsoft Edge Kiosk Mode

> Available for LTSC starting in [Windows 10 IoT Enterprise 2021 LTSC](/windows/iot/iot-enterprise/whats-new/Windows-10-IoT-Enterprise-LTSC-2021)

[Microsoft Edge kiosk mode](/deployedge/microsoft-edge-configure-kiosk-mode) offers two lockdown experiences of the browser so organizations can create, manage, and provide the best experience for their customers. The following lockdown experiences are available:

* Digital/Interactive Signage experience - Displays a specific site in full-screen mode.
* Public-Browsing experience - Runs a limited multi-tab version of Microsoft Edge.

Both experiences are running a Microsoft Edge InPrivate session, which protects user data.

## Internet Explorer 11

[Internet Explorer 11](/internet-explorer/internet-explorer) will be considered a legacy browser, in subsequent releases.

In anticipation of that, you can use [Internet Explorer (IE) mode](/deployedge/edge-ie-mode) on Microsoft Edge. IE mode allows you to run legacy web apps as well as modern web apps in a single browser.

> [!NOTE]
> For in-support Windows 10 IoT Enterprise [Semi-Annual Channel (SAC) releases](/lifecycle/products/windows-10-iot-enterprise), Internet Explorer 11 will reach end of support on June 15, 2022.
>
> Internet Explorer 11 follows the Long-Term-Servicing-Channel (LTSC) Lifecycle for [Windows 10 IoT Enterprise LTSC](/lifecycle/products/?terms=Windows%2010%20IoT%20Enterprise%20LTSC) products.

## Supported Versions

| Browser | ![Internet Explorer 11](./media/IE11.png) | ![Microsoft Edge Legacy](./media/Microsoft-Edge-Legacy.png) | ![New Microsoft Edge](./media/Microsoft-Edge-New.png) |
|--|--|--|--|
| OS Release | [IE11 App](/internet-explorer/internet-explorer) | [Edge Browser - Legacy](/deployedge/microsoft-edge-kiosk-mode-transition-plan) | [New Edge Browser](/deployedge/microsoft-edge-configure-kiosk-mode) |
| Windows 10 IoT Enterprise LTSC 2019 | [Follows OS Release Support Lifecycle](/lifecycle/products/windows-10-iot-enterprise-ltsc-2019) | No browser security updates after March, 9, 2021 (removed where applicable). In-box engine supported until OS EOL | Edge and WebView2 Runtime not in-box (requires app migration from EdgeHTML) |
| Windows 10 IoT Enterprise, version 21H2 | End of support June 15, 2022 | Removed & replaced with New Edge Browser in May 2021 Update | Included in-box or installed with May 2021 Update |
| Windows 10 IoT Enterprise LTSC 2021 | [Follows OS Release Support Lifecycle](/lifecycle/products/windows-10-iot-enterprise-ltsc-2021) | Not included | Microsoft Edge included in-box and follows [Modern Lifecycle Policy](/lifecycle/policies/modern) |
| Windows 11 IoT Enterprise | N/A | N/A | Microsoft Edge included in-box and follows [Modern Lifecycle Policy](/lifecycle/policies/modern) |

## Additional Resources

* [Configure Microsoft Edge kiosk mode](/deployedge/microsoft-edge-configure-kiosk-mode)
* [Plan your kiosk mode transition](/deployedge/microsoft-edge-kiosk-mode-transition-plan)
