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

# Your personalized command

SharinPix allows for personalized commands, in other words you can perform your custom actions on selected images.

{% hint style="info" %}
This article's code can be easily deployed to your org from [this URL](https://github.com/SharinPix/demo-apex/tree/action_email/).
{% endhint %}

**In this article we will be setting up a Visual Force page on Salesforce with a custom action "Send Email"**

Add the SharinPix Visualforce component in your Visualforce page using the code snippet below:

```
    <SharinPix:SharinPix height="500px" parameters="{! parameters }"/>
```

Once done, ensure your "apex:page" has an extension apex class with a "parameters" as follows

```apex
Map<String, Object> params = new Map<String, Object> {
	'Id' => stdCtrl.getId(),
    'abilities' => new Map<String, Object> {
        stdCtrl.getId() => new Map<String, Object> {
            'Access' => new Map<String, Object> {
                'see' => true,
                'image_list' => true,
                'image_upload' => true,
                'image_delete' => true,
                'image_crop' => true,
                'image_rotate' => true
            },
            /*******************************************/
            /* ADD CUSTOM ACTIONS IN THE `Actions` KEY */
            /*******************************************/
            'Actions' => new List<String> {
                'Send an email'
            }
        }
    }
};
parameters = JSON.serialize(params);
```

The above code will add the "Send an email" action to the SharinPix widget.\
Now we need to listen when the action is fired.

Add the following script to your Visual Force page.

<pre class="language-apex"><code class="lang-apex"><strong>var eventMethod = window.addEventListener ? "addEventListener" : "attachEvent";
</strong>var eventer = window[eventMethod];
var messageEvent = eventMethod == "attachEvent" ? "onmessage" : "message";
eventer(messageEvent, function(e) {
    if (e.origin !== "https://app.sharinpix.com") return;
	if (e.data.payload.action == 'Send an email') {
    	/*************************************************/
    	/* HERE WE WILL HANDLE THE `Send an email` EVENT */
    	/*************************************************/
    }
}, false)
</code></pre>

At this point, we need to send a request to the server (Apex Class) to send the email with the following pictures in the body.

```apex
if (e.data.payload.action == 'Send an email') {
    /*************************************************/
    /* HERE WE WILL HANDLE THE `Send an email` EVENT */
    /*************************************************/
    Visualforce.remoting.Manager.invokeAction(
    	'{! $RemoteAction.SharinPixDemoActionEmailCtrl.sendMail }',
    	JSON.stringify(e.data.payload.images),
    	function(res) {
    		alert('Email(s) have been sent.');
    	}
    );
}
```

Above we invoked a remote apex action.\
Now we will need to perform the send email action in the apex controller.

```apex
@RemoteAction
global static void sendMail(String imageJson) {
    List<Object> imageList = (List<Object>)JSON.deserializeUntyped(imageJson);
    List<String> imageUrlList = new List<String>();
    String contactId;
    for (Object img : imageList) {
        Map<String, Object> imgMap = (Map<String, Object>)img;
        Map<String, Object> thumbnailMap = (Map<String, Object>)imgMap.get('thumbnails');
        imageUrlList.add(String.valueof(thumbnailMap.get('mini')));
        contactId = String.valueof(imgMap.get('album_id'));
    }

    List<Messaging.SingleEmailMessage> mails = new List<Messaging.SingleEmailMessage>();

    Contact contact = [SELECT Id, Name, Email FROM Contact Where Id = :contactId LIMIT 1];
    if (!imageUrlList.isEmpty()) {
        Messaging.SingleEmailMessage mail = new Messaging.SingleEmailMessage();
        mail.setToAddresses(new List<String> { contact.Email });
        mail.setReplyTo(UserInfo.getUserEmail());
        mail.setSenderDisplayName(UserInfo.getName());
        mail.setSubject('Photo Uploaded');

        String body = 'Hello ' + contact.Name;
        body += '<br/>The following photo(s) have been uploaded on your record:<br/>';
        for (String url : imageurllist) {
            body += '<img src="' + url + '" /><br/>';
        }
        mail.setHtmlBody(body);

        mails.add(mail);
    }
    Messaging.sendEmail(mails);
}
```

The above apex remote action sends an email with the selected picture's thumbnail to the Contact on which the Visualforce page is on.

Below is a glimpse of the end result.

![](<../../.gitbook/assets/image - 2026-02-05T164846.931.png>)

End result email:

![](<../../.gitbook/assets/image - 2026-02-05T164935.150.png>)
