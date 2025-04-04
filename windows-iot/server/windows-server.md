---
title: About Windows Server IoT
author: terrywarwick
ms.date: 11/04/2024
ms.author: twarwick
ms.topic: article
ms.service: windows-iot
ms.subservice: iot
description: Learn about what Windows Server IoT is and what you can do with it.
keywords: Windows Server IoT, enterprise manageability, Windows ecosystem, IoT
---

# About Windows Server IoT

## What is Windows Server IoT?

<!--
 Windows Server IoT is a full version of Windows Server that delivers enterprise manageability and security to IoT solutions. Windows Server IoT shares all the benefits of the world-wide Windows ecosystem. It is a binary equivalent to Windows Server, so you can use the same familiar development and management tools that you use on your general-purpose servers. However, when it comes to licensing and distribution, the general-purpose version and IoT versions differ.  Windows Server IoT is only licensed through the OEM channel under special dedicated use rights.
-->

Windows Server IoT is binary equivalent to Windows Server. This means you get the latest features, including:

- hybrid capabilities with Azure
- enterprise manageability
- faster innovation for apps (including support for modern container technologies managed by Azure IoT Edge)
- advanced multilayer security

Windows Server IoT is designed to support large scale compute, connections, or storage workloads where processing on the edge is required for latency, bandwidth, cost, data residency, or privacy requirements. And because it's the same as Windows Server, you can use the familiar development and management tools that you use with your general-purpose Windows Servers.

Windows Server IoT does however, follow different licensing and distribution policies than Windows Server. Windows Server IoT is licensed through the OEM channel under special dedicated use rights as determined by special licensing agreements. This different licensing program helps OEMs more effectively compete in price sensitive markets.

Fixed-function appliances using Windows Server IoT are dedicated to specific information or transaction processing, aggregating data from downstream "things" and analyzing it on-premises at scale; maintaining databases that are too large to transfer to the cloud; serving as a gateway to enterprise IT infrastructures; or using Azure in hybrid scenarios with cloud-native apps.

With Windows Server IoT, you can build dedicated. Server-class appliances that can:

- Analyze multiple video streams in surveillance and security monitoring systems
- Monitor the health of industrial automation equipment or perform defect detection on high-speed manufacturing lines
- Enable intelligent building scenarios like optimizing energy use or monitoring enterprise fire and life safety
- Support medical imaging technology such as picture archiving and communication systems (PACS) to provide economical storage and access to patient images
- Support audio and video communication solutions such as live media, entertainment workflows and streaming
- Provide heavy-duty network attached storage (NAS) functionality for storage and analytics
- Enable telecommunications scenarios such as Power Break (PB) switchboard systems, call centers, or Interactive Voice Response (IVR) automated telephony systems

Whatever the solution, Windows Server IoT provides a trusted and functionally stable platform that can protect, process, and aggregate large volumes of data either on-premises or in Azure.

Due to the specific, dedicated nature of appliances using Windows Server IoT, Microsoft has a software licensing model tailor-made for Windows Server IoT.

## Licensing

Dedicated-purpose devices are built to perform a predefined set of tasks. The OEM channel licenses Windows Server IoT with special dedicated use licensing terms. (Prior versions were referred to as Windows Server for Embedded Systems or Windows Storage Server.)

Microsoft’s exclusive licensing scheme for dedicated use server applications enables you to provide price competitive products and solutions. Furthermore, the redistribution rights let you customize and brand your own server appliances meeting your marketing and branding needs.

The special licensing model is referred to as Windows Server IoT because of the following two distinguishing features:

1. The application is an embedded system used as a special-purpose solution.

1. The Windows Server IoT Licenses are available through a worldwide network of [authorized distributors](../iot-enterprise/windows-iot-distributors.md)

For additional information about Windows Server IoT OEM licenses and terms of use, contact one of our [authorized distributors](../iot-enterprise/windows-iot-distributors.md) for assistance.

