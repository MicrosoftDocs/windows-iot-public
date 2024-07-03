---
title: "Quickstart: Prepare your lab environment"
description: "Get your technician PC ready to start building Windows IoT Enterprise images and prepare the reference device sample"
author: asergaz
ms.author: sergaz
ms.service: windows-iot
ms.subservice: iot
ms.topic: quickstart
ms.date: 06/28/2024

#customer intent: As a beginner, I want to know how to prepare my environment to build Windows IoT Enterprise images.

---

# Quickstart: Prepare your lab environment

In this quickstart, we walk you through preparing the technician PC to then install a basic Windows IoT Enterprise image onto a reference device sample. At the end of this quickstart, you have a technician PC ready to start building Windows IoT Enterprise images, and a reference device sample with Windows IoT Enterprise installed.

The following quicsktarts in this series build on this one to customize the device in audit mode and then sysprep and capture the reference device image. Alternatively you can use the lab environment prepared in this quickstart to follow other tutorials under [Customization](../Customize/customize-overview.md), [Optimization](../Optimize/Overview.md) and [Deployment](../Deployment/index.md).

> [!TIP]
> This series of quickstarts is intended to help you get started with Windows IoT Enterprise as quickly as possible, and that is why we provide you steps to test it in a Virtual Machine. In a true development or production environment, you would start by choosing a **physical hardware** design that meets the [Windows Hardware requirements](/windows-hardware/design/minimum/minimum-hardware-requirements-overview). You would then build base images for this design and test it. Next, you would modify the base images to create designs for different audiences, including branding, logos, languages, and apps.

## Prerequisites

To prepare your **technician PC (your work PC)**, you need:

- Have at least 15 GB of free space for installing the software and for modifying Windows IoT Enterprise images. We recommend using Windows 11 with the latest updates.
- Have [Windows ADK](/windows-hardware/get-started/adk-install) with Deployment Tools, Configuration Designer, and the Windows PE add-on installed.
- Have a Windows 11 IoT Enterprise LTSC 2024 ISO.
    [!INCLUDE [Latest LTSC](../../includes/incl-latest-ltsc-release.md)]
- Have the [Languages and Optional Features ISO](/windows-hardware/manufacture/desktop/languages-overview?view=windows-11&preserve-view=true). If you can't download the ISO we will provide you the alternative steps to customize the device using network connection.

<!-- Required: Prerequisites - H2

"Prerequisites" must be the first H2 in the article.

List any items that are needed for the quickstart,
such as permissions or software.

If the user needs to sign in to a portal to do
the quickstart, provide instructions and a link.

If there aren't any prerequisites, in a new paragraph
under the "Prerequisites" H2, enter "None" in plain text
(not as a bulleted list item).

-->

## Open [Cloud Shell, Azure CLI, or PowerShell]

<!-- Optional: Open a demo environment - H2

If you want to refer to using Azure Cloud Shell,
the Azure CLI, or Azure PowerShell, place the
instructions after the "Prerequisites" section.

Include Cloud Shell only if all commands can 
run in Cloud Shell.

Use include files if they are available.

--->

## [verb] * [noun]

[Introduce a task and its role in completing the process.]

<!-- Required: Tasks to complete in the process - H2

In one or more numbered H2 sections, describe tasks that 
the user completes in the process the quickstart describes.

-->

1. Procedure step
1. Procedure step
1. Procedure step

<!-- Required: Steps to complete the tasks - H2

Use ordered lists to describe how to complete tasks in 
the process. Be consistent when you describe how to
use a method or tool to complete the task.

Code requires specific formatting. Here are a few useful 
examples of commonly used code blocks. Make sure to 
use the interactive functionality when possible.

For the CLI-based or PowerShell-based procedures,
don't use bullets or numbering.

Here is an example of a code block for Java:

```java
cluster = Cluster.build(new File("src/site.yaml")).create();
...
client = cluster.connect();
```

Here's a code block for the Azure CLI:

```azurecli-interactive 
az vm create --resource-group myResourceGroup --name myVM 
--image win2016datacenter --admin-username azureuser 
--admin-password myPassword12
```

This is a code block for Azure PowerShell:

```azurepowershell-interactive
New-AzureRmContainerGroup -ResourceGroupName 
myResourceGroup -Name mycontainer 
-Image mcr.microsoft.com/windows/servercore/iis:nanoserver 
-OsType Windows -IpAddressType Public
```
-->

## Clean up resources

<!-- Optional: Steps to clean up resources - H2

Provide steps the user takes to clean up resources that
were created to complete the article.

-->

## Next step -or- Related content

> [!div class="nextstepaction"]
> [Next sequential article title](link.md)

-or-

- [Related article title](link.md)
- [Related article title](link.md)
- [Related article title](link.md)

<!-- Optional: Next step or Related content - H2

Consider adding one of these H2 sections (not both):

A "Next step" section that uses 1 link in a blue box 
to point to a next, consecutive article in a sequence.

-or- 

If the quickstart is not part of a sequence, use a 
"Related content" section that lists links to 
1 to 3 articles the user might find helpful.

-->

<!--

Remove all comments except the customer intent
before you sign off or merge to the main branch.

-->