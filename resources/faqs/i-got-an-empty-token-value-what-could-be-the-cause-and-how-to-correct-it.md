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

# I got an empty token value, what could be the cause and how to correct it?

Some common causes leading to an empty SharnPix token value are:

* Automations such as Flows, Triggers, or Process Builder block the proper generation of the token.
* Users attempting to generate a SharinPix token without having proper access to the SharinPix token field.\
  \
  In cases involving the token generation using automation such as Flows, Triggers, or Process Builders, the user launching them should have edit access rights on the SharinPix Token field.
* Records are created before activation of the automation that populates the token fields.\
  \
  It could happen that a record containing the SharinPix Token field has been created before the activation of the automation or during the deactivation of the automation. In such cases, the SharinPix Token field will not be populated with the generated token. Here, the token should be generated manually. The next section details how you can manually generate a token on a record.
* It may also happen that users accidentally delete the token value in the fields. Therefore, we recommend the activation of [Field History Tracking](https://trailhead.salesforce.com/en/content/learn/projects/customize-a-salesforce-object/account-field-history-tracking) to keep track of changes that might have taken place in such fields.

## How to manually generate a token? (Some developer skills required)

### By modifying your current Flow

If the token generation Flow triggers the token generation only at the creation of the record, you simply need to:

* Modify the Flow so that it triggers when a record is being created and **updated** instead of only upon record creation.
* Once the Flow is modified:
  * Go to the record having the missing token.
  * Perform a simple update on the same record in order to trigger the Flow so that it performs the token generation. You can just click on the _Edit_ button followed by the _Save_ button for the update to perform the same.
* Finally, revert the modification on your Flow so that it only triggers upon the creation of records again.

If the Flow is already configured to be triggered upon the update of the records, then you simply need to perform a simple update on the record missing the token in order to regenerate the token. No need to modify the Flow in this case.

### Using the TokenGeneration Apex class

To manually generate a SharinPix upload token, you can make use of the Apex class **TokenGeneration** available in the SharinPix package.

Follow the steps below to do so:

* Open your Developer Console
* Click **Debug** | **Open Execute Anonymous Window** to open the **Enter Apex Code** window
* Then, execute the following code snippet:

```apex
List<sharinpix.TokenGeneration.Parameters> paramsList = new List<sharinpix.TokenGeneration.Parameters>();
sharinpix.TokenGeneration.Parameters param = new sharinpix.TokenGeneration.Parameters();      
param.recordId = '<Enter Your Record ID>';
param.fieldname = '<Enter the SharinPix Token Field API name>';
paramsList.add(param);
sharinpix.TokenGeneration.createToken(paramsList);
```

{% hint style="warning" %}
**Note:**

1\. The above configuration generates SharinPix tokens that only allow **photo uploads** using the SharinPix mobile app.

2\. The **recordId** parameter refers to the record ID on which you want to generate the token and the **fieldname** parameter refers to the SharinPix token field in which you want to store the generated token.

**These two parameters (that is, recordId and fieldname) are required and therefore should always be populated.**

3\. There are two more variables which are available in the available in the **TokenGeneration** class, namely:

* **name -** which can be used to reference the record name (or number) inside the token.
* **numberOfHours -** which can be used to set the number of hours before the token expires. This variable has a type **Number** and only takes **integers** as values. For example, if you want the token to expire in 3 hours, just enter 3 in the **Value** field.

The **name** and **numberOfHours** parameters are not required by default. If you want to make use of these two additional parameters as well, here is how the code should be like:
{% endhint %}

```apex
List<sharinpix.TokenGeneration.Parameters> paramsList = new List<sharinpix.TokenGeneration.Parameters>();
sharinpix.TokenGeneration.Parameters param = new sharinpix.TokenGeneration.Parameters();      
param.recordId = '<Enter Your Record ID>';
param.fieldname = '<Enter the SharinPix Token Field API name>';
param.name = '<Enter the Field Name>';
param.numberOfHours = 2;
paramsList.add(param);
sharinpix.TokenGeneration.createToken(paramsList);
```

### DEPRECATED: By modifying your current Process Builder

If your Process Builder triggers the token generation only at the creation of the record to generate the missing token, you simply need to:

* Modify your Process Builder so that it triggers when a record is being **updated** instead of on its creation.
* Then, go to the record having the missing token.
* Perform a simple update on the same record in order to trigger the Process Builder so that it performs the token generation. You can just click on the Edit button followed by the Save button for the update.
* Finally, revert the modification on your Process Builder so that it triggers upon the creation of records again.

If your Process Builder is already configured to be triggered upon the update of the records, then you simply need to perform a simple update on the record missing the token in order to generate the token. No need to modify the Process Builder in this case.

{% hint style="info" %}
If you need assistance in generating missing tokens on existing records, kindly contact the SharinPix Support team using th&#x65;_&#x53;harinPix Support_ tab in the _SharinPix_ app within your Salesforce organization.
{% endhint %}
