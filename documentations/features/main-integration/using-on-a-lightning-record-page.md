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

# Using on a Lightning Record Page

In this section, we will dive deeper into adding the SharinPix Album component on a record page.

To do so:

1. [Drag and drop SharinPix Album onto the record page](using-on-a-lightning-record-page.md#id-1.-drag-and-drop-the-sharinpix-album-on-the-record-page)
2. [Configure the SharinPix Album's parameters](using-on-a-lightning-record-page.md#id-2.-configure-the-sharinpix-albums-parameters)
3. [Tip: Add a custom tab to access the component quickly](using-on-a-lightning-record-page.md#id-3.-tip-add-a-custom-tab-to-access-the-component-quickly)

## 1. Drag and drop the SharinPix Album on the record page

To add the SharinPix Album component to your record page, open the Lightning App Builder from the record page as indicated below.

1. Click on the **Setup Icon**.
2. Select **Edit Page**.

![](<../../.gitbook/assets/image (21) (1).png>)

3\. From the **Lightning Components** list under the **Custom-Managed** section, select the **SharinPix Album** component.

4\. Drag and drop it onto the page.

{% hint style="warning" %}
**Note:**

If you can't see the SharinPix Album or any SharinPix components in the list of components, please ensure that you enable the My Domain on your organization.

For more information on how to enable My Domain, refer to this video: [https://salesforce.vidyard.com/watch/oFQ26FCXPVOA90xZaVDDjA](https://salesforce.vidyard.com/watch/oFQ26FCXPVOA90xZaVDDjA)
{% endhint %}

![](<../../.gitbook/assets/image (22) (1) (1).png>)

## 2. Configure the SharinPix Album's parameters

After dropping the **SharinPix Album** component on the desired region, configure its parameters as desired in the Ligning Component Parameters section on the right.

![](<../../.gitbook/assets/image (23) (2).png>)

You will find the description of each parameter below.

* **AlbumId:** Used to specify the album Id. If you want to use the record Id as the album Id, leave this field blank.
* **Height:** Used to specify the album's height. The default album height is **500** (px).
* **Use Fullscreen Image Viewer:** Used to enable/disable the option to view images in full screen.
* **Fullscreen Viewer Padding:** Used to add padding. The default value is **90px 0 0 0**.
* **Enable Action:** Used to enable/disable Tag Action. **Note:** The Tag Action is enabled by default on the SharinPix Album component. For more information on this feature and how to complete the Tag Action setup, refer to this article: [_Tag Action_](../working-with-tags/tag-action.md)
* **Enable Image Sync:** Used to enable/disable Image Sync. **Note:** Image Sync is checked by default on the SharinPix Album component. Additional steps are required to get this feature fully working on your Salesforce object. Please refer to this article to complete the Image Sync setup: _Setup_ [_SharinPix Image Sync_](../../image-sync/setup-sharinpix-image-sync.md)
* **Enable Toast:** Used to enable/disable toast message upon successful image upload.
* **Auto Refresh View:** Used to enable/disable the option to reload the view. **Note:** _This option is not supported in the Salesforce Community. When configured within a Community, it is advised to disable this option on the component._
* **Custom Permission Id or Name:** Used to specify the Id or Name of a custom permission.
* **Available Tags:** Used to specify a list of tag names delimited by a semi-colon. Example: TagA;TagB;TagC;
* **Auto Tags:** Used to specify a list of tags delimited by a semi-colon to apply to every image uploaded. Example: TagA;TagB;TagC;
* **Component ID:** Used to specify the component Id's to be matched by add-on components on a page.

## 3. Tip: Add a custom tab to access the component quickly

Create a custom tab on the Lightning App Builder to easily access the **SharinPix Album** component.

1. Click on **Add Tab.**
2. Then click on the newly created tab to rename it.
3. Open the **Tab Label** dropdown and select **Custom** from the list.
4. In the **Custom Tab Label** text box, enter the desired tab label, for example, _Photos_.

![](<../../.gitbook/assets/image (24) (2).png>)

5\. Click on the newly created custom Tab, in this case, the **Photos** tab.

7\. Drag and drop the **SharinPix Album** in the _Photos_ tab.

![](<../../.gitbook/assets/image (25) (2).png>)

8\. The **SharinPix Album** component is now available within the custom tab.

9\. Click **Save when done.**

10\. You can now start uploading photos!
