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

# SharinPix integration with TaskRay

The present article will outline the steps on how to integrate SharinPix within TaskRay **without** an Apex Class Controller. To be more precise, a new custom tab will be added to the task modal and the SharinPix album will be added to the Task pane. The final result is shown below.

<figure><img src="../../.gitbook/assets/image (1) (4).png" alt=""><figcaption></figcaption></figure>

{% hint style="success" %}
**Install TaskRay**

The following link will guide you towards the installation instructions for the TaskRay package: [instructions](https://support.taskray.com/hc/en-us/articles/115000175568).
{% endhint %}

## Visualforce Integration

1. From Setup, navigate to:
2.
   * **Lightning**:  Custom Code | Visualforce Pages
   * **Classic**:  Develop | Visualforce Pages

Click on New. Inside the label field enter SampleSharinPixPage. Paste the code below.

```apex
    <apex:page >
        <SharinPix:SharinPix height="500px" 
                             parameters="{
                             	'Id': '{!$CurrentPage.parameters.Id}', 
                                'abilities':{'{!$CurrentPage.parameters.Id}':{
                                'Access': {
                                	'image_upload':true,
                                    'image_list':true,
                                    'see':true,
                                    'image_delete':true
                                    }
    							  }
    						    }
                             }"
    	/>
    </apex:page>
```

## Add Custom Tab

**Add Custom Tabs to Project and Task Panes \[Admin]**

To configure custom tabs on Project or Task Details, you will be required to access TaskRay Global Settings and fill two fields: (1) a field containing the label of the tab (2) a field containing the URL of the Visualforce page being referenced inside the Task Pane.

1. From Setup, navigate to:
2.
   * **Lightning**: Custom Code | Custom Settings&#x20;
   * **Classic**: Develop | Custom Settings&#x20;
3. Click Manage next to TaskRay Global Settings.
4. Click on Edit inside the TaskRay Global Settings view.

Locate the Task Modal Custom Tab 1 Label.

<figure><img src="../../.gitbook/assets/image (64).png" alt=""><figcaption></figcaption></figure>

5\. Enter the label of the Custom tab. In our case it should be **SharinPix**.

<figure><img src="../../.gitbook/assets/image (65).png" alt=""><figcaption></figcaption></figure>

6\. Locate the Task Modal Custom Tab 1 URL. Enter the URL of the Visualforce page you want to reference within the Task Details pane. In this case, we will reference the Visualforce page we created in the previous section.

<figure><img src="../../.gitbook/assets/image (66).png" alt=""><figcaption></figcaption></figure>

You can refer to this article for the URL: [TaskRay Custom URL](https://support.taskray.com/hc/en-us/articles/115014930587-Add-Custom-Tabs-to-Project-and-Task-Details-Panes)

The symbol $id refers to the identifier for the current task being viewed. In our case, it will allow us to display the images relevant/belonging only to this task. The id symbol refers to any arbitrary value containing the value for $id.

7\. Finally click on Save.

8\. Access the TaskRay app and select the TaskRay tab.

9\. Create a new Project.

10\. Enter a name for the project. Click on Save & Close.

11\. Add new task.

12\. Click on New Task. When the modal appears, click on Save.

13\. Select the SharinPix tab.

<figure><img src="../../.gitbook/assets/image (67).png" alt=""><figcaption></figcaption></figure>

15\. The SharinPix album appears.

<figure><img src="../../.gitbook/assets/image (68).png" alt=""><figcaption></figcaption></figure>