## License Qualifications

Because Windows embedded/IoT Server is a special licensing model for specialized applications, the following requirements must be met:

- The application is an embedded system used as a special-purpose solution by an industry and can't be uses as a substitute for a general-purpose computing device. The application can’t be used with other commercial applications such as accounting, messaging or enterprise email, enterprise resource planning software, web-based time management applications that address appointments, meetings or other calendaring items, Microsoft Exchange Server or Microsoft SharePoint Portal Server, team collaboration software, word processing, or CRM.
- The embedded application must be preinstalled with the operating system on the server and shipped with the hardware. An embedded application means an industry or task-specific software program and/or function that provides the primary functionality of the end customer system. An embedded application is designed to meet the functionality requirements of the specific industry into which the system is marketed and distributed.

> [!IMPORTANT]
> In the end, devices must not be designed for use as a substitute for a general-purpose computing device.
>
> The embedded software application must provide the primary function of the solution.

## Editions

Microsoft offers six Windows Server IoT editions, each intended for a specific purpose.

| Windows&nbsp;Server&nbsp;IoT&nbsp;Editions | Description |
|----------|-------------|
| Standard           | A dedicated server with Active Directory integration (file, print, networking services) or servers requiring a connected keyboard, monitor, or mouse to perform its dedicated purpose. |
| Datacenter         | A dedicated server with Active Directory integration (file, print, networking services) or servers requiring a connected keyboard, monitor, or mouse to perform its dedicated purpose. |
| Storage Standard   | A dedicated file server appropriate for Network Attached Storage, Storage Area Network Gateway, or another storage solution.|
| Storage Workgroup  | A small storage solution (for 50 users or less) that does NOT require network infrastructure services (file, print, etc.) or a connected keyboard, monitor, or mouse|
| Telecommunications | A specialized telecommunications application such as PBX, IP PBX, Automated Attendant, Interactive Voice Response (IVR), or teleconferencing. |

## Releases

Windows Server IoT releases follow the [Fixed Lifecycle Policy](/lifecycle/policies/fixed).

| Release                             | Version | Availability | End of Servicing |
| ----------------------------------- | ----- | ------------ | ---------------- |
| [Windows Server IoT 2025](/lifecycle/products/windows-server-2025) | 26100 | 2024-11-01   | 2034-10-10       |
| [Windows Server IoT 2022](/lifecycle/products/windows-server-iot-2022) | 20348 | 2021-08-18   | 2031-10-14       |
| [Windows Server IoT 2019](/lifecycle/products/windows-server-iot-2019) | 17763 | 2019-03-04   | 2029-01-09       |

<!--
## Fixed purpose devices

> [!TIP]
> See your licensing agreement for complete guidance on all Windows Server IoT usage scenarios. If you do not have this licensing agreement, ask the OEM you work with for the commercial agreement.

Windows Server is well known as the server operating system used by small businesses and enterprises world-wide. What is less well known is that for years, Windows Server has also powered many dedicated solutions in retail, manufacturing, healthcare, and more. Windows Server IoT allows you to build fixed purpose solutions with specific allowances and restrictions in the license agreement.

## Long-term Servicing Channel (LTSC)

This is the release model you’re already familiar with, formerly called the "Long-Term Servicing Branch", where a new major version of Windows Server is released every two to three years. Users are entitled to five years of mainstream support and five years of extended support. This channel is appropriate for systems that require a longer servicing option and functional stability. Deployments of Windows Server IoT 2022 and earlier versions of Windows Server won't be affected by the new Semi-Annual Channel releases. 

* [Learn more about LTSC](/windows-server/get-started-19/servicing-channels-19#long-term-servicing-channel-ltsc)
-->
## Related Information

* [Windows Server documentation](/windows-server/index)
* [Windows Server IoT 2022 - Generally Available](https://techcommunity.microsoft.com/t5/internet-of-things/windows-server-iot-2022-now-generally-available/ba-p/2703521)
