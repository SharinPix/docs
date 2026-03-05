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

# I got a Google Map error, what should I do?

![](<.gitbook/assets/image (2).png>)

If you ever encounter the above pop-up error message and/or the text '**For development purposes only**' displayed on your SharinPix Map, you should check the Google Developer Tools' console for more details about the error. Solutions to such issues are usually available from the console as well.

To access the console:

1. either use to command **Ctrl + Shift + I** to activate it or right-click and select **Inspect**
2. then, click on the **Console** tab as depicted below:

![](<.gitbook/assets/image (3).png>)

The error message shall be highlighted in red on the console tab.

Additionally, details on how to address the issue will generally appear on the console.



One common error is as follows: **“You must enable Billing on the Google Cloud Project"**

This is because Billing has not been enabled on the Google Cloud Project.

To solve this, enable Billing at [**https://console.cloud.google.com/project/\_/billing/enable**](https://console.cloud.google.com/project/_/billing/enable)

You can learn more at [**https://developers.google.com/maps/gmp-get-started**](https://developers.google.com/maps/gmp-get-started)
