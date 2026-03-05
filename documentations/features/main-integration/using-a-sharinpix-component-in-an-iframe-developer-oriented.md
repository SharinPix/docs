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

# Using a SharinPix component in an Iframe (Developer-oriented)

In this article, you will learn:

* [The Iframe syntax used by SharinPix](using-a-sharinpix-component-in-an-iframe-developer-oriented.md#iframe-syntax-used-by-sharinpix)
* [How to create a Visualforce page that contains an Iframe embedding the SharinPix component](using-a-sharinpix-component-in-an-iframe-developer-oriented.md#creating-the-visualforce-page)

## Iframe syntax used by SharinPix

SharinPix is flexible enough to be used in an Iframe. Traditionally, the Iframe syntax used to embed a SharinPix component was as follows:

```html
<apex:page standardController="Account" extensions="GetToken">    
    <iframe id="iframeId" class="sharinpix-iframe" src="https://app.sharinpix.com/?token={! SharinPixToken }"></iframe>
</apex:page>
```

However, some iOS devices encountered a cookie issue when using this syntax as depicted in the image below:

![](<../../.gitbook/assets/image (18) (1) (1).png>)

To bypass this issue, SharinPix made use of the **postMessage** method (a method that ensures cross-document messaging between two domains) to send the token to the SharinPix URL.

The postMessage method takes two arguments:

1. The data to be sent.
2. The domain to which you want to send the data. This domain is commonly referred to as the **target origin**.

In the following section, you will learn how a SharinPix component can be embedded in an Iframe using the **postMessage** method. To demonstrate this, we will:

* Create an Apex method that generates the token.
* Create a Visualforce page that:
  1. Embeds an Iframe containing the SharinPix URL and a reference to the postMessage method.
  2. Invokes the Apex method to retrieve the token.

## Creating the Visualforce page

{% hint style="warning" %}
**Note:** For this demo, we will use the Account object.
{% endhint %}

This section shows how to create the Visualforce page that will:

* Embed an Iframe.
* Invoke the newly-created method that returns a token.
* Use the postMessage method to send the retrieved token to the target origin.

Firstly, create an Apex Class containing a method that generates a token and returns same using the code snippet below:

```apex
global with sharing class GetToken {
	public String currentRecordId {get;set;}
 
    public GetToken(ApexPages.StandardController controller) {
        currentRecordId  = ApexPages.CurrentPage().getparameters().get('id');
    }    
    
    @RemoteAction
    global static String generateToken(String recordId){
        String token;
        
        token = sharinpix.Client.getInstance().token(
                new Map<String, Object> {
                    'Id' => recordId,
                    'exp' => 0,
                    'path' => '/pagelayout/' + recordId,
                    'abilities' => new Map<String, Object> {
                        recordId => new Map<String, Object> {
                            'Access' => new Map<String, Boolean> {
                                'see' => true,
                                'image_list' => true,
                                'image_upload' => true,
                                'image_delete' => true
                            }
                        }
                    }
                }
            );
        return token;
    }
}
```

Now create the Visualforce page using the code snippet below:

```html
<apex:page standardController="Account" extensions="GetToken">
    
    <iframe id="iframeId" class="sharinpix-iframe" src="https://app.sharinpix.com/post_message" width="100%" height="100%"></iframe>
    
    <script>
    var iframe = document.getElementById('iframeId')
        iframe.onload = function() {
            Visualforce.remoting.Manager.invokeAction(
            "{! $RemoteAction.GetToken.generateToken }",
            "{!currentRecordId}",
             function(result, event) {
                if (event.status) {
                    iframe.contentWindow.postMessage({ token: result}, 'https://app.sharinpix.com');
                } else {
                    alert('Error. See console log.');
                    console.log('Result: ', result);
                    console.log('Event: ', event);
                }
             }
            );    
        }      
    </script>
</apex:page>
```

The newly-created Visualforce page consists of an Iframe embedding the SharinPix URL and a reference to the postMessage method.

Upon loading the Iframe, the Visualforce page will invoke the method **generateToken** from the class **GetToken** to retrieve the token.

```javascript
<script>
    var iframe = document.getElementById('iframeId')
        iframe.onload = function() {
            Visualforce.remoting.Manager.invokeAction(
            "{! $RemoteAction.GetToken.generateToken }",
            "{!currentRecordId}",
             function(result, event) {
                if (event.status) {
                    iframe.contentWindow.postMessage({ token: result}, 'https://app.sharinpix.com');
                } else {
                    alert('Error. See console log.');
                    console.log('Result: ', result);
                    console.log('Event: ', event);
                }
             }
            );    
        }      
</script>
```

The retrieved token will be then sent to the target origin using the postMessage method as shown in the code snippet below:

```javascript
iframe.contentWindow.postMessage({ token: result}, 'https://app.sharinpix.com');
```

### See the Iframe in Action

To access the SharinPix component from the Iframe, add the newly-created Visualforce page to an **Account** object.

![](<../../.gitbook/assets/image (19) (1) (1).png>)
