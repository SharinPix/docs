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

# SharinPix WebView on a Native Android Mobile Application

A WebView is a component inside a Java Android application which allows the display of a web app inside a mobile application. By running the SharinPix web app inside a WebView, your native Java Android application will contain the SharinPix experience usually available on Salesforce and the web. It can be seen as the equivalent of an iframe tag in HTML.

{% hint style="info" %}
* The folks at AppCoda have a [simple tutorial](https://www.javatpoint.com/android-webview-example) on how to include a basic WebView in your application. You can follow it and try embedding SharinPix in your own app.
* You have to use the link \*\*https://app.sharinpix.com/?token=XXXXX \*\*in your created WebView with a generated token.
{% endhint %}

Below is an example of a apex code:

```apex
    token = sharinpix.Client.getInstance().token(
        new Map<String, Object> {
            'Id' => wOrder.Id, //example of an albumId
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
```

## Example of a SharinPixWebView with the link

The code below demonstrates how to create a **SharinPixWebView** using the **onCreate** method in the activity.

It sets a listener **setOnResultListener** to check all the returning results from the **SharinPixWebView** controller. Based on this example when a result is returned, a popup/toast is shown.

In the **onActivityResult** method, it sends the activity results to the **SharinPixWebView** controller.

```apex
    public class MainActivity extends AppCompatActivity {
       private ActivityMainBinding binding;
       private SharinPixWebView sharinPixWebView;
    
       @Override
       protected void onCreate(Bundle savedInstanceState) {
           super.onCreate(savedInstanceState);
           binding = ActivityMainBinding.inflate(getLayoutInflater());
           setContentView(binding.getRoot());
           this.sharinPixWebView = new SharinPixWebView(MainActivity.this, R.id.webView, "https://app.sharinpix.com/?token=XXXXX");
           this.sharinPixWebView.setOnResultListener(new SharinPixWebView.OnResultListener() {
               @Override
               public void onResult(JSONObject jsonObject) throws JSONException {
                   Toast.makeText(getApplicationContext(), jsonObject.getString("name"), Toast.LENGTH_LONG).show();
               }
           });
       }
    
       @Override
       protected void onActivityResult(int requestCode, int resultCode, @Nullable Intent data) {
           super.onActivityResult(requestCode, resultCode, data);
           this.sharinPixWebView.onActivityResult(requestCode, resultCode, data);
       }
    }
```

## Steps for Installing SharinPixWebView Library

In settings.gradle include this line:

```apex
    dependencyResolutionManagement {
        repositoriesMode.set(RepositoriesMode.FAIL_ON_PROJECT_REPOS)
        repositories {
            .
            .
            .
            mavenCentral()
        }
    }
```

In build.gradle for your project module include this line:

```apex
    dependencies {
        implementation 'io.github.SharinPix:sharinpixwebview-android:LATEST_VERSION'
    }
```

Check for latest release on GitHub or Maven Central Repository Search: [https://github.com/SharinPix/sharinpixwebview-android](https://github.com/SharinPix/sharinpixwebview-android) or [https://search.maven.org/artifact/io.github.SharinPix/sharinpixwebview-android](https://search.maven.org/artifact/io.github.SharinPix/sharinpixwebview-android)

## Example for Overriding the onActivityFunction Function

Make sure to override the onActivityResult function in your activity and pass the parameters to the custom function on SharinPixWebView.

```apex
    @Override
    protected void onActivityResult(int requestCode, int resultCode, @Nullable Intent data) {
       super.onActivityResult(requestCode, resultCode, data);
       this.sharinPixWebView.onActivityResult(requestCode, resultCode, data);
    }
```

## Example for Creating an Instance of SharinPixWebView

When creating a new instance of SharinPixWebView, you should pass the following parameter:

* Activity: _the main activity from which your WebView_
* WebView ID
* URL

```apex
    this.sharinpixWebView = new SharinPixWebView(MainActivity.this, R.id.webView, "https://app.sharinpix.com/?token=XXXXX");
```

## Example for Implementing the SharinPixWebView Listener

To be able to receive post messages from the SharinPix application, make sure to implement the custom listener.

```apex
    this.sharinpixWebView.setOnResultListener(new SharinPixWebView.OnResultListener() {
       @Override
       public void onResult(JSONObject jsonObject) throws JSONException {
           Toast.makeText(getApplicationContext(), jsonObject.getString("name"), Toast.LENGTH_LONG).show();
       }
    });
```

The screenshot below shows images that are uploaded on the SharinPix application.

<figure><img src="../../.gitbook/assets/image (1) (5).png" alt=""><figcaption></figcaption></figure>

The screenshot shows a native toast being shown on the mobile application with the event that has been triggered when deleting an image on the SharinPix application.

<figure><img src="../../.gitbook/assets/image (95).png" alt=""><figcaption></figcaption></figure>
