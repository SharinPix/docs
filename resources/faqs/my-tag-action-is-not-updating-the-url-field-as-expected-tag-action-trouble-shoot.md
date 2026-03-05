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

# My Tag Action is not updating the URL field as expected (Tag Action Trouble Shoot)

Tag Action is the easiest way of obtaining a SharinPix image's URL and storing same in a Salesforce field.

Please find more about Tag Action [here](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/features/working-with-tags/tag-action).

If your Tag Action doesn't update the field as expected, you may have to check if you have one of those cases:

* You have not reloaded the page or haven't waited long enough for the Tag Action to be applied

Solution: Wait for the API call to finalize the modification. Reload the page after a longer delay

* You are using a VF page without the line which enables the Tag Action\
  Solution : add the following line on your Visualforce page:

**\<sharinpix:TagAction recordId="{!$CurrentPage.Parameters.Id}" />**

* You are using a Lightning Component without enabling the check box **Enable Action**\
  Solution : check the Enable Action box in the Lightning Component parameters through the Page Builder
* You don’t have the right to modify the record (record is locked, or the user don’t have an access to it)

Solution: unlock the record and retry

* You don't have edit access to the field being used to store the URL generated when performing the Tag Action.\
  Solution: give field edit access to the required user or profile.
* A validation rule is blocking the save of the record (you can check this by just trying to edit and save the record)\
  Solution: solve the validation rule and retry
* The field name used is not the API name (such as ImageURL\_\_c -> note the \_\_c at the end)\
  Solution: correct the field name on the Tag Action form the SharinPix Administration Dashboard. The best practice here is to copy and paste the field API name from Salesforce setup to be sure to use the good one
* Some users obtain an **Access Denied** error message while applying the Tag Action.\
  Solution: ensure that the option **Tag images** has been applied to the album. This can be done by either creating a SharinPix Permission record enabling the Tag images option or by enabling the Tag images option at an organisation level using the **SharinPix Global Administration**.

<figure><img src=".gitbook/assets/My Tag Action is not updating the URL field as expected (1).png" alt=""><figcaption></figcaption></figure>

* You are uploading images using the SharinPix mobile app and you have not set up the Tag Action workaround properly for this specific case.

{% hint style="warning" %}
**Note:**\
By default, the SharinPix Tag Action is not triggered when uploading images using the SharinPix mobile app.\
To enable the Tag Action feature when uploading images using the SharinPix mobile app, refer to the following article:\
[Tag Action does not work when uploading images using the SharinPix mobile app. What should I do?](tag-action-does-not-work-when-uploading-images-using-the-sharinpix-mobile-app-what-should-i-do.md)
{% endhint %}
