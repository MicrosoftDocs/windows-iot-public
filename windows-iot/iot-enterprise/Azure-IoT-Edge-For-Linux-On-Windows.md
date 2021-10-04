---
title: Azure IoT Edge for Linux on Windows
author: fcabrera
ms.author: fcabrera
ms.date: 10/05/2021
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Learn how to integrate Azure IoT Edge for Linux on Windows with your Windows IoT Enterprise solution.
keywords: IoT Enterprise, Linux, Device Builders, Appliance, EFLOW, Azure IoT Edge
---

# Azure IoT Edge for Linux on Windows (EFLOW)


[Azure IoT Edge for Linux on Windows](/azure/iot-edge/iot-edge-for-linux-on-windows?view=iotedge-2018-06&preserve-view=true) allows you to run containerized Linux workloads alongside Windows applications in Windows IoT deployments. Businesses that rely on Windows IoT to power their edge devices can now take advantage of the cloud-native analytics solutions being built in Linux.

IoT Edge for Linux on Windows works by running a Linux virtual machine on a Windows device. The Linux virtual machine comes pre-installed with the IoT Edge runtime. Any IoT Edge modules deployed to the device run inside the virtual machine. Meanwhile, Windows applications running on the Windows host device can communicate with the modules running in the Linux virtual machine.

![Windows and the Linux VM run in parallel, while the Windows Admin Center controls both components](./media/EFLOW.png)

Bi-directional communication between Windows process and the Linux virtual machine means that Windows processes can provide user interfaces or hardware proxies for workloads run in the Linux containers.

[Get started](/azure/iot-edge/how-to-install-iot-edge-on-windows) today.


## Benefits
You might choose to build a device that includes Azure IoT Edge for Linux on Windows (EFLOW) as it comes with many benefits.

EFLOW enables customers for the first time to run production Linux-based cloud-native workloads on Windows IoT. Customers retain their existing Windows IoT assets plus benefit from the power of Windows IoT for applications that require an interactive UX and high-performance hardware interaction. There is no longer a need to choose between Windows or Linux; customers can now leverage the best of both platforms.

EFLOW provides the ability to deploy Linux IoT Edge modules onto a Windows IoT device. This opens a world of capabilities for commercial IoT as well as AI/ML with the availability of pre-built modules from the Azure Marketplace such as Live Video Analytics, SQL Edge, and OPC Publisher as a few examples.

As a developer, you may also choose to implement your own custom modules using the Linux distribution of your choice to address specific business requirements. Running Linux modules on Windows IoT becomes a seamless part of your solution.

In addition, Windows applications can easily interact with Linux modules running on the same physical device. A Windows process that provides UI or accesses cameras, sensors, or other hardware can seamlessly communicate with business logic or ML inferencing provided by a Linux module.

## Additional Resources
* [EFLOW Documentation](/azure/iot-edge/iot-edge-for-linux-on-windows?view=iotedge-2018-06&preserve-view=true)
* [IoT Show: Run Linux based IoT Edge modules on Windows IoT](https://www.youtube.com/watch?v=UB2yigjg5V8)
* [Get started](/azure/iot-edge/how-to-install-iot-edge-on-windows) today.
