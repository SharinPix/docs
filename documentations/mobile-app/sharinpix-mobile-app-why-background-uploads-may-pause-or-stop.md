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

# SharinPix Mobile App: Why Background Uploads May Pause or Stop

To ensure that your photos and files continue uploading even after you leave the app, follow these device-specific requirements. Mobile operating systems often restrict background activity to save battery, so these settings are necessary for a seamless experience.

### 1. iOS (iPhone & iPad)

On iOS, background tasks are heavily restricted. For uploads to succeed, the app must remain in a **Background** state but not a **Terminated** state.

{% hint style="danger" %}
**Prerequisites**:&#x20;

Do not "Force Quit" the app. If you swipe the app up and away in the App Switcher (the screen where you see all open apps), iOS immediately kills all active upload sessions.

Simply swipe to your Home Screen or switch to another app. The app will continue the upload in the background.
{% endhint %}

{% hint style="info" %}
**Tip:**

Ensure "Background App Refresh" is enabled in your device Settings for this app.
{% endhint %}

<figure><img src="../.gitbook/assets/Copy of DOC Mobile - 1920 x 1080.png" alt=""><figcaption></figcaption></figure>

### 2. Android

Android allows more flexibility, but many manufacturers (especially Samsung) use "Adaptive Battery" features that can put the app to sleep if it isn't used frequently.

Samsung Devices (Android 11, 12, 13+)

To prevent Samsung's optimization from stopping your uploads:

**Option A: Set Battery to Unrestricted**

1. Go to **Settings** > **Apps**.
2. Locate and select **SharinPix**.

<figure><img src="../.gitbook/assets/2 (10).png" alt=""><figcaption></figcaption></figure>

\
&#x20;    3\. Tap on **Battery**.

&#x20;    4\. Change the setting from "Optimized" to **Unrestricted**.

<figure><img src="../.gitbook/assets/3 (10) (1).png" alt=""><figcaption></figcaption></figure>

**Option B: Add to "Never Sleeping Apps"**

1. Go to **Settings** > **Battery and device care** > **Battery** > **Background usage Limit**

<figure><img src="../.gitbook/assets/4 (8).png" alt=""><figcaption></figcaption></figure>

&#x20;   2\. Tap **Never sleeping apps**.

<figure><img src="../.gitbook/assets/5 (7).png" alt=""><figcaption></figcaption></figure>

&#x20;   3.Tap the **+** icon, find **SharinPix**, and tap **Add**.

<figure><img src="../.gitbook/assets/6 (7).png" alt=""><figcaption></figcaption></figure>

### Other Android Devices (Google Pixel, Xiaomi, OnePlus) <a href="#other-android-devices-google-pixel-xiaomi-oneplus" id="other-android-devices-google-pixel-xiaomi-oneplus"></a>

Most other Android brands follow a similar "Unrestricted" setting path:

Google Pixel:&#x20;

&#x20;1\. Open **Settings** > **Apps** > **See all apps**

&#x20;2\. Select **SharinPix** > **App Battery Usage**

&#x20;3\. Enable **Allow background usage**

### Troubleshooting Background Tasks

**Low Power Mode:** Both iOS and Android will disable background uploads if the device is in "Low Power Mode" or "Battery Saver" mode.

**Internet Connection:** Background uploads require a stable Wi-Fi or Cellular data connection. If the connection is lost, the upload will pause and resume once you are back online.
