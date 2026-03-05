# SharinPix app link directs to Google Play Store instead of the SharinPix app on Android 12. What should I do?

The recent app verification changes made by Google on the latest Android versions may cause the SharinPix mobile app universal links starting with the following formats to not work as expected:

<mark style="color:$danger;">`https://app.sharinpix.com/native_app/upload?token=...`</mark>

<mark style="color:$danger;">`https://app.sharinpix.com/native_upload?token=...`</mark>

**Kindly note that this has already been resolved in the latest version of the app. Please update from the Google Play Store.**

Other workarounds to resolve this issue are to either:

1. Modify your implementation to use the SharinPix deeplink <mark style="color:$danger;">`sharinpix://upload?token=...`</mark> instead of the SharinPix universal link.
2.  Or change the SharinPix app settings on the user's device directly. This approach does not require changes to your current SharinPix implementation. To set up this workaround, follow the steps below:

    * On the user's device, open the **App info** for the SharinPix mobile app:

    <figure><img src=".gitbook/assets/test (7).png" alt=""><figcaption></figcaption></figure>



* Next, tap on **Open by default** :

<figure><img src=".gitbook/assets/test (8).png" alt=""><figcaption></figcaption></figure>

* Then, tap on **Add link** :

<figure><img src=".gitbook/assets/test (9).png" alt=""><figcaption></figcaption></figure>

* To finish, select **app.sharinpix.com** and choose **Add** :

<figure><img src=".gitbook/assets/test (10).png" alt=""><figcaption></figcaption></figure>

