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

# I got an error 'Visit: id value of incorrect type: \[sharinpix\_\_Visit\_\_c]. What should I do?

If you encounter an error message similar to: <mark style="color:$danger;">`Upsert failed. First exception on row 0; first error: FIELD_INTEGRITY_EXCEPTION, Visit: id value of incorrect type: <record>: [sharinpix__Visit__c]`</mark> or if the image sync feature is not working as expected on the Visit object, this may be due to a mismatch between the standard Salesforce Visit object and the SharinPix Visit object.

Such mismatch usually occurs when the fields with the same API name exist on both the standard and SharinPix Visit objects.

For example, having Visit\_\_c on the standard object and sharinpix\_\_Visit\_\_c on the SharinPix Visit object may cause a mismatch in the image sync configuration.

Kindly note that in such cases, the **sharinpix** namespace is ignored.



To avoid such mismatch, ensure that no two field API names are added on both objects. In image sync configurations, for instance, this can be done by changing the field API names on the SharinPix Visit object so as it doesn't match any existing field API names on the standard Visit object.

{% hint style="success" %}
**Tip:**

If the issue still persists after applying the above workaround or if you need further assistance to resolve such issue, kindly contact SharinPix support on **support@sharinpix.com**.
{% endhint %}
