# My integration doesn't work on SFS (FSL)/ I got an invalid token error message on SharinPix mobile app. What should I do ?&#x20;

{% hint style="info" %}
**Information:**

Salesforce Field Service (SFS) was formerly known as Field Service Lightning (FSL).
{% endhint %}

If you are encountering issues with your SFS integration such as:

* The App Extension not showing up on the SFS mobile app
* Or having an invalid token error message upon launching the SharinPix app

here are some guidelines on how to fix them.

## App Extension not working as expected

* If the App Extension is not available in the SFS app, this might be due to the type specified in the App Extension detail. For example, if the App Extension is of type Android, it will not be visible on iOS devices and vice versa. Therefore, if you intend to use the App Extension on iOS devices the type specifed in the App Extension detail should be **iOS**. The same procedure applies for Android devices.
* If your App Extension is not available on a specific object, you should firstly check if your App Extension is available globally. To do so, remove the value entered in the field **Scoped To Object Types** in the App Extension detail. Leave the field blank and click **Save**. Next, open the SFS app, select any record then select **Show Actions**. Under the **App Extensions** section, check if your App Extension is available.

If you can view and access your App Extension this might be an indication that the value previously entered in the **Scoped To Object Types** field was wrongly typed.

To be able to access the App Extension on a specific object, you must ensure that the object's API name is correctly entered in the **Scoped To Object Types** field.

For example, if you intend to use the App Extension on the Work Order object, the value to be entered in the **Scoped To Object Types** field is **WorkOrder** as shown below:

![](<.gitbook/assets/image - 2026-01-28T164047.558.png>)

### Fixing the 'Invalid Token Error' message

The screenshot below depicts the error message obtained when the token is invalid:

![](<.gitbook/assets/image - 2026-01-28T164132.250.png>)

The **Invalid Token Error** message might be caused due to:

* An incorrect deeplink syntax.
* An empty value for the token
* An access to the token field prohibited for the user running SFS mobile App

The deeplink entered in the **Launch Value** field varies depending on whether the App Extension is intended to be used on iOS devices or Android devices.

![](<.gitbook/assets/image - 2026-01-28T164239.839.png>)

If you intend to use the App Extension on iOS devices, the field **Type** should have the value **iOS** and the field **Launch Value** should have the following deeplink syntax:

```
sharinpix://upload?token={!$SharinPix_Token__c}
```

Else, if you intend to use the App Extension on Android devices, the field **Type** should have the value **Android** and the field **Launch Value** should have the deeplink syntax that follows:

```
sharinpix://upload?token={!SharinPix_Token__c}
```

{% hint style="success" %}
**Tip:**

For iOS, notice the presence of a '$' symbol just before the SharinPix\_Token\_\_c field in the deeplink. For Android on the other hand, no '$' symbol is used.

For more information about you may refer to the following article:

[SharinPix mobile App : Deeplink syntax](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/mobile-app/sharinpix-mobile-app-deeplink-syntax)
{% endhint %}

* No access to the token field

In this case, the user might not have access to the token field used in the deeplink. To be able to properly launch the SharinPix app from the SFS app, you must ensure that users have access to the token field.

* The token field API name is incorrect

If the token field API name is not typed correctly inside the deeplink, this will result in an invalid token error message.

* The token generated is not in the correct format

Assuming that the user have access to the token field and that the deeplink syntax is correct, the invalid token error message might occur due to a blank or incorrect token. In this case, you should:

1. Ensure that a token value is inserted in the corresponding token field.
2. If yes, you should verify the token value. To do so, you can make use of the JWT debugger to decode the token by following the steps below:
   * Copy the record's token value. This can be found in the token field
   * Open a new Tab and type **jwt.io** in the address bar
   * In the **Encoded** box, delete the existing content and paste the token value
   * The decoded token can be seen inside the **Decoded** box just under the **PAYLOAD:DATA** section as shown below:

![](<.gitbook/assets/image - 2026-01-28T164322.413.png>)

* You can now cross-check the token's content inside the payload and look for any anomaly. Some point that need to be verified are:
  * If the token contains the correct record ID:

![](<.gitbook/assets/image - 2026-01-28T164407.749.png>)

* The list of abilities applied in the token:

![](<.gitbook/assets/image - 2026-01-28T164455.565.png>)

By decoding the token, it is easier to find any anomaly in the its content so as to fix the token generated accordingly.
