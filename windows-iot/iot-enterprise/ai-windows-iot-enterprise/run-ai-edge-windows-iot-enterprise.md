---
title: Run AI at the edge on Windows IoT Enterprise
description: Build local AI into purpose-built devices with a common Windows framework across supported AMD, Intel, Qualcomm, and NVIDIA hardware.
#customer intent: Build local AI into purpose-built devices with a common Windows framework across supported hardware.
ms.date: 11/12/2026
ms.topic: overview
ms.service: windows-iot
ms.subservice: iot
ms.collection: magic-ai-copilot
author: v-fvalentyna
ms.author: v-fvalentyna
ms.reviewer: v-fvalentyna
---

# Run AI at the edge on Windows IoT Enterprise

To add AI capabilities to edge IoT devices, start by choosing models that meet your application's needs and preparing them to run efficiently on your chosen hardware. As models evolve and hardware changes between production runs, each new pairing can require another round of integration and testing. Models come from your own training pipeline, open-source projects, a catalog, or Windows itself. The hardware can be a CPU, GPU, or NPU.

Microsoft builds SDKs and tools to reduce that integration work. [Windows ML](/windows/ai/new-windows-ml/overview), [Foundry Local](/azure/foundry-local/get-started), and [Windows AI APIs](/windows/ai/apis/) cover the range from bringing your own model to using one that Windows supplies. They provide access to hardware acceleration, with different levels of control and different hardware and deployment requirements.

This article explains how to choose among these options, prepare models and device images, and plan updates for a Windows IoT device. It also looks at emerging local and agentic capabilities, then closes with a self-checkout reference design you can use to get started.

## How Windows ML works across hardware

[Windows Machine Learning (Windows ML)](/windows/ai/new-windows-ml/overview) is a framework for running AI models locally in Windows applications.

For ONNX models, Windows ML lets your application use common inference APIs across supported hardware. Execution providers (EPs) handle hardware-specific execution. Windows ML helps your application discover compatible providers, acquire supported providers when needed, and select how to run the model on the available hardware.

Microsoft supports and maintains the copy of ONNX Runtime included with Windows ML. ONNX provides a common model format that many training tools can export, letting you use a model outside the framework you used for training.

CPUs support general-purpose execution, GPUs suit highly parallel workloads, and NPUs target efficient AI processing. Choose an execution provider and driver for your target hardware, then validate that your model runs correctly with that configuration.

The [Windows ML execution-provider catalog](/windows/ai/new-windows-ml/supported-execution-providers) lists providers and their hardware requirements. 

:::image type="content" source="media/run-ai-edge-windows-iot-enterprise/ai-on-iot-diagram.png" alt-text="Three integration options and the components behind them. The experimental Runtime and task-specific APIs are part of direct Windows ML, not a separate integration option." lightbox="media/run-ai-edge-windows-iot-enterprise/ai-on-iot-diagram.png":::

## Choose how to integrate AI

You have three main options for integrating local AI into a Windows IoT application. 

Your choice depends on the model you need, the control you need over how it runs, and your device's hardware and deployment requirements.

| Option for AI integration | Who provides the model | Best scenario |
|---|---|---|
| Direct Windows ML | You supply the model. | You need direct control over how your application loads and runs the model and selects execution providers. |
| Foundry Local | You choose a model from the Foundry Local catalog or supply a compatible custom model. | You want built-in model downloading, loading, and management, with higher-level APIs for inference. |
| Windows AI APIs | Windows supplies and services the model. Model installation requires eligible hardware; running a supported Windows version alone doesn't make the device eligible. | A Windows-provided capability meets your application's needs, without bringing and managing your own model. |

For details on each option, see the following sections.

### Direct Windows ML: Bring your own model

If you have a vision model trained to catch a particular defect on a production line, you can call [Windows ML](/windows/ai/new-windows-ml/overview) directly and deploy that model with your application. Your code supplies the inputs, runs inference, and decides what to do with the results. You control how the model fits into the device's existing workflow.

The ONNX Runtime APIs included with Windows ML support production use. They let you control inference sessions and select execution providers without writing a separate inference integration for each silicon vendor.

Windows ML is expanding beyond its ONNX Runtime APIs with an experimental Windows ML Runtime API and higher-level APIs for text generation and speech recognition. These additions support more model formats and handle common inference tasks without requiring you to write every step yourself.

