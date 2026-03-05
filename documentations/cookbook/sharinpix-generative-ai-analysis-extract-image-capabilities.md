---
layout:
  width: default
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
  metadata:
    visible: false
  tags:
    visible: true
---

# SharinPix Generative AI Analysis/Extract Image Capabilities

This article demonstrates how to use the latest GPT models to integrate AI capabilities with SharinPix Images.

In the following sections, you will learn:

* [The SharinPix Playground tab (to write and test your prompts)](sharinpix-generative-ai-analysis-extract-image-capabilities.md#sharinpix-playground)
* [The AIConnect Apex class (to integrate the Gen AI capability to your dev)](sharinpix-generative-ai-analysis-extract-image-capabilities.md#aiconnect)
* [To use AIConnect in Flows (to integrate the Gen AI capability into your flows)](sharinpix-generative-ai-analysis-extract-image-capabilities.md#using-aiconnect-in-flows)

{% hint style="info" %}
**Information:**

The AIConnect feature can be used:

* In your own Lightning Component development
* In Flows
{% endhint %}

{% hint style="warning" %}
**Note:**

To be able to use this feature, you will need an[ OpenAI API key](https://help.openai.com/en/articles/4936850-where-do-i-find-my-openai-api-key).
{% endhint %}

## Prerequisite

To insert your OpenAI API key, you need to go to SharinPix Settings.

![](<../.gitbook/assets/Click on the (3) (1) (1).png>)

After saving your OpenAI API key, you are good to go.

## SharinPix Playground

The SharinPix Playground is a tab on the SharinPix App, which allows users to test the Al Image capabilities as shown in the diagram below,

![](<../.gitbook/assets/SharinPix Playground 1 (1).png>)

On the SharinPix Playground page, we have a SharinPix Album with prompt and result text boxes. The AI feature is called when the "Extract" button is clicked. The "Extract" button runs the Prompt entered against the image being viewed and updates the Result text box with the response.

![](<../.gitbook/assets/SharinPix Playground 2 (1).png>)

## AIConnect

The SharinPix package provides the Apex class, **AIConnect**, which includes methods that integrate OpenAI features. This enables us to execute prompts against the ChatGPT model, using images uploaded to SharinPix.

### AIConnect Example

**extractImageInfo**

_<mark style="color:$danger;">`global static String extractImageInfo(String imageUrl, String prompt)`</mark>_

* This method can be used to extract information according to the prompt provided from the image using the imageUrl.

```apex
String url = 'https://p.sharinpix.com/image.png';
String prompt = 'Provide the licenses plate number found on the image';
String result = sharinpix.AIConnect.extractImageInfo(url, prompt);
```

_<mark style="color:$danger;">`global static String extractImageInfo(String imageUrl, String prompt, String modelName)`</mark>_

* This version performs the same action as the method above but also allows specifying a **custom GPT model name** to use for the analysis.
* If the <mark style="color:$danger;">`modelName`</mark> parameter is left blank, the GPT Model defaults to <mark style="color:$danger;">`gpt-4o`</mark>.

```
String url = 'https://p.sharinpix.com/image.png';
String prompt = 'Identify the type of vehicle and its color visible in the image';
String modelName = 'gpt-4o';
String result = sharinpix.AIConnect.extractImageInfo(url, prompt, modelName);
```

## Using AIConnect in Flows

### Using AIConnect in a Screen Flow

**AIConnectAutomation** is an Apex Invocable method that uses the AIConnect class. This enables the use of AIConnect in a Screen Flow to analyze SharinPix images using a prompt provided by the user.

This section demonstrates how to build a flow that allows the user to input a custom prompt, select a single image from a SharinPix Album, and display the AI-generated analysis result in real time.

{% hint style="warning" %}
**Warning**\
This setup is optimized to analyze **one image at a time**. If the user selects multiple images, the flow will fail. For analyzing multiple images at once, refer to the [SharinPix AI Extractor documentation.](sharinpix-ai-extractor-integration-in-salesforce-flow-admin-oriented.md)
{% endhint %}

### Flow Configuration Overview:

Below is a visual representation of the flow:

1. **Screen** – Prompt input and image selection
2. **Assignment** – Create and assign variables
3. **Get Records** – Retrieve the selected image
4. **Apex Action** – Call AIConnectAutomation
5. **Screen** – Display the AI-generated response

### Step-by-Step Setup

**Step 1: Create a New Screen Flow**

* Go to **Setup > Flows** and create a **new Screen Flow**.

![](<../.gitbook/assets/SharinPix Generative AI AnalysisExtract Image Capabilities (1).png>)

**Step 2: Add a Screen – “Select Image to Analyse”**

* Add a **Long Text Area** input for the user to type the AI prompt.
* Below the component, add a **SharinPix Album** component for image selection.
  * In the <mark style="color:$danger;">`AlbumId`</mark> field, create a new resource of type **Variable** and Data Type **Text.** For the**API Name,** please type in "**recordId** ".

![](<../.gitbook/assets/SharinPix Generative AI AnalysisExtract Image Capabilities (9) (1).png>)

**Step 3: Add an Assignment – “Set prompt and image”**

* Create 2 variables:

1. <mark style="color:$danger;">`selectedImage`</mark>
   * Resource Type: Variable
   * Data Type: Text
   * Allow multiple values (collection): ✅ (Ticked)
2. <mark style="color:$danger;">`prompt`</mark>
   * Resource Type: Variable
   * Data Type: Text

* Assign:
  * <mark style="color:$danger;">`selectedImage`</mark> ← selected image ID from album component from **Select Image to Analyse screen**
  * <mark style="color:$danger;">`prompt`</mark> ← user-entered prompt from **Select Image to Analyse screen**

![](<../.gitbook/assets/SharinPix Generative AI AnalysisExtract Image Capabilities (8) (1).png>)

**Step 4: Add a Get Records Element – “Get SharinPix Image”**

* Object: <mark style="color:$danger;">`SharinPix__Image__c`</mark>
* Condition Requirements:
  * <mark style="color:$danger;">`sharinpix__ImagePublicId__c`</mark> IN <mark style="color:$danger;">`selectedImage`</mark>
* Store:
  * Only the first record
  * Automatically store all fields

![](<../.gitbook/assets/SharinPix Generative AI AnalysisExtract Image Capabilities (4) (1).png>)

**Step 5: Add Apex Action – “Analyse Image”**

* Search for and add **AIConnectAutomation**.
* Example input values:
  * **Image URL** : <mark style="color:$danger;">`Get_SharinPix_Image.sharinpix__ImageURLFull__c`</mark>
  * **Prompt** : <mark style="color:$danger;">`prompt`</mark>
  * **GPT Model:** <mark style="color:$danger;">`gpt-4o`</mark> (if no value is provided, defaults to <mark style="color:$danger;">`gpt-4o`</mark>)

{% hint style="warning" %}
**Warning**

* Different GPT Models (e.g., GPT-4o, GPT-5) have different pricing depending on their capabilities and token usage. You can check the latest pricing on [OpenAI’s official page](https://openai.com/api/pricing/).
* Ensure your OpenAI account has **sufficient credit balance** to process requests.
{% endhint %}

![](<../.gitbook/assets/SharinPix Generative AI AnalysisExtract Image Capabilities (12) (1).png>)

**Step 6: Add a Screen – “Display Analysis”**

* Add a **Read-only Long Text Area** or **Display Text** component and set its default value to the output from the Apex Action. In this case <mark style="color:$danger;">`Text from Analyse_Image`</mark>.

After sending the request, the AI-generated response will be displayed to the user in this screen.

![](<../.gitbook/assets/Click on the (18) (1) (1).png>)

### Demo

Step 1 : Put your flow on the record page and make sure to tick the box to pass in the record ID to the flow.

![](<../.gitbook/assets/SharinPix Generative AI AnalysisExtract Image Capabilities (6) (1).png>)

Step 2: On your record page, select the image you want to analyse and and type in your prompt. Click the next button to proceed to the results page.

![](<../.gitbook/assets/SharinPix Generative AI AnalysisExtract Image Capabilities (7) (1).png>)

The AI Analysis result will be displayed on the next screen.

![](<../.gitbook/assets/SharinPix Generative AI AnalysisExtract Image Capabilities (10) (1).png>)

### Using AIConnect in a Record Triggered Flow

* Create a new Flow on SharinPix Image creation. The Flow will be triggered every time a SharinPix image is created, and then the response from the AIConnectAutomation will be updated in its Description field.

![](<../.gitbook/assets/Click on the (4) (1).png>)

* Since a Response is expected from the AIConnect call, you need to check the box:
  * “Include a Run Asynchronously path to access an external system after the original transaction for the triggering record is successfully committed“ as shown below.

![](<../.gitbook/assets/Click on the (5) (1).png>)

* Create a new resource (Constant) for a static prompt as follows.

![](<../.gitbook/assets/Click on the (6) (1).png>)

* Add an Apex Action and select the Apex class **AIConnectAutomation.**
* Image URL: Enter the image's URL.
* Prompt: Use the resource 'MyStaticPrompt' created earlier for the prompt.
* GPT Model: Input example value <mark style="color:$danger;">`gpt-5`</mark>.

![](<../.gitbook/assets/SharinPix Generative AI AnalysisExtract Image Capabilities (11) (1).png>)

* Update the SharinPix Image Object with the response from AIConnectAutomation apex action.

![](<../.gitbook/assets/Click on the (11) (1) (1).png>)

## Need help to write your GenAI image prompt?

The visual experts are here to help. Just send an email to [info@sharinpix.com](mailto:info@sharinpix.com) to get some help so we can explain you how we can deliver services through our experts to assist you on that duty!
