---
description: Get the tools you need to create an IoT Enterprise image
title: Get the tools you need to customize Windows IoT Enterprise
ms.date: 12/10/2018
ms.topic: article
author: TerryWarwick
ms.author: twarwick
ms.service: windows-iot
ms.subservice: iot

---

# Get the tools needed to customize Windows IoT Enterprise

## Windows IoT Enterprise

Windows IoT Enterprise is a full version of Windows that delivers enterprise manageability and security to IoT solutions. Windows IoT Enterprise shares all the benefits of the worldwide Windows ecosystem. It's a binary equivalent to Windows Enterprise, so you can use the same familiar development and management tools as client PCs and laptops. However, when it comes to licensing and distribution, the desktop version and IoT versions differ. Windows IoT Enterprise offers both LTSC and SAC options, and OEMs can choose the one they need for their devices.

## Getting started with Windows IoT Enterprise

Before reaching out to an Embedded/IoT Distributor, we recommend working with a device that meets the [Windows Hardware requirements](/windows-hardware/design/minimum/minimum-hardware-requirements-overview). You can load your PC or recommended device with an evaluation copy of Windows Enterprise in order to begin prototyping right away.  

In order to start your journey in manufacturing with Windows IoT Enterprise, you need to reach out to a distributor from [this list](https://query.prod.cms.rt.microsoft.com/cms/api/am/binary/RWCpaM).

## What you need to build IoT Enterprise images

You need the following tools to go through any of the labs in this section and create OEM images using the Windows IoT Enterprise Operating System.

## PCs and devices

Here's how we refer to them:

- Technician PC: Your work PC. This PC should have at least 15 GB of free space for installing the software and for modifying IoT Enterprise images. We recommend using either Windows or Windows 11 with the latest updates.

  - Configure the technician PC as follows:
    - [Windows ADK](/windows-hardware/get-started/adk-install) with Deployment Tools, Configuration Designer, and the Windows PE add-on installed
    - Windows IoT Enterprise 2019 LTSC OPK
    - Feature on Demand ISO
    - Language Pack ISO

- IoT device: A test device or board that represents all of the devices in a single model line. Depending on the device you need a keyboard, mouse and a monitor.
- A USB key that's at least 8 GB in size and that can have all information removed from it

## Next steps

Now you have what you need to build a custom image. Lab 1a shows how to get started.

>[!div class="nextstepaction"]
>[Go to lab 1a](iot-ent-create-a-basic-image.md)