The Runtime API integrates [llama.cpp](https://github.com/ggml-org/llama.cpp), an open-source inference engine widely used to run language models locally. It runs compatible models in GGUF format, including quantized versions that can reduce memory and storage requirements. You can use these GGUF models without converting them to ONNX. The same Runtime API also runs compatible ONNX models through ONNX Runtime.

For common tasks, the [Text Generation API](/windows/ai/new-windows-ml/runtime/text-generation) and [Speech Recognition API](/windows/ai/new-windows-ml/runtime/speech-recognition) build on the Windows ML Runtime API. The Text Generation API handles tokenization, the generation loop, and streaming output for a compatible ONNX or GGUF language model you supply. The Speech Recognition API transcribes audio using an ONNX Whisper model. Your application could transcribe a spoken request, then pass the text to a local language model to generate a response. You still supply the models and configure their execution.

Use the [Windows ML Runtime API](/windows/ai/new-windows-ml/runtime/overview) directly when you need finer control over model execution, hardware placement, or multi-model pipelines.

The Runtime and task-specific APIs currently support C++ and Python and remain experimental, not yet supported for production deployment. For GGUF models, this release supports CPU execution and NVIDIA CUDA acceleration. NPU execution is not yet supported by this GGUF/llama.cpp integration. Package the GGUF model and required llama.cpp backend modules with your application.

See [AI Development on Windows: from PyTorch and llama.cpp to Windows ML](https://devblogs.microsoft.com/foundry-on-windows/build-on-winml-oct-7-26/) for architecture and examples.

### Foundry Local: Choose the model, use built-in management

[Foundry Local](/azure/foundry-local/get-started) handles model downloads, caching, loading, and inference through an SDK. The [SDK](/azure/foundry-local/reference/reference-sdk-current) embeds its inference runtime in your application. 

Its catalog includes models that Microsoft has optimized for local use, including chat, reasoning, and speech-to-text models. Foundry Local selects a compatible variant for the device. You can also prepare a compatible custom ONNX model.

On Windows, the Foundry Local SDK can use Windows ML for hardware acceleration. Follow the [Foundry Local SDK setup instructions](/azure/foundry-local/reference/reference-sdk-current) for your programming language to configure that support.

Your application can call Foundry Local directly through the SDK, with inference running inside the application process. Foundry Local also offers an optional local HTTP server with an OpenAI-compatible API.

For offline operation, include the model, required runtime components, execution providers, and drivers in the final device image.

### Windows AI APIs: Use when the capability fits the devices

[Windows AI APIs](/windows/ai/apis/) expose ready-made capabilities such as text processing, image description, OCR, and speech recognition through the Windows App SDK. Windows supplies and services the underlying models. To use a Windows AI API, your device must meet its hardware requirements and have the Windows-managed model that powers that capability installed.

## Prepare your device for deployment

### Prepare the model

If you plan to use ONNX Runtime, export your model to ONNX if needed, then analyze and optimize it for the target hardware. Quantization can reduce memory use and improve inference speed, but check its effect on accuracy in your application.

The [Windows ML CLI](https://aka.ms/winmlcli) provides export, analyze, optimize, quantize, and compile commands. Its [workflow guide](https://microsoft.github.io/winml-cli/latest/) explains how to combine those steps and choose target-specific options.

Foundry Local catalog models already include optimized variants, but you still need to validate the selected variant on the device you plan to build. 

To prepare a custom model for Foundry Local, use Olive, Microsoft's model-conversion and optimization tool, with a [recipe for your model and target hardware](https://github.com/microsoft/olive-recipes). The [Microsoft Learn guide](/azure/foundry-local/how-to/how-to-compile-hugging-face-models) explains the process, including the configuration and supporting files Foundry Local requires alongside the ONNX model.

### Assemble and test the device image

Package the application, model, runtime, required execution providers or backend modules, and drivers in the factory image so the device can run AI without downloading additional components at first use.

If your application uses the ONNX Runtime APIs included with Windows ML, you can bundle the runtime with your application or use a shared runtime installed on the device. With self-contained deployment, your application carries the runtime. With framework-dependent deployment, your application uses a compatible shared runtime through the Windows App Runtime. The [deployment guide](/windows/ai/new-windows-ml/distributing-your-app) explains the options available to your programming language and Windows ML package.

When your application creates an ONNX Runtime session, inference runs on the CPU unless you configure an execution provider for acceleration. Configure a compatible GPU or NPU provider based on the workload's performance and efficiency requirements.

[Microsoft reports NPU and GPU performance on par with dedicated vendor SDKs](/windows/ai/new-windows-ml/overview), with results that vary by model and hardware.

1. Measure latency, memory use, and power under expected operating conditions. Confirm that the model runs on the intended GPU or NPU.
1. Qualify the runtime, model, EPs, and drivers together on the finished image, including offline startup and operation.

### Plan updates

Plan updates for the model, runtime, and execution providers together. You can deploy and service the model separately when it needs a different update cadence from the application or device image.

With a self-contained runtime, you deliver runtime updates with the application. With framework-dependent deployment, plan for updates to the shared Windows App Runtime.

Choose [Windows-managed or bundled execution providers](/windows/ai/new-windows-ml/windows-ml-eps-vs-bring-your-own) to match the device's servicing policy. Windows ML 2.5.96 and later acquire Windows-managed EPs through the Microsoft Store; versions 2.4.89 and earlier use Windows Update. Dynamic acquisition requires Windows 11 version 24H2 or later, compatible hardware and drivers, and access to the relevant delivery services. These requirements apply to dynamically acquired providers, not to all Windows ML inference. If you bundle compatible providers, you control their versions and updates and can include them in the offline image. Test updates with the model, runtime, and drivers on the Windows IoT image you ship. See [execution-provider acquisition guidance](/windows/ai/new-windows-ml/execution-provider-errors) for version-specific details.

## Aion and the next generation of local capabilities

Microsoft is developing on-device models for text tasks and agentic applications. At Build 2026, Microsoft announced [Aion 1.0 Instruct for everyday text tasks and Aion 1.0 Plan](https://blogs.windows.com/windowsdeveloper/2026/06/02/build-2026-furthering-windows-as-the-trusted-platform-for-development/), a 14-billion-parameter reasoning and tool-calling model for local agentic workflows. Aion Instruct will replace Phi Silica.

Aion Plan points toward devices that can help work through a task, not just return a prediction or generate text. For example, a maintenance application could use its reasoning and tool-calling capabilities to investigate a fault, retrieve diagnostic data, and invoke an application-provided tool to take an approved action. Your application would control the available tools, permissions, and approval requirements.

The [Phi Silica documentation](/windows/ai/apis/phi-silica) provides the replacement schedule and guidance for preparing your application. The [Aion Instruct sample](https://aka.ms/tryAion) lets developers validate the model on supported hardware, but its current preview package is not for customer deployment.

## Windows ML in action: A self-checkout kiosk

For an example on how to use Windows ML to perform object detection in a self-checkout kiosk, see the [EdgeAI-ObjectDetection sample](https://github.com/microsoft/Windows-IoT-Samples/tree/master/samples/EdgeAI-ObjectDetection). The self-checkout demo compares the object labels detected by a camera with the labels entered in a shopping cart. At checkout, it displays any mismatches. The comparison checks whether labels are present, not whether item quantities match. Here's how it works:

1. The reusable WinUI control captures camera frames and runs a separately supplied, compatible YOLO model through the ONNX Runtime APIs included with Windows ML.
1. The application selects an execution provider for the target hardware. In the kiosk's Auto mode, it tries NPU, then GPU, then CPU; an explicit hardware selection does not fall back.
1. The control returns detection results to the application, which compares detected labels with the cart and displays any mismatches.

If you're interested in building a similar self-checkout kiosk, download our reusable WinUI user control that wraps the model setup and inference UI, then drop it into any WinUI application. Your application supplies a compatible ONNX model, a camera source, and inference settings, including the selected execution provider.

Use our accompanying app to test out and benchmark the performance of various compatible YOLO models running on different execution providers. Just supply the model and validate the configuration on your target hardware.

> [!NOTE] 
> The sample supports both x64 and Arm64 architectures. This public documentation covers model requirements, initial provider setup, and deployment.

## Get started

Start with our [self-checkout reference design](https://github.com/microsoft/Windows-IoT-Samples/tree/master/samples/EdgeAI-ObjectDetection) to see how model integration, hardware acceleration, and application logic come together. Use the following resources to explore the APIs, prepare your model, and build for your target device.

- [Windows ML](https://aka.ms/winml)
- [Windows ML command-line tool](https://aka.ms/winmlcli)
- [Foundry Local](https://aka.ms/foundrylocal)
- [Edge AI object-detection and self-checkout reference design](https://github.com/microsoft/Windows-IoT-Samples/tree/master/samples/EdgeAI-ObjectDetection)
- [Windows AI APIs setup](/windows/ai/apis/get-started)
- [Windows App SDK](https://aka.ms/winappsdk)
- [Aion Instruct developer validation](https://aka.ms/tryAion)
- [Choosing your Windows AI solution](/windows/ai/windows-ai-comparison)