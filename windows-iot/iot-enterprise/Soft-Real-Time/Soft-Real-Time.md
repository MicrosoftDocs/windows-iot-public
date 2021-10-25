---
title: Soft Real-Time
author: rsameser
ms.author: riameser
ms.date: 10/26/2021
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Soft Real-Time on Windows 10 IoT Enterprise
keywords: IoT Enterprise, Soft Real-Time
---

# Soft Real-Time on Windows IoT Enterprise
Windows 10 soft real-time is a new feature with [Windows 10 IoT Enterprise, version 21H2](/windows/iot/product-family/what's-new-in-windows-10-iot-enterprise-21h2) that allows device makers to introduce soft real-time capabilities on their devices.

This real-time behavior is introduced through 4 key settings:

1. **CPU isolation**: migrates the system-level disturbances off of the isolated CPUs, reducing potential jitter to the user's real-time application

2. **Custom ISR/DPC pinning on isolated CPUs**: All hardware interrupts are routed to the system and non-real-time cores but by writing a Custom ISR/DPC driver you can route your device specific interrupts to the real-time cores.

3. **Priority inheritance for mutexes**: This setting ensures the highest priority thread is executed, even in complex multi-threaded scenarios.

4. **Up to 16 RT thread priority levels**: This allows the programmer to divvy up resources among real-time tasks to ensure the most important ones get executed first.

## What is a Real-Time Operating System?
When running a program, a normal operating system gives deterministic results but allows for a nondeterministic time to complete a task. In a real-time operating system both the results of program execution and the time taken to get those results are (at least partially) deterministic.

### Hard Real-Time vs. Soft Real-Time
A hard real-time operating system is one where the time taken is deterministic to an exact moment. These operating systems are deployed in use cases where failure to get results on time represents a total system failure. Examples include microcontrollers within a car engine or airplane, printers, laser cutters, etc. Azure Real-Time OS is an example of such an OS.

A soft real-time operating system is one where there is a small window of time for program completion rather than a precise moment due to a bit of jitter from the operating system. Soft real-time systems, though less precise, can be run on multiple cores and impose fewer restrictions on applications. This is the type of real-time performance that you can expect from Windows 10 IoT Enterprise after using this guide.

### When do I need Real-Time Performance?
Real-time performance is not necessarily faster performance. It is just predictable performance. If you want better overall system performance – soft real-time might not be your best route to achieving it. However, if you have a real-world constraint (such as a calculation that must be performed before a robot’s environment changes or a motor that must be activated before a conveyor belt moves along) then soft real-time might be what you need.

Soft real-time should not be used in control loops where individual devices cannot operate without input from the soft RT machines. Such command-and-control loops will need to use a hard real-time device. Soft real-time is most useful in a State Machine Trigger device, where devices operate on independent microcontrollers until the soft real-time machine provides an input to change their behavior.

![Soft Real-Time Use Cases](./media/Real-Time.png)

Next: [How to set up a Device for Real-Time Performance](/windows/iot/iot-enterprise/soft-real-time/soft-real-time-device?branch=pr-en-us-29)
