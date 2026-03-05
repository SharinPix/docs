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

# SharinPix Related Record Albums component is not displaying any records. What should I do?

![](<.gitbook/assets/image (11).png>)

If your SharinPix Related Record Albums component is not displaying any records **(**&#x61;s depicted above), this most probably means that either:

1. The value entered in the **Related Object Field API Name** parameter is incorrect or does not exist for the  object specified in the **Related Object** parameter
2. Or the current record has no related records of the object specified in the **Related Object** parameter.



The **Related Object Field API Name** specifies the field name of the related records to be displayed. In the component's parameters, this value is set to the **Name** field by default.&#x20;

If the related object chose in **Related Object** parameter does not have any field API name set to the default value, Name, no records will be displayed on the component. In such cases, the default 'Name' value in the **Related Object Field API Name** parameter should be changed to the field API name of your choice.

{% hint style="danger" %}
**Note:**&#x20;

1. The field API name entered in the **Related Object Field API Name** paremeter should be available on the object chosen in the **Related Object** parameter and should be entered correctly for the records to be displayed as expected on the component.
2. &#x20;If no records are displayed on the component despite using correct values in both the **Related Object** and **Related Object Field API Name** parameters, verify if the current record has related records of the object specified in the **Related Object** parameter.
{% endhint %}
