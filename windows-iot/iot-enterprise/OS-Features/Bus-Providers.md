---
title: Bus Providers
author: rsameser
ms.author: riameser
ms.date: 3/12/2021
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Learn about the different providers available through Windows 10 IoT Enterprise.
keywords: IoT Enterprise, Bus Providers
---

# Bus Providers
Windows has in-box UWP APIs that provide direct access to GPIO, SPI, or I2C busses. This gives very easy access to this hardware from a high-level API. However, there are many times when a device maker wants to use an off-SoC controller to access a bus. It can be as simple as a cheap chip that adds 16 GPIO pins, or as rich as a full MCU that not only adds GPIO, SPI, and I2C pins, but also supports PWM and ADC. With the "Bus Provider" model, we give developers the ability to access these off-SoC busses using the in-box APIs, using a user-mode provider that bridges the gap.

Someone building a provider implements a set of interfaces into a UWP class library and then any developer who wants to talk to that hardware simply includes the component and tells the in-box APIs about it. If you look at the sample code from the [remote provider](https://github.com/ms-iot/BusProviders/tree/develop/Arduino) you can see how easy it is to configure the provider, and once set as the default provider for that app, the rest of the code in the client app is identical to the code required to access an on-SoC bus.

```
Providers.Provider.Configuration =
    new Providers.ConnectionConfiguration("VID_2341", "PID_0043", 57600);
Windows.Devices.LowLevelDevicesController.DefaultProvider =  new Providers.Provider();

gpioController = await GpioController.GetDefaultAsync();
i2cController = await I2cController.GetDefaultAsync();
adcController = await AdcController.GetDefaultAsync();
pwmController = await PwmController.GetDefaultAsync();

GpioPin pin = gpioController.OpenPin(LED_PIN, GpioSharingMode.Exclusive);`
```

## Available Providers

We currently have a number of providers available on the [Bus Providers](https://github.com/ms-iot/BusProviders) GitHub repo. In addition to the code for the provider, each provider has a sample VS solution that demonstrates how a client would use that provider.

- **ADC**
  - Ads1x15
  - Mcp3008

- **PWM**
  - PCA9685
  - Simulated with Gpio

In addition to the providers that give you access to real hardware, we have built a [Simulated Provider](https://github.com/ms-iot/BusProviders/tree/develop/SimulatedProvider) that will act as if it was an infinitely capable provider and is designed to let you write and debug your applications without having to first deploy them to a working device. For a richer experience, you can customize it to simulate your actual hardware. *For example: updating the I2c provider to return back the result "75" when you send it the command for a temperature reading on a device with the designated secondary address.*

## Additional Resources

Additional bus tools, sample codes, and building and testing on I2C, SPI, GPIO, MinComm/UART can be found [here](https://github.com/Microsoft/Windows-iotcore-samples/tree/develop/BusTools).

Please reference [Windows Runtime (WinRT) APIs](https://docs.microsoft.com/uwp/api/?view=winrt-19041&preserve-view=true) and here's how to leverage the APIs from [Win32 applications](https://blogs.windows.com/windowsdeveloper/2017/01/25/calling-windows-10-apis-desktop-application/).   

Review [Windows Bus Providers](https://docs.microsoft.com/uwp/api/windows.devices.pwm.provider?view=winrt-19041&preserve-view=true)
