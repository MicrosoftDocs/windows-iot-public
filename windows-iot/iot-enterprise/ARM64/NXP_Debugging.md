---
title: Kernel Debugging on NXP i.MX Evaluation Kits
author: anch-msft
ms.author: anthonychen
ms.date: 11/12/2024
ms.topic: how-to
ms.service: windows-iot
ms.subservice: iot
description: How to configure an NXP i.MX Evaluation Kit for kernel debugging
keywords: IoT Enterprise, Hardware, Windows IoT, Arm64, NXP
zone_pivot_groups: KDNet-KDCOM
---

# Kernel Debugging on NXP i.MX 8 and i.MX 9 Evaluation Kits

> [!NOTE]
> This article assumes familiarity with the concepts described in [Get started with Windows Debugging](/windows-hardware/drivers/debugger/getting-started-with-windows-debugging) and [Get started with WinDBG (kernel-mode)](/windows-hardware/drivers/debugger/getting-started-with-windbg--kernel-mode-)

## Introduction

Kernel debugging on NXP i.MX 8 and i.MX 9 Evaluation Kits (EVKs) enables you to debug kernel mode driver and OS issues such as blue screen crashes. NXP EVK boards support both network kernel debugging (KDNET) over the ethernet port and serial kernel debugging (KDCOM) over the micro-USB port.

::: zone pivot="kdnet"

## Set Up Network Kernel Debugging

Network kernel debugging uses the NXP EVK board's ethernet port to connect to the host computer. The NXP EVK board must be connected to the same network that your host computer is connected to.

In addition, NXP i.MX 8M Plus EVK boards must be connected using the ethernet port that is marked ENET1. NXP i.MX 93 EVK boards must be connected using the ethernet port that is marked ENET2.

### Obtain the KDNET extensibility module kd_8003_1fc9.dll

```kd_8003_1fc9.dll``` is the KDNET extensibility module for the ethernet network interface card on NXP i.MX EVK boards. Obtain ```kd_8003_1fc9.dll``` for the version of Windows installed on your NXP EVK board by reaching out to NXP. 

Once you have ```kd_8003_1fc9.dll```, copy it to the ```C:\windows\system32\``` folder on the NXP EVK board.

### Get the IP address of your host computer

On your host computer, open a Command Prompt or PowerShell window and use ```ipconfig``` to get the IP address.

```cmd
ipconfig
```

Make a note of either the IPv4 or IPv6 address of the network adapter connected to the network.

### Enable test signing on the NXP board

Open a Command Prompt or PowerShell window with Administrator privileges and enable test signing in the BCD.

```cmd
bcdedit /set testsigning on
```

### Enable network kernel debugging on the NXP board

First, enable kernel debugging on the NXP board in the BCD.

> [!NOTE]
> If Secure Boot is enabled, you will have to disable it to enable kernel debugging.

```cmd
bcdedit /debug on
```

Next, configure kernel debugging settings with the IP address of your host computer, a port number, and (optionally) a key. The recommended range of network ports to use for kernel debugging is 50000-50039.

<!--markdownlint-disable-next-line -->
# [IPv4 host address](#tab/IPv4)

```cmd
bcdedit /dbgsettings net hostip:w.x.y.z port:n key:a.b.c.d
```

<!--markdownlint-disable-next-line -->
# [IPv6 host address](#tab/IPv6)

```cmd
bcdedit /dbgsettings net hostipv6:s:t:u:v:w:x:y:z port:n key:a.b.c.d
```

---

Reboot the NXP board once you're finished for the BCD settings to take effect.

### Attach to the NXP EVK board with the network kernel debugger

Launch WinDBG on your host computer with the architecture that matches your host computer's architecture (either X64 or Arm64). When it launches, go to the File tab and select Attach to Kernel (ctrl + k). Then, select the Net tab, and enter the port number and key that was set in the BCD on the NXP EVK board. Reboot the NXP EVK board to have the kernel debugger attach.

::: zone-end

::: zone pivot="kdcom"

## Set Up Serial Kernel Debugging

> [!NOTE]
> Serial Kernel Debugging is only supported on the following NXP EVK boards:
>
> - NXP i.MX 8M Plus EVK
> - NXP i.MX 8M Quad EVK
> - NXP i.MX 8M Mini EVK
> - NXP i.MX 8M Nano EVK

On supported NXP EVK boards, a serial controller is exposed through the micro-USB port via an FTDI serial-to-USB chip. When the EVK board's micro-USB port is connected to your host computer, it appears on your host computer as a set of virtual COM ports.

### Install the FTDI virtual COM port driver on your host computer

On your host computer, download the FTDI virtual COM port driver from the [FTDI website](https://ftdichip.com/Drivers/vcp-drivers/) and install the driver.

The FTDI virtual COM port driver enables COM ports to be enumerated on your host computer when you connect it to the micro-USB port on the NXP EVK boards.

After installing the FTDI driver, connect your host computer to the NXP EVK board's micro-USB port. Open the Device Manager to verify that four new COM ports appear under the Ports device type.

### Determine which of the COM ports is active

Only one of the four virtual COM ports presented by the NXP EVK boards is active. Determine which one is active by connecting to each COM port using a serial terminal (for example, PuTTY) and observing the output while the NVK EVK board boots. Specify 921600 as the speed or baud rate when connecting to the COM port. Take a note of the COM port that prints logging data to the serial terminal during boot.

### Enable serial kernel debugging on the NXP board

First, enable kernel debugging on the NXP board in the BCD.

> [!NOTE] 
> If Secure Boot is enabled, you will have to disable it to enable kernel debugging.

```cmd
bcdedit /debug on
```

Next, configure kernel debugging settings for serial debugging with debugport set to 1 and baudrate set to 115200.

```cmd
bcdedit /dbgsettings serial debugport:1 baudrate:115200
```

Reboot the NXP board once you're finished for the BCD settings to take effect.

### Attach to the NXP EVK board with the serial kernel debugger

Launch WinDBG on your host computer with the architecture that matches your host computer's architecture (either X64 or Arm64). When it launches, go to the File tab and select Attach to Kernel (ctrl + k). Then, select the COM tab, and specify the port from earlier (for example, com5) and a baudrate of 921600. Reboot the NXP EVK board for the kernel debugger to attach.

::: zone-end