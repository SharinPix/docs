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

# SharinPix Mobile App: Track Mobile Users Uploading Photos From the SharinPix Mobile App

{% hint style="info" %}
The SharinPix mobile app uses tokens to authenticate itself and upload photos that can be viewed on Salesforce.&#x20;

Since the app is built for offline use, the tokens are usually generated beforehand and stored in Salesforce fields on records. This allows multiple users to upload photos to a single Salesforce record. As such, the tokens cannot be tied to any specific user to avoid relating the user to all photos uploaded by anyone to the record. Thus, the tokens are "anonymous".

This article demonstrates how to keep track of the user uploading photos using "anonymous" tokens. The article covers how to:

1. [Configure the SharinPix Mobile Launcher component to retrieve the mobile user that performed the upload.](sharinpix-mobile-app-track-mobile-users-uploading-photos-from-the-sharinpix-mobile-app.md#configure-the-sharinpix-mobile-launcher-component-to-retrieve-the-mobile-user-information)
2. [Configure a deeplink (link to upload photos from the SharinPix mobile app) to retrieve the mobile user that performed the upload.](sharinpix-mobile-app-track-mobile-users-uploading-photos-from-the-sharinpix-mobile-app.md#configure-a-deeplink-to-retrieve-the-mobile-user-information)
{% endhint %}

{% hint style="success" %}
**Tip:**

For more information on SharinPix tokens, refer to this documentation: [Working with SharinPix Tokens](../best-practices/working-with-sharinpix-tokens.md)
{% endhint %}

{% hint style="warning" %}
**Note:**

The user identifier will be saved on a SharinPix Image record. To enable the use of the SharinPix Image object, kindly ensure that the SharinPix Image Sync has been activated on the Salesforce object on which users are uploading photos.

For more information on SharinPix Image Sync, refer to this article: [What is SharinPix Image Sync?](../image-sync/what-is-sharinpix-image-sync.md)

For steps on how to activate the SharinPix Image Sync on an object, refer to this article:[ Setup SharinPix Image Sync](../image-sync/setup-sharinpix-image-sync.md)
{% endhint %}

## Configure the SharinPix Mobile Launcher component to retrieve the mobile user information

{% hint style="success" %}
**Tip:**

For more details on the SharinPix Mobile Launcher component, refer to this documentation: [SharinPix Mobile Launcher](../lightning-web-component/sharinpix-mobile-launcher.md)
{% endhint %}

To retrieve the mobile user that performed the upload using the SharinPix Mobile Launcher component, create a Screen Flow embedding the component as explained below:

1\. Create a Screen Flow

2\. Create a new Flow variable to retrieve the current record ID as follows:

* Under the Manager tab, click on the **New Resource** button and fill in the fields as follows:
* Resource Type: **Variable**
* API Name: **recordId**
* Description: Variable storing the current record ID.
* Data Type: **Text**
* Default Value: Select **{!$GlobalConstant.False}**
* Availability Outside the Flow: **Check Available for input**

![](<../.gitbook/assets/Screenshot 2024-04-12 at 4.28.17 PM (1).png>)

3\. Next, add a **Screen** element after the _Start_ element.

4\. Configure the **Screen Properties** element as follows:

* Label: **screenMobileLauncher**
* Configure Header: Uncheck the **Show Header** checkbox
* Configure Footer: Uncheck the **Show Footer** checkbox

5\. Next drag and drop the **SharinPix Mobile Launcher** component onto the Screen and configure the component as indicated below:

* API Name: **mobileLauncher**
* Button Label: **Takes Photos**
* Album ID: **{!recordId}**
* Custom parameters: **user\_id={!$User.Id}**

{% hint style="info" %}
**Information:**

The value entered in the **Custom parameters** field keeps track of the current user using the _SharinPix Mobile Launcher_ component to upload photos. The user ID is stored as file metadata on the uploaded photo and is used to retrieve the name of the user who uploaded the photo.
{% endhint %}

\
6\. Configure all other SharinPix Mobile Launcher parameters as desired and click on **Done**.

![](<../.gitbook/assets/Screenshot 2024-04-12 at 4.39.02 PM (1).png>)

7\. **Save** and **Activate** the Flow when done.

<figure><img src="../.gitbook/assets/test (19).jpg" alt=""><figcaption></figcaption></figure>

8\. Next, add the Flow component on the desired record page using the Lightning App Builder. **Note:** Ensure that the **Pass record ID into variable** checkbox is checked.

<figure><img src="../.gitbook/assets/test (20).jpg" alt=""><figcaption></figcaption></figure>

{% hint style="success" %}
**Tips:**

* As the SharinPix Mobile Launcher component only work on mobile, it is a good practice to add a filter on the Flow to make the component only visible and accessible on the Salesforce mobile app.
* For end users to access the Flow, ensure that they have the Run Flows permission assigned to them. For more information on how to grant the Run Flows permission, refer to this Salesforce article: [Add Run Flows Permissions](https://help.salesforce.com/s/articleView?id=sf.wcc_setup_add_run_flows_perms.htm\&type=5)
{% endhint %}

#### Demo: See the Flow in Action <a href="#demo-see-the-flow-in-action" id="demo-see-the-flow-in-action"></a>

* On the Salesforce mobile app, tap on the SharinPix Mobile Launcher component embedded to open the SharinPix mobile app. In our case, it is the **Take Photos** button below

<figure><img src="../.gitbook/assets/test (21).jpg" alt=""><figcaption></figcaption></figure>

* Upload some photos on the SharinPix mobile app.

<figure><img src="../.gitbook/assets/test (22).jpg" alt=""><figcaption></figcaption></figure>

* Once the upload is completed, go to the related SharinPix Image record for the photo. The username of the mobile user who uploaded the photo is available in the field **Uploaded By (Mobile User)**.

![](<../.gitbook/assets/Screenshot 2024-04-12 at 5.28.49 PM (1).png>)

## Configure a deeplink to retrieve the mobile user information

{% hint style="info" %}
This section demonstrates how to configure a SharinPix deeplink to keep track of the mobile user uploading photos.

As this is a common Salesforce Field Service (SFS) use case, this section will focus on a SFS-oriented implementation. **Please note that a similar implementation can be applied to a non-SFS context.**
{% endhint %}

{% hint style="info" %}
For this demo, we will use the Work Order object.
{% endhint %}

To capture the username of the field service mobile user opening the SharinPix mobile app to upload photos, proceed as follows:

1\. Create a Flow of type **Field Service Mobile Flow**.

2\. Go to the **Manager** tab and click on **New Resource**.

* Resource Type: **Variable**
* API Name: Enter **Id**
* Data Type: Text
* Default Value: **{!$GlobalConstant.EmptyString}**
* Availability Outside the Flow: **Available for input**
* Click **Done**

3\. Go to the **Manager** tab again and click on **New Resource**.

* Resource Type: **Variable**
* API Name: **WorkOrderRecord**
* Data Type: **Record**
* Object: **Work Order**
* Click **Done**

4\. Add a **Get Records** element under the _Start_ element. Configure the Get Records element as follows:

* Label: **lookupWorkOrder**
* Object: **Work Order**
* Conditions: **Id** (Field) equals (operator) **{!Id}** (newly-created resource named Id)
* In the **How Many Records to Store**, check the **Only the first record** option
* In the **Where to Store Field Values**, check the **Together in a record variable** option
* Then in the **Select Variable to Store Work Order** section, use the **WorkOrderRecord** variable for the **Record** field
* In the **Select Work Order Fields to Store in Variable** section, click on **Add Field** and select the token field, that is, **SharinPix\_Token\_\_c** for this demo
* Click **Done**

5\. Go to the Manager tab and click on New Resource:

* Resource Type: **Variable**
* API Name: **Launch\_SharinPix\_App**
* Data Type: **Text**
* Default Value: **\<a href="sharinpix://upload?token={!WorkOrderRecord.SharinPix\_Token\_\_c}\&user\_id={!$User.Id}">Take Photos\</a>**
* Click **Done**

6\. Go to the **Element** tab and add a **Screen** element after the _Get Records_ element. Configure the **Screen** element as follows.

* Label: **Mobile Launcher Screen**
* Add a **Display Text** component on the Screen.
* Label the _**Display Text**_ component as **sharinpixDeeplink**_**.**_<br>
* In the **Resource Picker** section, add the **Launch\_SharinPix\_App** variable.

7\. **Save** and **Activate** the Flow when done.

8\. Next, embed the Field Service Mobile Flow in an App Extension as demonstrated below.

<figure><img src="../.gitbook/assets/test (23).jpg" alt=""><figcaption></figcaption></figure>

{% hint style="success" %}
**Tip:**

For more information on how to embed a Field Service Mobile Flow in an App Extension, refer to the following link: [Creation of an App Extension embedding a Field Service Mobile Flow](../integrations/salesforce-field-service/integration-of-sharinpix-app-with-sfs-fsl-app-using-app-extension.md#creation-of-an-app-extension-embedding-a-field-service-mobile-flow)
{% endhint %}

### Demo: See the Field Service Mobile Flow in Action

* On the Field Service Mobile app, open the Flow action

<figure><img src="../.gitbook/assets/test (29).png" alt=""><figcaption></figcaption></figure>

* You are now inside the Flow. Select **Take Pictures** to launch the SharinPix app and upload photos.

<figure><img src="../.gitbook/assets/test (30).png" alt=""><figcaption></figcaption></figure>

* Once the upload is completed, go to the related SharinPix Image record for the photo. The username of the mobile user who uploaded the photo is available in the field **Uploaded By (Mobile User)**.

![](<../.gitbook/assets/Screenshot 2024-04-12 at 5.28.49 PM (1).png>)
