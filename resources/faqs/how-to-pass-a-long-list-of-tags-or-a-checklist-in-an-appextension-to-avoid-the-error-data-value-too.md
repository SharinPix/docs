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

# How to pass a long list of tags or a checklist in an AppExtension to avoid the error "data value too large"?

These articles provide good practice as well as a workaround to the error message "data value too large". Your AppExtension will consist mainly of a **Token**.You can also add **Tags** and **Checklists**

Click [here](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/integrations/salesforce-field-service/integration-of-sharinpix-app-with-sfs-fsl-app-using-app-extension#creation-of-the-app-extension) to create an AppExtention.

Click [here](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/mobile-app/sharinpix-mobile-app-checklist) to learn more on Checklist.

{% hint style="warning" %}
**Note:**

This is a very common error while using AppExtension.\
This article documents a common error message when configuring SharinPix deeplinks with values greater than 255 characters.
{% endhint %}

The below screenshot shows you an example of the error:

![](<.gitbook/assets/1_1 (1).png>)

## How you should avoid creating AppExtension?

{% hint style="danger" %}
**Warning:**

The example below demonstrates a bad example of an AppExtension value.

<mark style="color:red;">`sharinpix://upload?token={!$SharinPix_Token__c}&checklist=Front_of_Home;Right_Side_of_Home;Left_Side_of_Home;Back_of_Home;Attic_Access;Inside_Attic;Rafter_Span;Rafter_Size;Rafter_Thickness;Roof_Slope;Main_Panel;Main_Panel_Up_With_Door_Open;Main_Service_Panel_With_Cover_Removed;Main_Service_Panel_Schedule;Main_Service_Panel_Breaker_Size;Main_Service_Panel_Breaker_Sizes_All;Label_of_Panels_Max_Busbar_Rating;Feeder_Sizes;Wire_Feeders;Utility_Meter_Up_Close;Utility_Meter_At_Distance;Conduit_Run_To_Meter_Location;Roof_Condition;Roof_Obstructions;Potential_Shading;Drone_Video`</mark>

The above demonstrates a SharinPix deeplink with a long checklist value. The AppExtenstion value in this case exceeds the maximum 255 characters allowed in an AppExtension value
{% endhint %}

## How to add Checklist in an AppExtension with a formula field?

* Create a Formula field of type text on the WorkOrder. For example **CheckListFormula\_\_c.**
* In the Formula field, **CheckListFormula\_\_c** , add the checklist value, that is the list of tags separated by a semi-colon. For example: "**Front-Door;Back-Yard;Entrance** "(Every values should be separate by a **;** )
* Once the Formula field is saved, copy its API name and paste it into the SharinPix deeplink value in the AppExtension

Here is an example of how to write AppExtension with a formula field:

```
sharinpix://upload?token={!$SharinPix_Token__c}&checklist={!$CheckListFormula__c}
```

{% hint style="success" %}
This also works with a field of type "**Long Text** ". See the below example.
{% endhint %}

## How to add Checklist in an AppExtension with a long text area field?

* Create a field of type Text Area (long). For example **TagList\_\_c.**
* In the text area field **TagList\_\_c** add the checklist value. The value should be separated by a semi-colon. For example: "**Front\_of\_Home" + ";" +"Right\_Side\_of\_Home" + ";" +"Left\_Side\_of\_Home** "

![](<.gitbook/assets/2_2 (1).png>)

Here is an example of how to write AppExtension with a long text area:

```
 sharinpix://upload?token={!$SharinPix_Token__c}&checklist={!$TagList__c}
```
