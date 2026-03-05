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

# SharinPix WebView on a Native iOS Mobile Application

A WebView (or WKWebView on iOS) is a component inside a Swift application which allows the display of a web app inside a mobile application. By running the SharinPix web app inside a WebView, your native Swift application will contain the SharinPix experience usually available on Salesforce and the web. It can be seen as the equivalent of an iframe tag in HTML.

{% hint style="info" %}
* The folks at AppCoda have a [simple tutorial](https://www.appcoda.com/swiftui-wkwebview/) on how to include a basic WebView in your application. You can follow it and try embedding SharinPix in your own app.
* You have to use the link **https://app.sharinpix.com/?token=XXXXX** in your created WebView with a generated token.
{% endhint %}

Below is an example how to generate token:

```apex
    token = sharinpix.Client.getInstance().token(
                    new Map<String, Object> {
                        'Id' => wOrder.Id,
                        'exp' => 0,
                        'path' => '/pagelayout/' + wOrder.Id,
                        'abilities' => new Map<String, Object> {
                            wOrder.Id => new Map<String, Object> {
                                'Access' => new Map<String, Boolean> {
                                    'see' => true,
                                    'image_list' => true,
                                    'image_upload' => true,
                                    'image_delete' => true
                                }
                            },
                            'Display' => new Map<String, Object> {
                                'tags'=> true
                            }
                        }
                    }
                );
                if (Trigger.isInsert) {
                    updatedWOrders.add(new WorkOrder(
                        Id = wOrder.Id,
                        SharinPix_Token__c = token
                    ));
                } else {
                    wOrder.SharinPix_Token__c = token;
                }
```

## Example of a WebView with the link

```swift
    import SwiftUI
    import WebKit
     
    struct WebView: UIViewRepresentable {
     
        var url: URL = URL(string: "https://app.sharinpix.com/?token=XXXXX")!;
        var webViewController: WebViewController = WebViewController()
     
        func makeUIView(context: Context) -> WKWebView {
            return WKWebView()
        }
     
        func updateUIView(_ webView: WKWebView, context: Context) {
            let contentController = webView.configuration.userContentController
            contentController.add(webViewController, name: "sharinpixOnEvent")
            let request = URLRequest(url: url)
            webView.load(request)
        }
    }
```

## ContentController

{% hint style="info" %}
* You have to add a **contentController** to listen to all events/post messages sent by the SharinPix application.
* The **WebViewController** should be added.
{% endhint %}

### Example of a ContentController

```apex
    let contentController = webView.configuration.userContentController;
    contentController.add(webViewController, name: "sharinpixOnEvent");
```

## Example of a WebViewController

```apex
    class WebViewController: NSObject, WKScriptMessageHandler, WKNavigationDelegate {
        func userContentController(_ userContentController: WKUserContentController, didReceive message: WKScriptMessage) {
            let dict = message.body as? NSDictionary
            print(dict ?? "SharinPix null")
            guard let string = dict?["name"] as? String else { return }
            print("SharinPix: " + string)
            showAlert(message: string)
        }
        .
        .
        .
    }
```

{% hint style="success" %}
The WebViewController class will allow the Swift application to get every event that is sent by the SharinPix application
{% endhint %}

## iOS Permissions

### Accessing the native camera

To be able to open the native camera on your Swift application, you should include the permission "**Privacy - Camera Usage Description (NSCameraUsageDescription)**" in Info in your XCode project.

If the permission is not allowed hence the user will not get the native camera.

* Go to your XCode Project
* Click on the project
* Click on Info
* Add a new property by clicking on the arrow **up down** on the permission "**Privacy - Camera Usage Description**" (See screenshot below).

<figure><img src="../../.gitbook/assets/image (96).png" alt=""><figcaption></figcaption></figure>

Below is the screenshot where the Permission **Privacy - Camera Usage Description** is asked.

<figure><img src="../../.gitbook/assets/image (101).png" alt=""><figcaption></figcaption></figure>

The screenshot below shows images that are uploaded on the SharinPix application.

<figure><img src="../../.gitbook/assets/image (102).png" alt=""><figcaption></figcaption></figure>

The screenshot shows a native alert being shown on the mobile application with the event that has been triggered when deleting an image on the SharinPix application.

<figure><img src="../../.gitbook/assets/image (103).png" alt=""><figcaption></figcaption></figure>
