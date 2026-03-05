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

# I got the error 'You do not have sufficient access right to merge albums.' when using the SharinPix Merge Album component. What should I do?

If you encounter the error message **You do not have sufficient access right to merge albums. Please contact your System Administrator.** when using the SharinPix Merge Album component, here is what you can do:

1. Ensure that the user performing the merge action has been assigned to the SharinPix Lightning Components permission set.
2. If the above did not resolve the issue, ensure that the user has access to the source record.

{% hint style="warning" %}
**Note:**

If you are using a converted lead record as the source record, you should ensure that the user has view and edit access on the converted lead. Such access can be granted using the **View and edit converted lead records** permission using a Salesforce permission set.

For more information on how to grant the **View and edit converted lead records** permission, kindly refer to this Salesforce article:

[Let Users View and Edit Converted Leads](https://help.salesforce.com/s/articleView?id=sf.leads_view_edit_converted.htm\&type=5)
{% endhint %}
