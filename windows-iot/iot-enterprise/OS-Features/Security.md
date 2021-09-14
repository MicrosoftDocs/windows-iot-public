---
title: Security
author: rsameser
ms.author: riameser
ms.date: 3/12/2021
ms.topic: article
ms.prod: windows-iot
ms.technology: iot
description: Learn about the Security features of Windows 10 IoT Enterprise.
keywords: IoT Enterprise, Security
---

# Security
Windows 10 IoT Enterprise comes with a host of [security offerings](https://docs.microsoft.com/windows/whats-new/ltsc/whats-new-windows-10-2019#security) that you can leverage to best fit your Windows 10 IoT Enterprise solution.

## Microsoft Security Response Center
The world is more connected today than it has ever been. Technology is wound deep into our lives and has become part of our routine. With great advances, we have also seen a greater dynamic playing out between threat actors and the defenders. The [Microsoft Security Response Center (MSRC)](https://www.microsoft.com/msrc?rtc=1) is part of the defender community and on the front line of security response evolution. For over twenty years MSRC has been working to improve security for our customers, learning from both successes and failures. Time has only reasserted MSRC's commitment to better protect customers and the broader ecosystem.

MSRC's mission is to protect customers from being harmed by security vulnerabilities in Microsoft's products and services. By building your solution with Windows 10 IoT Enterprise, you have Microsoft Security Response Center's commitment towards security. Please review their [Security Update Guide](https://msrc.microsoft.com/update-guide/) to ensure your devices are up-to-date and secured.

## Comprehensive Security Features
Windows 10 IoT Enterprise, brings Enterprise security to your IoT devices.

Windows 10 IoT Enterprise is built on a five-point comprehensive security platform:
1. [Device protection](#1-device-protection)
2. [Threat Resistance](#2-threat-resistance)
3. [Data Protection in Motion](#3-data-protection-in-motion)
4. [Cloud Security](#4-cloud-security)
5. [Response](#5-response)

## 1. Device Protection
Windows Security provides the following built-in security options to help protect your device from malicious software attacks. Like they say, a strong defense, is a strong offense.

##### Trusted Platform Module (TPM)​
[Trusted Platform Module (TPM)](https://docs.microsoft.com/windows/security/information-protection/tpm/trusted-platform-module-top-node) technology is designed to provide hardware-based, security-related functions. A TPM chip is a secure crypto-processor that is designed to carry out cryptographic operations. The chip includes multiple physical security mechanisms to make it tamper resistant, and malicious software is unable to tamper with the security functions of the TPM. Some of the key advantages of using TPM technology are that you can:
* Generate, store, and limit the use of cryptographic keys.
* Use TPM technology for platform device authentication by using the TPM’s unique RSA key, which is burned into itself.
* Help ensure platform integrity by taking and storing security measurements.

##### Windows Device Health Attestation​
Modern malware is getting more and more sophisticated. Some of them, specifically bootkits, are capable of starting before Windows. [Device Health Attestation](https://docs.microsoft.com/windows/security/threat-protection/protect-high-value-assets-by-controlling-the-health-of-windows-10-based-devices#device-health-attestation) can be used to detect and remediate in the unlikely event where a device is infected. The device's firmware logs the boot process, and [Windows](https://docs.microsoft.com/windows-server/security/device-health-attestation) can send it to a trusted Health Attestation Server that can objectively assess the device's health.

##### Secure Boot​
[Secure boot](https://docs.microsoft.com/windows-hardware/design/device-experiences/oem-secure-boot) is a security standard developed by members of the PC industry to help make sure that a device boots using only software that is trusted by the Original Equipment Manufacturer (OEM). When the PC starts, the firmware checks the signature of each piece of boot software, including UEFI firmware drivers (also known as Option ROMs), and the operating system. If the signatures are valid, the PC boots, and the firmware gives control to the operating system.

The OEM can use instructions from the firmware manufacturer to create Secure boot keys and to store them in the PC firmware. When you add UEFI drivers, you'll also need to make sure these are signed and included in the Secure Boot database.

For information on how the secure boot process works included Trusted Boot and Measured Boot, see [Secure the Windows 10 boot process](https://docs.microsoft.com/windows/security/information-protection/secure-the-windows-10-boot-process).

##### BitLocker​
Wherever confidential data is stored, it must be protected against unauthorized access. Windows has a long history of providing at-rest data-protection solutions that guard against nefarious attackers, beginning with the Encrypting File System in the Windows 2000 operating system. More recently, [BitLocker](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-device-encryption-overview-windows-10) has provided encryption for full drives and portable drives. Windows consistently improves data protection by improving existing options and by providing new strategies. To learn more, see [BitLocker Overview and Requirements FAQ](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview-and-requirements-faq)


## 2. Threat Resistance
We provide a security tools set for Windows to protect a wide range of threats against execution of unauthorized code and scripts, network, and malware attacks. Effectively identifying, assessing, and remediating endpoint weaknesses is pivotal in running a healthy security program and reducing organizational risk. Threat and vulnerability management serves as an infrastructure for reducing organizational exposure, hardening endpoint surface area, and increasing organizational resilience.

##### Windows Defender Firewall
[Windows Defender Firewall](https://docs.microsoft.com/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security) is a stateful host firewall that helps secure the device by allowing you to create rules that determine which network traffic is permitted to enter the device from the network and which network traffic the device is allowed to send to the network. Windows Defender Firewall also supports Internet Protocol security (IPsec), which you can use to require authentication from any device that is attempting to communicate with your device. When authentication is required, devices that cannot be authenticated as a trusted device cannot communicate with your device. You can also use IPsec to require that certain network traffic is encrypted to prevent it from being read by network packet analyzers that could be attached to the network by a malicious user.

* [Deployment Guide](https://docs.microsoft.com/windows/security/threat-protection/windows-firewall/windows-firewall-with-advanced-security-deployment-guide)
* [Best Practices](https://docs.microsoft.com/windows/security/threat-protection/windows-firewall/best-practices-configuring)

##### Windows Defender
[Microsoft Defender for Endpoint](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) is a unified platform for preventative protection, post-breach detection, automated investigation, and response. Defender for Endpoint protects endpoints from cyber threats, detects advanced attacks and data breaches, automates security incidents, and improves security posture.

## 3. Data Protection in Motion
Data Protection covers control of data protection at rest, in transit, and via authorized access mechanisms. This includes discover, classify, protect, and monitor sensitive data assets using access control, encryption, and logging.

##### X.509/TLS-Based Handshake and Encryption
Transport Layer Security (TLS), like Secure Sockets Layer (SSL), is an encryption protocol intended to keep data secure when being transferred over a network. [These articles](https://docs.microsoft.com/mem/configmgr/core/plan-design/security/enable-tls-1-2) describe steps required to ensure that Configuration Manager secure communication uses the TLS 1.2 protocol.


## 4. Cloud Security
Microsoft Azure includes tools to safeguard data according to your company's security and compliance needs.

To learn more, visit [Azure Security](https://azure.microsoft.com/overview/security/)


## 5. Response
Microsoft has all the tooling to provide immediate support and assistance.  

##### Device Management
Microsoft provides a whole suite of [device management](../Device-Management/Device-Management-Overview.md) solutions to keep your devices safe and monitor activity at all times. Managing a device is now easier than ever on Windows 10 IoT Enterprise. There are multiple options that your organization can choose from in order to best manage your devices, such as Microsoft Intune, Endpoint Manager and third-party OMA-DM based management tools. OEMs can also select [Azure Device Agent](https://docs.microsoft.com/windows/iot-core/manage-your-device/azureiotda), which leaves it up to their customers to select the device management solution that fits them best.

* [Use Intune to remediate vulnerabilities identified by Microsoft Defender ATP](https://docs.microsoft.com/mem/intune/protect/atp-manage-vulnerabilities)

##### Device Recovery
In case something is to go wrong with your device, Windows 10 IoT Enterprise supports two device recovery options:

**Option #1:** Isolate the device using device management tools or network settings

**Option #2:** Reimage the device back to factory settings.

*[Windows IoT Device Health Attestation](#windows-device-health-attestation) enables the operator to assess if a device is booted to a trusted and compliant state, and takes appropriate remedial actions if necessary.*


## Additional resources
* [Azure Security Center](https://azure.microsoft.com/services/security-center/)
* [Azure Security Benchmark](https://docs.microsoft.com/azure/security/benchmarks/overview)
