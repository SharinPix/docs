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

# SharinPix Flow JSON Parser Integration in Salesforce Flow (Admin-Oriented)

## Overview

The **FlowJSONParser** invocable method allows Salesforce users to parse JSON strings within a Flow. It provides a streamlined way to extract specific values from a JSON string and automatically store them into Salesforce object fields. This automation eliminates manual data entry, helping users efficiently work with structured JSON data.

This document covers the following topics:

* **FlowJSONParser Parameters** : A breakdown of the input and output parameters that power the AI extraction process, detailing how the data is processed and returned.

{% hint style="warning" %}
**Prerequisites:**

Before integrating the JSON Parser in a Salesforce Flow,

* Ensure that you are on a recent SharinPix Package Version. Follow this document to [upgrade the SharinPix package](https://app.gitbook.com/s/i8tH1o5AHthxksYgF6ij/how-to-update-sharinpix-package-from-the-appexchange)
{% endhint %}

## SharinPix Flow JSON Parser Parameters

### Input Parameters

Below are the **inputs** required when using the **FlowJSONParser** invocable method in a Salesforce Flow.

| **Parameter**        | **Description**                                                                                                                                                                                                                                                                                                                                           |
| -------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| JSON String to Parse | <ul><li>This is the JSON string that needs to be parsed. It can either be a plain JSON string or a Text Template formatted to JSON.</li><li>This parameter is <strong>required</strong> for parsing the provided JSON data.</li></ul>                                                                                                                     |
| Ignore Error?        | <ul><li>A Boolean value indicating whether errors should be ignored during parsing.</li><li>If set to <strong>True</strong>, any parsing errors will result in the response: <mark style="color:$danger;"><code>[Error]: &#x3C;error text></code></mark>.</li><li>This parameter is <strong>required</strong>.</li></ul>                                  |
| Index                | <ul><li>This parameter specifies the index in case the provided JSON is an array.</li><li>It allows you to specify which element in the array to parse.</li></ul>                                                                                                                                                                                         |
| Field01 - Field10    | <ul><li>These are the keys from the JSON data that need to be extracted.</li><li>You can specify up to 10 fields (from <strong>Field01</strong> to <strong>Field10</strong>) to retrieve specific values from the JSON.</li><li>Each field corresponds to a key in the provided JSON and will return the associated value from the JSON object.</li></ul> |

{% hint style="warning" %}
**Note:**

The number of fields is limited to **10 keys** only. If the provided JSON contains more keys than the specified number of fields, the additional keys will not be extracted.
{% endhint %}

### Output Parameters

Below are the **outputs** received when using the **FlowJSONParser** invocable method.

| **Parameter**     | **Description**                                                                                                                                                                                                                                                                                                                                                                       |
| ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Value01 - Value10 | <ul><li>These output variables hold the parsed values from the provided JSON string, corresponding to the keys specified in <strong>Field01</strong> to <strong>Field10</strong>.</li><li>You can assign these values either to a <strong>variable</strong> to store the parsed data or directly to a <strong>Salesforce object field</strong> to keep the extracted value.</li></ul> |

These output parameters allow users to easily store and use extracted data from JSON strings within Salesforce flows, automatically populating fields in Salesforce objects based on the parsed values.

{% hint style="info" %}
**Info:**

For more information on how to integrate the JSON parser within a flow, please follow the article below: [Parse the JSON Result](sharinpix-ai-extractor-integration-in-salesforce-flow-admin-oriented.md#step-5-parse-the-extracted-result)
{% endhint %}
