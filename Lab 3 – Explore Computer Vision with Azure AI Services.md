# Lab 3 – Explore Computer Vision with Azure AI Services

## Introduction
In this lab, you will explore the Azure Computer Vision service by using a simple command-line application. Computer Vision uses pre-trained machine learning models to analyze images and extract meaningful information, such as captions, objects, and tags. This lab demonstrates how to provision an Azure AI services resource, run a client application, and analyze images in a controlled environment.

## Objectives
- Provision an Azure AI services resource for Computer Vision
- Use Azure Cloud Shell to run PowerShell commands
- Configure and run a sample client application
- Analyze multiple images using the Computer Vision service
- Understand key output types: captions, objects, and tags

## Prerequisites
- Azure subscription with administrative access
- Access to the Azure portal (https://portal.azure.com)
- Basic familiarity with PowerShell

---

## Task 1 – Create an Azure AI Services Resource

1. Open the [Azure portal](https://portal.azure.com) and sign in.
2. Click **+ Create a resource**.
3. Search for **Azure AI services** and select **Create**.
4. Configure the resource with the following settings:

| Setting         | Value |
|-----------------|-------|
| Subscription    | Your Azure subscription |
| Resource group  | Select or create a unique resource group |
| Region          | Any available region |
| Name            | Enter a unique name |
| Pricing tier     | Standard S0 |
| Acknowledge terms | Selected |

5. Click **Review + create**, then **Create**.
6. After deployment, navigate to the **Keys and Endpoint** page of the resource. You will use these credentials in the client application.

---

## Task 2 – Run Cloud Shell

1. In the Azure portal, select the **Cloud Shell** icon ([>_]) at the top right.
2. On the first launch, choose **PowerShell**.
3. If prompted, create storage for Cloud Shell and wait for setup to complete.
4. Ensure the shell type is **PowerShell** (switch from Bash if needed).

---

## Task 3 – Configure and Run a Client Application

1. In Cloud Shell, clone the sample repository:

```powershell
git clone https://github.com/MicrosoftLearning/AI-900-AIFundamentals ai-900
```

2. Open the code editor:

```powershell
code .
```


3. In the **Files** pane, expand `ai-900` and open `analyze-image.ps1`.
4. Replace the placeholder values with your Azure AI services resource credentials:

```powershell
$key="YOUR_KEY_HERE"
$endpoint="YOUR_ENDPOINT_HERE"
```
Save the changes using the … menu in the editor.

## Task 4 – Analyze Images

### Analyze First Image

```powershell
cd ai-900
./analyze-image.ps1 store-camera-1.jpg
```
Review the results, including:
- Suggested caption
- List of objects detected
- Relevant tags

### Analyze Second Image

```powershell
./analyze-image.ps1 store-camera-2.jpg
```
Review the results for this image.

### Analyze Third Image

```powershell
./analyze-image.ps1 store-camera-3.jpg
```
Review the analysis results.

## Task 5 – Learn More

This sample application demonstrates basic capabilities of the Computer Vision service.
For additional features, see the Computer Vision documentation
.
