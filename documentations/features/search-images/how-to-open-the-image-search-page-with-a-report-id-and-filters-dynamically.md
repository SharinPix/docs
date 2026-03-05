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

# How to open the Image Search page with a Report Id and Filters dynamically

SharinPix allows you to open the Image Search page directly using a Report Id and personalized filters.

This feature is similar to the [SharinPix Image Search tab](using-the-search-image-tab.md) implementation present in your organization. Using this feature, you can now open the search page with the **reportId** parameter to automatically display the images related to the report result, instead of choosing a report from the report selector as it is the case in the Image Search tab.

Additionally, you can pass report filters instead of editing the report itself to add filters each time. Here, we are making use of the Salesforce Report URL Hacking principle to pass the parameters.

## URL Format

The example below demonstrates the URL format that needs to be called:

<mark style="color:red;">`/apex/sharinpix__ImageSearch?reportId=<YOUR_REPORT_ID>`</mark>

The above URL should be used according to your Salesforce domain. For example:

<mark style="color:blue;">**https://sharinpix-fsl-demo-dev-ed--sharinpix.na73.visual.force.com**</mark>**/apex/ImageSearch?reportId=00O1I000000lcRXUAQ**

## Report Filters

As mentioned earlier, this feature makes use of the Salesforce URL Hacking.

<mark style="color:red;">`/apex/sharinpix__ImageSearch?reportId=report_id&reportFilters=[{"column":"your field name goes here","operator":"equals","value":"your value goes here"}]`</mark>

Only 3 parameters are needed in a report filter: **column** , **operator** and **value**.

Everything is in a JSON formatted array. Therefore, to apply multiple filters you can add multiple set of filter inside the array.

The Operators (**case sensitive**) available are:

* equals
* notEqual
* lessThan
* greaterThan
* lessOrEqual
* greaterOrEqual
* contains
* notContain
* startsWith

The Column name differs for each object. You should ensure that the name being used in the report filter is correct to avoid report errors.

{% hint style="warning" %}
**Note:**

* For the time being, multiple filters use the **AND** operator
* If filters are already applied on the report, they will be overwritten
* Column name will differ from reports. Make sure that you are using the correct one
{% endhint %}

## Example

The example below demonstrates a personalized Image Search page URL with customized report filters:

```
https://sharinpix-fsl-demo-dev-ed--sharinpix.na73.visual.force.com/apex/sharinpix__ImageSearch?reportId=00O1I000000lkyXUAQ&reportFilters=[{"column":"EMPLOYEES","operator":"greaterThan","value":"8"},{"column":"ACCOUNT.NAME","operator":"equals","value":"SharinPix"}]
```

The above will open the Image Search page with images uploaded to Account records having employees greater that 8 and account name equaling to SharinPix.
