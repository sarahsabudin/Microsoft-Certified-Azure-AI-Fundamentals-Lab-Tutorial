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

<img width="2183" height="395" alt="image" src="https://github.com/user-attachments/assets/6199f558-4bbb-4dd3-8661-4f98e5caae04" />

3. On the first launch, choose **PowerShell**.
4. If prompted, create storage for Cloud Shell and wait for setup to complete.

<img width="2495" height="803" alt="image" src="https://github.com/user-attachments/assets/6a7c0af2-36e3-4b82-b143-31dccc37ab01" />

6. Ensure the shell type is **PowerShell** (switch from Bash if needed).

<img width="1981" height="336" alt="image" src="https://github.com/user-attachments/assets/388388df-4c0d-4cb6-ba9f-5a41b9dbdaf5" />

7. Wait for PowerShell to start. You should see the following screen in the Azure portal:

<img width="2495" height="485" alt="image" src="https://github.com/user-attachments/assets/37053242-6ca4-4707-9c37-819014b506d6" />

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
<img width="2495" height="485" alt="image" src="https://github.com/user-attachments/assets/32557ced-307c-40c1-b928-2f676c9b9c35" />

<img width="1241" height="1059" alt="image" src="https://github.com/user-attachments/assets/2b9f2b7f-d65c-44e7-8cd8-ea8c46ef801c" />

3. In the **Files** pane, expand `ai-900` and open `analyze-image.ps1`.This file contains some code that uses the Computer Vision service to analyze an image, as shown here:

5. Replace the placeholder values with your Azure AI services resource credentials:


```powershell
$key="YOUR_KEY_HERE"
$endpoint="YOUR_ENDPOINT_HERE"
```
After pasting the key and endpoint values, the first two lines of code should look similar to this:
Save the changes using the … menu in the editor.

```powershell
 $key="1a2b3c4d5e6f7g8h9i0j...."    
 $endpoint="https..."
```
6. At the top right of the editor pane, use the … button to open the menu and select Save to save your changes

## Task 4 – Analyze Images

The sample client application will use your Computer Vision service to analyze the following image, taken by a camera in the Northwind Traders store:

### Analyze First Image

<img width="1024" height="682" alt="image" src="https://github.com/user-attachments/assets/c5aed60e-0e22-4b18-b119-5801a6cc300d" />

```powershell
cd ai-900
./analyze-image.ps1 store-camera-1.jpg
```
Review the results, including:
- Suggested caption
- List of objects detected
- Relevant tags

### Analyze Second Image

<img width="1024" height="682" alt="image" src="https://github.com/user-attachments/assets/f47c04ef-330b-4b55-9072-4e968e4c84d1" />

```powershell
./analyze-image.ps1 store-camera-2.jpg
```
Review the results for this image.

<img width="1024" height="682" alt="image" src="https://github.com/user-attachments/assets/801db97f-0317-4a43-a818-5e71fde1edde" />

### Analyze Third Image

![Uploading image.png…]()

```powershell
./analyze-image.ps1 store-camera-3.jpg
```
Review the analysis results.

## Task 5 – Learn More

This sample application demonstrates basic capabilities of the Computer Vision service.
For additional features, see the Computer Vision documentation
.
