---
title: Start Prototyping
author: rsameser
ms.author: riameser
ms.date: 10/05/2021
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Learn how to prototype with Windows IoT Enterprise
keywords: IoT Enterprise, Prototype, Hardware, SoCs, Custom Boards, development devices, boards, SOC, SOM, system on chips, Windows IoT
---
# Start Prototyping
This guide will walk you through how to start prototyping with Windows IoT Enterprise.

## Step 1: Select Hardware
To begin your prototyping journey, you can select a SoC board or leverage your existing hardware to run Windows IoT Enterprise, as long as it meets the following [requirements](./Hardware_Requirements.md).

The following boards have been proven to be a great start point for your Windows IoT Enterprise solution. Feel free to choose a specific version based upon your budgetary constraints and technical requirements.

* [Latte Panda](https://www.lattepanda.com/)
* [Intel NuC](https://www.intel.com/content/www/us/en/products/boards-kits/nuc.html)
* [AAEON Up Squared](https://www.aaeon.com/en/p/iot-gateway-maker-boards-up-squared)
* [Up Board](https://up-board.org/up/specifications/)
* [NXP i.MX 8](https://www.nxp.com/products/processors-and-microcontrollers/arm-processors/i-mx-applications-processors/i-mx-8-processors/i-mx-8-family-arm-cortex-a53-cortex-a72-virtualization-vision-3d-graphics-4k-video:i.MX8)
* [NXP i.MX 8M](https://www.nxp.com/products/processors-and-microcontrollers/arm-processors/i-mx-applications-processors/i-mx-8-processors/i-mx-8m-family-armcortex-a53-cortex-m4-audio-voice-video:i.MX8M)
* [NXP i.MX 8M Mini](https://www.nxp.com/products/processors-and-microcontrollers/arm-processors/i-mx-applications-processors/i-mx-8-processors/i-mx-8m-mini-arm-cortex-a53-cortex-m4-audio-voice-video:i.MX8MMINI)
* [NXP i.MX 8M Nano](https://www.nxp.com/products/processors-and-microcontrollers/arm-processors/i-mx-applications-processors/i-mx-8-processors/i-mx-8m-nano-family-arm-cortex-a53-cortex-m7:i.MX8MNANO)
* [NXP i.MX 8M Plus](https://www.nxp.com/products/processors-and-microcontrollers/arm-processors/i-mx-applications-processors/i-mx-8-processors/i-mx-8m-plus-arm-cortex-a53-machine-learning-vision-multimedia-and-industrial-iot:IMX8MPLUS)

*If you are a SoM provider or an ODM and would like to be added to the list above, directly edit this page and submit a pull request or send an email to winiotentsomhelp@microsoft.com*

## Step 2: Evaluate Edition
To get started, you can try the [Windows 10 Enterprise 90 day Evaluation](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise). To select which edition of Windows IoT Enterprise you would like to work with, review [Features by Release](../Features.md).

## Step 3: Deploy an Image
If your board comes with instructions on how to deploy Windows IoT Enterprise, follow those instructions. Otherwise, you can follow the labs provided in the [Windows IoT Enterprise Manufacturing Guide](../Commercialization/Manufacturing-Guide.md).

> [!TIP] Try out [Edge Device Image Builder](https://aka.ms/EDIBPublicPreviewRelease) a tool currently in public preview that walks OEMs through customizing and configuring a Windows 10 IoT Enterprise LTSC 2021 image. Check out the [announcement blog](https://aka.ms/EDIBPublicPreviewBlog) and [documentation](https://aka.ms/EDIBDocumentation) for more information on how to get started. 

## Step 4: Load an Application
You can choose to port over any of your existing [Windows applications](/windows/apps/desktop/choose-your-platform) or feel free to reference any of our [UWP app samples](https://github.com/microsoft/Windows-universal-samples) in GitHub.

## Step 5: Licensing & Distribution
If you are interested in pursuing your prototype, past the 90-day evaluation period, reach out to a Windows IoT distributor. Microsoft offers many Windows IoT and Embedded SKUs, and authorized distributors of Windows IoT products can help you pick the right SKU for your hardware and your budget by leveraging their development experiences, and knowledge, to help you build secure and connected Windows IoT solutions. If you would like to work with one of our distributors, please [select a distributor](https://aka.ms/IoTDistributorList) in your region and contact the distributor directly for more details.

## Additional Resources
* [Windows IoT Enterprise Manufacturing Guide](/windows-hardware/manufacture/desktop/iot-ent-overview)
* [Windows Processor Requirements](/windows-hardware/design/minimum/windows-processor-requirements)
