# Lab 02 – Explore Automated Machine Learning in Azure ML

## Introduction

In this lab, you will use the automated machine learning feature in Azure Machine Learning to train and evaluate a machine learning model. You will then deploy and test the trained model as a web service.

This exercise uses historical bicycle rental data to train a regression model that predicts the number of rentals expected on a given day.

Estimated completion time: 30 minutes.

> Note: To complete this lab, you need an Azure subscription with administrative access.

---

## Objectives

By completing this lab, you will:

- Create an Azure Machine Learning workspace
- Enable preview features in Azure Machine Learning Studio
- Train a regression model using Automated ML
- Review model performance metrics
- Deploy and test a real-time prediction endpoint
- Perform resource cleanup to manage costs

---

## Prerequisites

- An active **Azure subscription**
- Administrative access to create resources
- Access to the **Azure portal**
- Web browser access to **Azure Machine Learning Studio**

---

## Task 1 – Create an Azure Machine Learning Workspace

To use Azure Machine Learning, you must first provision a workspace.

> Tip: If you already have an Azure Machine Learning workspace, you may skip to the next task.

1. Sign in to the Azure portal:  
   https://portal.azure.com

2. Select **+ Create a resource**.
3. Search for **Machine Learning**.
4. Select **Azure Machine Learning**.
5. Click **Create**.
6. Configure the following settings:

| Setting | Value |
|----------|--------|
| Subscription | Your Azure subscription |
| Resource group | Create or select a resource group |
| Name | Enter a unique workspace name |
| Region | Select the closest geographical region |
| Storage account | Default new storage account |
| Key vault | Default new key vault |
| Application insights | Default new application insights resource |
| Container registry | None |

7. Select **Review + create**.
8. Select **Create**.
9. Wait for deployment to complete.
10. Go to the deployed resource.
11. Select **Launch studio**.

Alternatively, open:

https://ml.azure.com

12. Sign in using your Microsoft account.
13. Close any pop-up messages.
14. If your workspace is not displayed, select **All workspaces** from the left menu and choose your workspace.

---

## Task 2 – Enable Preview Features

1. In Azure Machine Learning Studio, click **Manage preview features** (loudspeaker icon).
2. Enable the following preview feature:

- **Guided experience for submitting training jobs with serverless compute**

---

## Task 3 – Use Automated Machine Learning to Train a Model

1. In Azure Machine Learning Studio, go to **Automated ML** (under Authoring).
2. Select **+ New Automated ML job**.

### Basic Settings

| Setting | Value |
|----------|--------|
| Job name | mslearn-bike-automl |
| New experiment name | mslearn-bike-rental |
| Description | Automated machine learning for bike rental prediction |
| Tags | None |

Click **Next**.

---

### Task Type & Data

- Select task type: **Regression**
- Select dataset: **Create a new dataset**

#### Data Type

| Setting | Value |
|----------|--------|
| Name | bike-rentals |
| Description | Historic bike rental data |
| Type | Tabular |

#### Data Source

- Select **From web files**
- Web URL:  
  https://aka.ms/bike-rentals
- Skip data validation: Do not select

#### Settings

| Setting | Value |
|----------|--------|
| File format | Delimited |
| Delimiter | Comma |
| Encoding | UTF-8 |
| Column headers | Only first file has headers |
| Skip rows | None |
| Dataset contains multi-line data | Do not select |

#### Schema

- Include all columns except **Path**
- Review automatically detected data types

After creating the dataset, select **bike-rentals**.

Click **Next**.

---

### Task Settings

| Setting | Value |
|----------|--------|
| Task type | Regression |
| Dataset | bike-rentals |
| Target column | Rentals |

#### Additional Configuration Settings

| Setting | Value |
|----------|--------|
| Primary metric | Normalized root mean squared error |
| Explain best model | Unselected |
| Use all supported models | Unselected |
| Allowed models | RandomForest, LightGBM |

#### Limits

| Setting | Value |
|----------|--------|
| Max trials | 3 |
| Max concurrent trials | 3 |
| Max nodes | 3 |
| Metric score threshold | 0.85 |
| Timeout (minutes) | 15 |
| Iteration timeout (minutes) | 5 |
| Enable early termination | Selected |

#### Validation and Test

| Setting | Value |
|----------|--------|
| Validation type | Train-validation split |
| Percentage of validation data | 10 |
| Test dataset | None |

Click **Next**.

---

### Compute

| Setting | Value |
|----------|--------|
| Compute type | Serverless |
| Virtual machine type | CPU |
| Virtual machine tier | Dedicated |
| Virtual machine size | Standard_DS3_V2 |
| Number of instances | 1 |

Click **Submit**.

The training job starts automatically.

Wait for completion.

---

## Task 4 – Review the Best Model

1. When the job completes, open the **Overview** tab.
2. Review the **Best model summary**.
3. If you see the message  
   *“Warning: User specified exit score reached…”*  
   continue to the next step.
4. Select the **Algorithm name** of the best model.
5. Select the **Metrics** tab.
6. Review:
   - **Residuals chart**
   - **Predicted vs True chart**

The residuals chart displays differences between predicted and actual values.  
The predicted_true chart compares predictions against true values.

---

## Task 5 – Deploy and Test the Model

1. On the **Model** tab of the best model, select **Deploy**.
2. Choose **Web service**.
3. Configure:

| Setting | Value |
|----------|--------|
| Name | predict-rentals |
| Description | Predict cycle rentals |
| Compute type | Azure Container Instance |
| Enable authentication | Selected |

4. Click **Deploy**.
5. Wait until **Deploy status** changes from Running to **Succeeded** (5–10 minutes).

---

## Task 6 – Test the Deployed Service

1. In Azure Machine Learning Studio, select **Endpoints**.
2. Open the **predict-rentals** endpoint.
3. Select the **Test** tab.
4. Replace the template JSON with:

```json
{
  "Inputs": { 
    "data": [
      {
        "day": 1,
        "mnth": 1,
        "year": 2022,
        "season": 2,
        "holiday": 0,
        "weekday": 1,
        "workingday": 1,
        "weathersit": 2,
        "temp": 0.3,
        "atemp": 0.3,
        "hum": 0.3,
        "windspeed": 0.3
      }
    ]
  },
  "GlobalParameters": 1.0
}

5. Click **Test**.

6. Review the results.

Example output:

```json
{
  "Results": [
    444.27799000000000
  ]
}

The model returns a predicted number of bicycle rentals based on the input features.

---

## Task 7 – Clean-up

### Delete Endpoint

1. In **Azure Machine Learning Studio**, go to **Endpoints**.
2. Select **predict-rentals**.
3. Click **Delete**.
4. Confirm deletion.

### Delete Workspace (Optional)

1. Open the **Azure portal**.
2. Go to **Resource groups**.
3. Select the resource group used for this lab.
4. Click **Delete resource group**.
5. Enter the resource group name.
6. Select **Delete**.

---

## Why Automated Machine Learning in Azure ML

This lab demonstrates:

- How to provision an Azure Machine Learning workspace
- How to configure and run Automated ML jobs
- How to evaluate regression model performance
- How to deploy a real-time prediction endpoint
- How to test machine learning models via REST input

This hands-on exercise reinforces key AI-900 concepts around machine learning workflows, model evaluation, and deployment in Azure.
