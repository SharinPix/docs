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

# SharinPix Mobile App: Snap & Say

The SharinPix mobile app **Snap & Say** feature enables the recognition and translation of spoken language into a photo text description.

This documentation covers the following sections:

* [Demo of the Snap & Say Feature.](sharinpix-mobile-app-snap-say.md#demo)
* [Supported Languages – A list of languages available for this feature.](sharinpix-mobile-app-snap-say.md#supported-languages)

{% hint style="warning" %}
**Note:**

* The **Snap & Say** feature is available by default on the SharinPix mobile app's camera view. It will automatically use the device’s system language.
* On iOS, it is possible to force the language by setting the **snapsay\_language** parameter in the [**Global configuration**](sharinpix-mobile-app-global-configuration.md).
* If the device's language or the language passed to **snapsay\_language** is not supported by the device's OS native API. **English** will be set as the default.
{% endhint %}

## Demo

The screenshot below demonstrates the SharinPix mobile app's camera view with the Snap & Say feature selected at the bottom of the screen in the scrollable horizontal list of modes:

<figure><img src="../.gitbook/assets/SharinPix Mobile App- Snap &#x26; Say - 1.png" alt=""><figcaption></figcaption></figure>

To use the Snap & Say feature, ensure that the option is selected. Then tap and hold the record button to snap the photo and start saying the photo description to your device.

<figure><img src="../.gitbook/assets/SharinPix Mobile App- Snap &#x26; Say - 2.png" alt=""><figcaption></figcaption></figure>

Once you are done saying the description, release the button so as to allow scanning and transformation of your voice record into text using speech recognition. The text will be displayed on the screen and can be edited as depicted below:

<figure><img src="../.gitbook/assets/SharinPix Mobile App- Snap &#x26; Say - 3.png" alt=""><figcaption></figcaption></figure>

You can modify the text by tapping on the text area as demonstrated below:

<figure><img src="../.gitbook/assets/SharinPix Mobile App- Snap &#x26; Say - 4.png" alt=""><figcaption></figcaption></figure>

Tap anywhere outside of the modal to save the text.

To view the photo and the description, click on the captured photos icon located at the bottom left of the screen as demonstrated below:

<figure><img src="../.gitbook/assets/SharinPix Mobile App- Snap &#x26; Say - 5.png" alt=""><figcaption></figcaption></figure>

The photo description will be displayed below:

<figure><img src="../.gitbook/assets/SharinPix Mobile App- Snap &#x26; Say - 6.png" alt=""><figcaption></figcaption></figure>

To upload the photo, go back to the camera view and tap on the upload button located at the bottom right as indicated below:

<figure><img src="../.gitbook/assets/SharinPix Mobile App- Snap &#x26; Say - 7.png" alt=""><figcaption></figcaption></figure>

{% hint style="danger" %}
**Warning** :\
Due to platform limitations, Snap & Say is unavailable for offline Android.
{% endhint %}

## Supported languages

The **Snap & Say** feature supports a wide range of languages to provide users with a seamless experience. Below are some of the most commonly supported languages on both Android and iOS devices:

| Language | Country       | Code  |
| -------- | ------------- | ----- |
| Arabic   | Saudi Arabia  | ar-SA |
| English  | United States | en-US |
| French   | France        | fr-FR |
| German   | Germany       | de-DE |
| Hindi    | India         | hi-IN |
| Italian  | Italy         | it-IT |
| Korean   | South Korea   | ko-KO |
| Russian  | Russia        | ru-RU |
| Spanish  | Spain         | es-ES |
| Swedish  | Sweden        | sv-SE |

{% hint style="warning" %}
**Note:**

* The availability of other languages may depend on your device's operating system.
* For a comprehensive list of available locales, you can refer to [**SimpleLocalize**](https://simplelocalize.io/data/locales/). To ensure compatibility, it's recommended to test your chosen language code.
{% endhint %}
