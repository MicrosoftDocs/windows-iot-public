---
title: Hardware Platforms and Boards
author: anch-msft
ms.author: anthonychen
ms.date: 10/2/2024
ms.topic: article
ms.service: windows-iot
ms.subservice: iot
description: Learn about the available options of hardware platforms and boards for building Windows IoT devices
keywords: IoT Enterprise, Hardware, SoCs, Custom Boards, development devices, boards, SOC, SOM, system on chips, Windows IoT
zone_pivot_groups: x64-Arm64
---

# Hardware Platforms and Boards

## Selecting Hardware

To begin building a Windows IoT Enterprise solution, you need to select a hardware platform or board.

A full hardware platform houses all of the board-level components inside an enclosure and is commercial ready out-of-the-box. It's a good fit for application-level solutions builders that don't need high degrees of hardware customizability.

A hardware board includes only the board with exposed components, making it easier to make hardware configuration changes and debug hardware issues. It's a good fit for OEMs that have specific or bespoke hardware requirements for their product.

Other factors to consider when selecting hardware include performance, available memory, availability connectivity options, security, customizability, time to market, and cost. Decide which hardware works best for you based on your specific requirements.

## Recommended Hardware Platforms

:::zone pivot="x64"

| Manufacturer | Platform |
| ------ | -------------- |
| AAEON | [BOXER-6645U-RPL Compact Embedded Computer](https://www.aaeon.com/en/p/compact-fanless-box-6645u-rpl) |
| AAEON | [BOXER-6646-ADP Compact Embedded Computer](https://www.aaeon.com/en/p/compact-fanless-box-pc-solutions-boxer-6646-adp) |
| ADLINK | [MVP-6200 Expandable Modular Industrial Computer](https://www.adlinktech.com/Products/Industrial_PCs_Fanless_Embedded_PCs/ExpandableFanlessEmbeddedComputers/MVP-6200_Series?lang=en) |
| ADLINK | [MVP-5200 Compact Industrial Computer](https://www.adlinktech.com/Products/Industrial_PCs_Fanless_Embedded_PCs/IntegratedFanlessEmbeddedComputers/MVP-5200_Series?lang=en) |
| Advantech | [UNO-238 V2 IoT Edge Computer](https://www.advantech.com/en-us/products/9a0cc561-8fc2-4e22-969c-9df90a3952b5/uno-238-v2/mod_77575fa5-5252-41a8-9f0d-5ef789890faf) |
| ASRock | [Expandable Edge AIoT Platform](https://www.asrockind.com/en-gb/expandable-edge-aiot-platform) |
| ASRock | [Compact Edge AIoT Platform](https://www.asrockind.com/en-gb/compact-edge-aiot-platform) |
| ASUS | [IoT Embedded PCs and AI Systems](https://iot.asus.com/embedded-computers-edge-ai-systems/all-series/filter?Series=Fanless-Embedded-Computers,Embedded-Computers&Spec=86) |
| DFI | [EB100-MTU Industrial NUC](https://www.dfi.com/product/index/1681) |
| DFI | [X6-MTH-ORN AI Industrial System](https://www.dfi.com/product/index/1673) |
| iBase | [Ultra-Compact IoT Gateways](https://www.ibase.com.tw/en/product/category/Intelligent_System/Edge_Computing_Wide_Temperature_System) |
| IEI | [IDS-330-ADL-P Digital Signage System](https://www.ieiworld.com/en/product/model.php?II=942) |
| Kontron | [KBox Embedded Box PCs](https://www.kontron.com/en/products/energy/embedded-box-pc/c139294) |
| Seavo | [McLaren Island AIoT Developer Kit](https://www.seavo.com/en/products/products-info_itemid_561.html) |

::: zone-end

:::zone pivot="arm64"

| Manufacturer | Platform |
| ------ | -------------- |
| Advantech | [EPC-R3720 Edge Computer](https://www.advantech.com/en/products/880a61e5-3fed-41f3-bf53-8be2410c0f19/epc-r3720/mod_fde326be-b36e-4044-ba9a-28c4c49a25c6) |

::: zone-end

## Recommended Hardware Boards

:::zone pivot="x64"

| Manufacturer | Board | Type |
| ------ | -------------- | ----- |
| ADLINK | [Express-RLP](https://www.adlinktech.com/Products/Computer_on_Modules/COMExpressType6/Express-RLP?lang=en) | System on Module |
| Congatec | [conga-HPC/cRLP](https://www.congatec.com/en/products/com-hpc/conga-hpccrlp/) | System on Module |
| Congatec | [conga-HPC/cRLS](https://www.congatec.com/en/products/com-hpc/conga-hpccrls/) | System on Module |
| Congatec | [conga-TC700](https://www.congatec.com/en/products/com-express-type-6/conga-tc700/) | System on Module |
| Congatec | [conga-TC675](https://www.congatec.com/en/products/com-express-type-6/conga-tc675/) | System on Module |
| DFI | [MTH968](https://www.dfi.com/product/index/1652 )| System on Module |
| Portwell | [PCOM-B885](https://portwell.com/products/detail.php?CUSTCHAR1=PCOM-B885) | System on Module |
| ASRock | [NUC Boards](https://www.asrockind.com/en-gb/nuc) | Single Board Computer |
| DFI | [MTH253](https://www.dfi.com/product/index/1679) | Single Board Computer |
| iBASE | [Single Board Computers](https://www.ibase.com.tw/en/product/category/Embedded_Computing/Single_Board_Computer/x86_based_3_5_Single_Board_Computer) | Single Board Computer |

::: zone-end

:::zone pivot="arm64"

| Manufacturer | Board | Type |
| ------ | -------------- | ----- |
| Thundercomm | [ RB3 Gen 2](https://www.thundercomm.com/product/qualcomm-rb3-gen-2/) | Development Kit |
| NXP | [i.MX 8M Plus EVK](https://www.nxp.com/design/development-boards/i-mx-evaluation-and-development-boards/evaluation-kit-for-the-i-mx-8m-plus-applications-processor:8MPLUSLPD4-EVK) | Development Kit |
| NXP | [i.MX 93 EVK](https://www.nxp.com/products/processors-and-microcontrollers/arm-processors/i-mx-applications-processors/i-mx-9-processors/i-mx-93-applications-processor-family-arm-cortex-a55-ml-acceleration-power-efficient-mpu:i.MX93) | Development Kit |
| NXP | [i.MX 8M Mini EVK](https://www.nxp.com/design/development-boards/i-mx-evaluation-and-development-boards/evaluation-kit-for-the-i-mx-8m-mini-applications-processor:8MMINILPD4-EVK) | Development Kit |
| Avnet | [MSC SM2S IMX8PLUS](https://embedded.avnet.com/product/msc-sm2s-imx8plus/) | System on Module |
| Advantech | [ROM-5722](https://www.advantech.com/en/products/computer-on-module/rom-5722/mod_11aa0c77-868e-4014-8151-ac7a7a1c5c1b) | System on Module |
| SECO | [Trizeps VIII Plus](https://edge.seco.com/usa/trizeps-viii-plus.html) | System on Module |
| Advantech | [RSB-3720](https://www.advantech.com/en/products/single_board_computer/rsb-3720/mod_d2f1b0bc-650b-449a-8ef7-b65ce4f69949) | Single Board Computer |

::: zone-end

## More Resources

* [Windows IoT Enterprise Manufacturing Guide](../Commercialization/Manufacturing-Guide.md)
* [Windows IoT Enterprise Processor Requirements](./Processor_Requirements.md)
