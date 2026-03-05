# I got an error message 'Webpage not available' when trying to launch the SharinPix mobile app. What should I do?

![](.gitbook/assets/1_1.png)

If you are encountering a 'Webpage not available' error message in a Salesforce webview as depicted above, this could be because you’re opening a SharinPix deeplink instead of a Universal Link. In some cases where a webview is used within the Salesforce app to display external web content, this behavior can be observed.

**The workaround is to use a SharinPix Universal Link instead.**

For example, the following deeplink example will not work on Salesforce webviews:

`sharinpix://upload?token`_`<Token Inserted Here>`_

It should be replaced by a Universal Link similar to one below:

`https://app.sharinpix.com/native_app/upload?token=`_`<Token Inserted Here>`_

**Tip:**

Deeplinks start with `sharinpix://`whereas Universal Links start with `https://app.sharinpix.com/native_app/`.

{% hint style="warning" %}
**Note:**

Salesforce webviews are usually opened

* Within a Community website on the Salesforce app when trying to launch the SharinPix app using a deeplink or any components used to open the SharinPix app such as the [SharinPix Mobile Launcher](https://app.gitbook.com/s/Hhhsz8OAg6xcF0k0DJhg/sharinpix-mobile-launcher).
* When a custom LWC is used to open a SharinPix deeplink.
{% endhint %}
