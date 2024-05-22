---
title: Developing an Application for Real-Time Performance
author: TerryWarwick
ms.author: twarwick
ms.date: 03/30/2023
ms.topic: article
ms.service: windows-iot
ms.subservice: iot
description: Soft Real-Time Application on Windows 10 IoT Enterprise
keywords: IoT Enterprise, Soft Real-Time
---

# Developing a Soft Real-Time Application

Once a device is configured for real-time performance, an application can be set to run in real-time using standard Win32 APIs. The only factors that will give a thread or process real-time performance are the thread/process priority rank and the CPU core affinity.

To get real-time performance on a particular thread or process, its priority should be in the range of real-time performance and its affinity should be set to run on the real-time cores.

## Configure a Process for Real-Time

1. Use the [SetPriorityClass Function](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setpriorityclass) to: Set the process’ ProcessPriorityClass attribute to ```REALTIME_PRIORITY_CLASS```.
2. Use the [SetProcessAffinityMask Function](/windows/win32/api/winbase/nf-winbase-setprocessaffinitymask) to set the process to run exclusively on the cores which are reserved for the real-time application

## Configure a Thread for Real-Time

1. Use the [NtSetInformationThread function](/windows-hardware/drivers/ddi/ntifs/nf-ntifs-ntsetinformationthread) to set the thread’s ThreadBasePriority to a value between 16 and 31
2. Use the [SetThreadAffinityMask function](/windows/win32/api/winbase/nf-winbase-setthreadaffinitymask) to set the thread to run exclusively on the cores which are reserved for the real-time application
