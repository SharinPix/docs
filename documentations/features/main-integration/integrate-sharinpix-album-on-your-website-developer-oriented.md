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

# Integrate SharinPix Album on Your Website (Developer-oriented)

## Introduction

{% hint style="warning" %}
Please note that you will require developer skills to be able to integrate SharinPix Album on your Website.
{% endhint %}

In this document, we will guide you through the different element you need to do to display a SharinPix album on your website.

To get started, you need to generate a JSON Web token. Learn more here: [https://jwt.io/introduction](https://jwt.io/introduction)\
This is used to authenticate SharinPix Album. There are 4 main information required to display and interact a SharinPix Album.

* **AlbumId** - the album Id on which to upload images.
* **Issuer** - A key used to determine who is the owner and which organization the album and images belongs to.
* **Secret** - A secret which will sign the album (we use this to verify authenticity of the requests).
* **Abilities** - refers to the different permission granted to the current album

## Getting Started

{% hint style="info" %}
For this document, we will show you how to build a JWT in Javascript programming language. But this can be done similarly in any languages.
{% endhint %}

{% hint style="danger" %}
For security reasons, it is imperative that JWT (JSON Web Token) tokens are generated on the server side only. Generating JWT tokens on the client side can expose sensitive information and significantly increase the risk of unauthorized access and data breaches.

**Failure to comply with this guideline may result in security vulnerabilities and potential breaches of sensitive data.**
{% endhint %}

First, you need to create a SharinPix Secret. For that, you need to go the SharinPix Admin Dashboard and create the secret.

Connect to the Admin Dashboard: [Overview of the SharinPix Administration Dashboard](https://app.gitbook.com/s/2putv2B9RAZpym8daOH2/overview-of-the-sharinpix-administration-dashboard)

Go to the Secrets tab and create a new one.

![](<../../.gitbook/assets/image (14) (1).png>)

## Building Token

We shall now construct our token. You will now need to download the appropriate JWT library depending on the programming language you are using. As mentioned earlier, we will be using Javascript for this demo.

{% hint style="success" %}
Link to JWT libraries: [https://jwt.io/libraries](https://jwt.io/libraries)\
Installation instructions are also provided there.
{% endhint %}

Below is a sample javascript code. Import appropriate library before running the code. In this case, the library was <mark style="color:$danger;">`jsrsasign-all-min.js`</mark>.

```javascript
var albumId, base_url, client_id, client_secret, params, token;
albumId = 'my_album_id'; //replace with your album id
client_id = '1bf911ea-1fff-4917-8e9e-52061846543c'; //replace with your Id from your secret
client_secret = 'GGIVjB4KcMBxUajtLfCf_wxF4wcHFesBDCMykQdgPtUBoLs'; //replace with your secret
base_url = 'https://app.sharinpix.com/';

params = {
    iss: client_id,
    path: '/pagelayout/'+albumId,
    abilities: {}
};
params["abilities"][albumId] = {
    Access: {
        see: true,
        image_upload: true,
        image_delete: true,
        image_list: true
    }
};

token = KJUR.jws.JWS.sign(null, {
            alg: "HS256",
            cty: "JWT"
        },
        JSON.stringify(params), client_secret);
```

{% hint style="danger" %}
For demonstration purposes, the sample code above generates the token on the client side. As mentioned above, JWT (JSON Web Token) tokens should be generated on the server side. SharinPix already provides Apex methods to generate tokens; this is documented [here](../../access-and-security/online-token-generation-methods.md).
{% endhint %}

The above code generates a string like this:

eyJhbGciOiJIUzI1NiIsImN0eSI6IkpXVCJ9.eyJpc3MiOiIxYmY5MTFlYS0xZmZmLTQ5MTctOGU5ZS01MjA2MTg0Nj U0M2MiLCJwYiL3BhZ2VsYXlvdXQvbXlfYWxidW1faWQiLCJhYmlsaXRpZXMiOnsibXlfYWxidW1faWQiOnsiQWNjZ XNzIjp7InNlZSI6dHJ1ZSwiaW1hZ2VfdXBsb2FkIjp0cnVlLCJpbWFnZV9kZWxldGUiOnRydWUsImltYWdlX2xpc3 QiOnRydWV9fX19.qp7TqeGUPTKA1DsNaws70\_ml7SoJST9MR9A-6Duy1lE

## Displaying SharinPix Album

Now to display the SharinPix album on your html page, use the following below and insert the generated token.

```html
<iframe id="iframeId" class="sharinpix-iframe" src="https://app.sharinpix.com/post_message" width="100%" height="100%"></iframe>
    
<script>
    var token = "<your-generated-token>"
    var iframe = document.getElementById('iframeId')
    iframe.onload = function() {
        iframe.contentWindow.postMessage({ token: token}, 'https://app.sharinpix.com');
    }      
</script>
```

{% hint style="success" %}
Contact SharinPix support in case you are having difficulties implementing these.
{% endhint %}
