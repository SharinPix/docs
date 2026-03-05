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

# Restrict Uploads Using File Extensions

This article demonstrates how to restrict file uploads based on file extensions.

Uploads can be restricted as follows:

* [Using a SharinPix Permission record to specify the list of accepted file extensions.](restrict-uploads-using-file-extensions.md#using-sharinpix-permission-records)
* [Using an Apex method to generate an online token with a list of accepted file extensions.](restrict-uploads-using-file-extensions.md#using-the-upload_accept-parameter-in-apex-method)

## Using SharinPix Permission Records

SharinPix Permission records consist of the **Accepted file types** parameter used to specify the type of files that can be uploaded to an album.

The **Accepted file types** parameter takes as a value the list of accepted file extensions separated by a semi-colon.

For example, to restrict uploads to .jpeg, and PDF files, the value will be as follows: <mark style="color:$danger;">`.jpeg;application/pdf`</mark>

![](../../.gitbook/assets/7069a577-b5c5-48b8-b0ed-2ff9e0d7f203.png)

{% hint style="success" %}
**Tips:**

* The **application/pdf** extension is used in the **Accepted file types** parameter to enable the upload of PDF files.
* For more information on how to create and assign SharinPix Permission, refer to this article: [SharinPix Permission object](../../access-and-security/sharinpix-permission-object-how-to-create-and-assign-custom-permission.md)
{% endhint %}

## Using the upload\_accept parameter in Apex Method

Online tokens can be used to restrict uploads based on file extensions using the <mark style="color:$danger;">`upload_accept`</mark> parameter that specifies the type of files that can be uploaded to an album.

For example, to restrict uploads to .png and .jpeg files, the value will be as follows:

<mark style="color:$danger;">`'upload_accept' => new List <String> { '.png', '.jpeg' }`</mark>

The following code snippet demonstrates how to generate an online token with the `upload_accept` parameter.

```
public String generateToken(Id recordID) {
  sharinpix.Client clientInstance = sharinpix.Client.getInstance();
  String token = clientInstance.token(
      new Map<String, Object> {
          'Id' => recordID,          
          'upload_accept' => new List <String> { '.png', '.jpeg' },
          'path' => '/pagelayout/' + recordID,
          'abilities' => new Map<String, Object> {
              recordID => new Map<String, Object> {
                  'Access' => new Map<String, Boolean> {
                      'see' => true,
                      'image_list' => true,
                      'image_upload' => true
                  }
              }
          }
      }
  );
  return token;
}
```

{% hint style="success" %}
**Tip:**

For more information on the common uses of online tokens and how they can be generated, refer to this article: [Online token generation methods](../../access-and-security/online-token-generation-methods.md).
{% endhint %}
