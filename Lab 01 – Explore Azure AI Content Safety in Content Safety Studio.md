# Lab 01 – Explore Azure AI Content Safety in Content Safety Studio

## Introduction

Azure AI services provide pre-built and customizable APIs and models to help developers integrate artificial intelligence capabilities into applications. In this lab, you will explore **Azure AI Content Safety** using the **Content Safety Studio**.

The Content Safety Studio enables you to test and evaluate how text and image content is moderated. You will provision a single-service Content Safety resource and run moderation tests to understand how severity levels are determined.

> Note: The goal of this exercise is to gain a general understanding of how Azure AI services are provisioned and used. This lab does not require comprehensive knowledge of content safety concepts.

---

## Objectives

By completing this lab, you will:

- Provision an Azure AI Content Safety resource
- Associate an Azure AI resource with Content Safety Studio
- Run text moderation tests using built-in samples
- Interpret severity scores and moderation results
- Locate keys and endpoints for application integration

---

## Prerequisites

- An active **Azure subscription**
- Access to the **Azure Portal**
- Web browser access to **Content Safety Studio**
- Permission to create resources in Azure

---

## Task 1 – Navigate the Content Safety Studio

1. Open the **Content Safety Studio**.
2. If you are not logged in, select **Sign In** in the top right corner of the screen.
3. Use the email and password associated with your Azure subscription to sign in.
4. On the menu at the top of the screen, click the icon on the left of **Azure AI**.
5. Observe the drop-down list of other studios designed for development with Azure AI services.
6. Click the icon again to hide the list.

---

## Task 2 – Associate a Resource with the Studio

Before using the studio, you must associate an Azure AI services resource with it.

In this lab, you will create a **single-service Content Safety resource**.

1. On the top right of the screen, click the **Settings** icon.
2. On the Settings page, locate the **Directory** tab and **Resource** tab.
3. Select the **Resource** tab.
4. Click **Create a new resource**.

> Note: The Directory tab allows users to select different directories. You do not need to change it unless you want to use a different directory.

5. In the Azure Portal, on the **Create Content Safety** page, configure the following settings:

| Setting | Value |
|----------|--------|
| Subscription | Your Azure subscription |
| Resource group | Select or create a resource group with a unique name |
| Region | Choose any available region |
| Name | Enter a unique name |
| Pricing tier | Free F0 |

6. Select **Review + Create**.
7. Review the configuration.
8. Select **Create**.
9. Wait for deployment to complete.

You have now provisioned a single-service **Content Safety** resource.

10. After deployment completes, open a new browser tab and return to **Content Safety Studio**.
11. Click the **Settings** icon again.
12. Confirm that your newly created resource appears in the list.
13. Select the resource.
14. Click **Use resource** at the bottom of the screen.
15. You will be returned to the studio home page.

---

## Task 3 – Try Out Text Moderation in the Content Safety Studio

1. On the Content Safety Studio home page, under **Run moderation tests**, locate the **Moderate text content** box.
2. Click **Try it out**.
3. Under **Run a simple test**, select **Safe Content**.
4. Observe that text appears in the input box.
5. Click **Run test**.
6. In the **Results** panel, review the output.

You will observe:

- Four severity levels: **Safe**, **Low**, **Medium**, **High**
- Four types of harmful content categories
- Confidence-based evaluation results

7. Determine whether the AI service considers the sample acceptable.
8. Now select the sample under **Violent content with misspelling**.
9. Confirm the content appears in the input box.
10. Click **Run test**.
11. Inspect the results in the **Results** panel.
12. Optionally, run tests on additional samples and review their severity scores.

---

## Task 4 – Check Out the Keys and Endpoint

The moderation capabilities can be integrated into applications using the resource's **endpoint** and **keys**.

### In Content Safety Studio

1. Navigate back to the **Settings** page.
2. Ensure the **Resources** tab is selected.
3. Locate your resource.
4. Scroll to view the **Endpoint** and **Key** values.

### In the Azure Portal

1. Open the **Azure Portal**.
2. In the top search bar, search for **Content Safety**.
3. Select your resource.
4. In the left-hand menu under **Resource Management**, select **Keys and Endpoints**.
5. Review the endpoint and keys listed.
6. After completing the lab, navigate to the **Overview** page of your Content Safety resource.
7. Select **Delete** at the top of the screen.
8. Confirm deletion to remove the resource and reduce costs.

---

## Optional Cleanup

To avoid unnecessary charges:

- Navigate to the **Azure Portal**
- Locate your **Content Safety resource**
- Select **Delete**
- Confirm the deletion
- Monitor **Notifications** for completion

---

## Why Azure AI Content Safety Lab

This lab demonstrates:

- How Azure AI services are provisioned
- How to associate resources with Azure AI studios
- How built-in AI models classify and score harmful content
- How to access keys and endpoints for application integration
- How Azure AI services can be integrated into real-world applications

This exercise validates your understanding of Azure AI service deployment and usage, which is a core concept in the AI-900 certification path.
