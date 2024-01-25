---
title: Start Prototyping
author: TerryWarwick
ms.author: twarwick
ms.date: 10/20/2023
ms.topic: article
ms.service: windows-iot
ms.subservice: iot
description: Learn how to prototype with Windows IoT Enterprise
keywords: IoT Enterprise, Prototype, Hardware, SoCs, Custom Boards, development devices, boards, SOC, SOM, system on chips, Windows IoT
---
# Start Prototyping

This guide walks you through how to start prototyping with Windows IoT Enterprise.

## Step 1: Select Hardware

To begin your prototyping journey, you can select a SoC board or use your existing hardware to run Windows IoT Enterprise, as long as it meets the following [requirements](./Hardware_Requirements.md).

The following boards have been proven to be a great start point for your Windows IoT Enterprise solution. Feel free to choose a specific version based upon your budgetary constraints and technical requirements.

|Architecture|Recommended Boards|
|----|----|
|x64| [Latte Panda](https://www.lattepanda.com/)<br>[Intel NuC](https://www.intel.com/content/www/us/en/products/boards-kits/nuc.html)<br>[AAEON Up Squared](https://www.aaeon.com/en/p/iot-gateway-maker-boards-up-squared)<br>[Up Board](https://up-board.org/up/specifications/)|
|ARM64|[NXP i.MX 8 Family](https://www.nxp.com/products/processors-and-microcontrollers/arm-processors/i-mx-applications-processors/i-mx-8-applications-processors:IMX8-SERIES)<br>[NXP i.MX 93](https://www.nxp.com/products/processors-and-microcontrollers/arm-processors/i-mx-applications-processors/i-mx-9-processors/i-mx-93-applications-processor-family-arm-cortex-a55-ml-acceleration-power-efficient-mpu:i.MX93)|

>NOTE: *If you are a SoM provider or an ODM and would like to be added to our list of hardware for prototyping, directly edit this page and submit a pull request or send an email to winiotinquire@microsoft.com*

## Step 2: Evaluate Edition

To get started, you can try the [Windows 10 Enterprise 90 day Evaluation](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise). To select which edition of Windows IoT Enterprise you would like to work with, review [Features by Release](../Features.md).

## Step 3: Deploy an Image

If your board comes with instructions on how to deploy Windows IoT Enterprise, follow those instructions. Otherwise, you can follow the labs provided in the [Windows IoT Enterprise Manufacturing Guide](../Commercialization/Manufacturing-Guide.md).

## Step 4: Load an Application

You can choose to port over any of your existing [Windows applications](/windows/apps/desktop/choose-your-platform) or feel free to reference any of our [UWP app samples](https://github.com/microsoft/Windows-universal-samples) in GitHub.

## Step 5: Licensing & Distribution

If you're interested in pursuing your prototype, past the 90-day evaluation period, reach out to a Windows IoT distributor. Microsoft offers several Windows IoT products. Authorized distributors of Windows IoT products can help you choose the right product for your solution and help you build secure and connected Windows IoT solutions. If you would like to work with one of our distributors, please [select a distributor](https://aka.ms/IoTDistributorList) in your region and contact the distributor directly for more details.

## Other Resources

* [Windows IoT Enterprise Manufacturing Guide](../Commercialization/Manufacturing-Guide.md)
* [Windows Processor Requirements](/windows-hardware/design/minimum/windows-processor-requirements)
