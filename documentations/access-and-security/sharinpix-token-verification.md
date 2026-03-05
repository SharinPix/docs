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

# SharinPix Token Verification

This article explains how to verify if a SharinPix Token is valid using an Apex method.

The following sections include:

* [Explanation of the validateToken method](sharinpix-token-verification.md#validatetoken-method)
* [A use case example demonstrating how to call the method in an apex class and validate a Visualforce site token.](sharinpix-token-verification.md#demo)

**For more information on SharinPix tokens, refer to this article:**[Working with SharinPix Tokens](../best-practices/working-with-sharinpix-tokens.md)

## validateToken Method

The <mark style="color:$danger;">`validateToken (String token)`</mark> method available in the <mark style="color:$danger;">`sharinpix.Client`</mark> class assesses the token's validity. It returns true if the token is valid and false otherwise.This method ensures that only valid and authentic tokens are used to access and upload SharinPix images. The code snippet below demonstrates how to use the validateToken method to validate a SharinPix Token.

### validateToken Method Example

_global void **verifyToken**(String **token**)_

```
Boolean isValid = sharinpix.Client.getInstance().validateToken(token);
System.debug('Token Valid: ' + isValid);
```

## verifyToken Method

The <mark style="color:$danger;">`verifyToken`</mark> method, used inside the <mark style="color:$danger;">`validateToken`</mark> method examines several criteria to ensure the validity of the provided token. It evaluates whether any exceptions should be thrown during the verification process.

### verifyToken Method Example

_global void**verifyToken**(String **token**)_

```
String errorMessage = '';

try {
    sharinpix.Client.getInstance().verifyToken(token);
    return true;
} catch(Exception error) {
    errorMessage = error.getMessage();
}
```

### Criteria for SharinPix Token Verification

The <mark style="color:$danger;">`verifyToken`</mark> method's validation process includes:

* Checking the expiration time (<mark style="color:$danger;">`exp`</mark>) to ensure it's later than the current timestamp, avoiding acceptance of expired tokens.
* Verifying the token issued time (<mark style="color:$danger;">`iat`</mark>) by ensuring that it is earlier than the current timestamp thus preventing acceptance of tokens issued in the future.
* Checking that the token is not null and does not have an invalid format.
* Most importantly, the token header is decoded and an error is thrown if the signature is invalid. This ensures that the token has been created with your credentials only and has not been tampered with.

## Demo

### Validate a SharinPix Token for a Visualforce Site

The sample code below demonstrates the use of the <mark style="color:$danger;">`validateToken`</mark> method for token validation within a Visualforce site. This method is important for ensuring the security and integrity of the authentication process on the Visualforce site.

#### Visualforce Page

```
<apex:page controller="SiteParameterValidateToken">
    <apex:outputPanel rendered="{! canAccessSite }">
        <!-- Component rendered only after Apex validates token. -->
        <p>Valid Token : {! canAccessSite }</p>
    </apex:outputPanel>
    <apex:outputPanel rendered="{! !canAccessSite }">
        <!-- Error message? Redirect? -->
        <p>Valid Token : {! canAccessSite }</p>
    </apex:outputPanel>
</apex:page>
```

#### Apex Class

```apex
public class SiteParameterValidateToken {
    public Boolean canAccessSite { get; set; }
    
    public SiteParameterValidateToken() {
        String token = ApexPages.currentPage().getParameters().get('token');
        canAccessSite = false;
        try {
            canAccessSite = sharinpix.Client.getInstance().validateToken(token); // the new method on SharinPix
        } catch (Exception e) {
            canAccessSite = false;
        }
    }
}
```
