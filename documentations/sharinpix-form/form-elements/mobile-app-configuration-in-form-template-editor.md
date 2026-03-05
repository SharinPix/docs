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
    visible: false
  metadata:
    visible: false
  tags:
    visible: true
  actions:
    visible: true
---

# Mobile App Configuration In Form Template Editor

In the [SharinPix Form Template Editor](sharinpix-form-template-editor.md), the Capture element is more than just a capture media button. It serves as a fully configurable gateway to the SharinPix Mobile App’s camera features.

By configuring the Mobile App Settings, administrators can dictate exactly how the camera behaves when a user taps the capture button in a form. You can preset the camera mode (e.g., Scan, Video, RoomPlan), control hardware settings (Flash, Front/Back camera), and enforce tagging structures to organise images automatically as they are captured.

This documentation covers:

* [A guide on how to locate, add, and configure the Capture element within the Form Builder.](mobile-app-configuration-in-form-template-editor.md#accessing-mobile-app-configuration-how-to-locate-and-open-the-settings-within-the-form-builder)
* [Configure Mobile App for Other Media-Enabled Input Elements (Radio, Text, TextArea)](mobile-app-configuration-in-form-template-editor.md#configure-mobile-app-for-media-enabled-input-elements-radio-text-textarea)
* [A detailed breakdown of Configuration Parameters for the Mobile App.](mobile-app-configuration-in-form-template-editor.md#configuration-parameters)
* [Configure Capture element within Form Builder to fill PDF with Form Values.](mobile-app-configuration-in-form-template-editor.md#configure-capture-element-within-form-builder-to-fill-pdf-with-form-values)

### Accessing Mobile App Configuration: How to locate and open the settings within the Form Builder.

Follow these steps to configure the capture behaviour for a specific form element capture:

1. Create and open a new Form Template, this is better explained in [SharinPix Form template](sharinpix-form-template-editor.md).&#x20;

* Open the Salesforce App Launcher.
* Search for **SharinPix Form Templates**.
* Click on the **SharinPix Form Templates** object.
* Create a new form template.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (1) (3).png" alt=""><figcaption></figcaption></figure>

2. Add a Capture Element: From the elements sections, drag and drop the Capture element into your form layout.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (5) (3).png" alt=""><figcaption></figcaption></figure>

3. Access Configuration: Click on the Capture element you just added to select it. Look for the "Configure Mobile App" button (on the right) in the element properties panel.&#x20;

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (6) (3).png" alt=""><figcaption></figcaption></figure>

4. Define Settings: A configuration section will appear. Adjust the settings for Mode, Direction, Flash, Tags and others. More on the configuration is explained [below](mobile-app-configuration-in-form-template-editor.md#configuration-parameters).

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (7) (4).png" alt=""><figcaption></figcaption></figure>

5. Open the form on a mobile device (via universal link or deeplink), the different modes and configuration will be available upon opening the capture button.&#x20;

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (8) (2).png" alt=""><figcaption></figcaption></figure>

### Configure Mobile App for Media-Enabled Input Elements (Radio, Text, TextArea)

You can enable media capture directly on standard input fields to associate photos with specific data entries. These are the steps below:

1. Select an Input Element: Click on a Radio, Text, or TextArea element.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (9) (2).png" alt=""><figcaption></figcaption></figure>

2. Enable Media: In the element properties panel, toggle "Enable media capture" to ON.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (10) (2).png" alt=""><figcaption></figcaption></figure>

3. Configure: A "Configure Mobile App" button will appear immediately below the toggle. Click it to define the camera behavior for that specific field.

<figure><img src="../.gitbook/assets/DOC SF - 1920 x 1080 (11) (3).png" alt=""><figcaption></figcaption></figure>

{% hint style="warning" %}
**Note**:\
The configurations above will only work in the **SharinPix Mobile App** and **not in online mode**.
{% endhint %}

### Configuration Parameters

#### **1. Launch Behaviour**

These settings determine the camera's initial state when the user opens it.

<table data-header-hidden><thead><tr><th width="223.41796875">Paramters</th><th></th></tr></thead><tbody><tr><td><strong>Setting</strong></td><td><strong>Description</strong></td></tr><tr><td><a href="https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/mobile-app/sharinpix-mobile-app-deeplink-syntax#mode">Mode</a></td><td><p>Defines which camera interface opens by default. </p><p>Options include:</p><p></p><p>• <strong>Camera:</strong> Standard photo capture.</p><p>• <strong>Roll:</strong> Opens the device gallery directly.</p><p>• <strong>System Cam:</strong> Uses the device's native OS camera.</p><p>• <strong>Scan:</strong> Opens the document scanning interface.</p><p>• <strong>Snap &#x26; Say:</strong> Captures an image while recording audio simultaneously.</p><p>• <strong>Room Plan:</strong> Opens the room scanning tool (iOS only).</p><p>• <strong>Video:</strong> Opens video recording mode.</p></td></tr><tr><td>Direction</td><td><p>Sets which camera lens is active upon launch:</p><p></p><p>• <strong>Back:</strong> The rear-facing main camera (default).</p><p>• <strong>Front:</strong> The selfie camera.</p><p>• <strong>Both:</strong> The front and back cameras simultaneously.</p></td></tr><tr><td>Flash</td><td><p>Controls the flash behaviour:</p><p></p><p>• <strong>Off:</strong> Flash disabled.</p><p>• <strong>On:</strong> Flash fires on every capture.</p><p>• <strong>Torch:</strong> The light remains on continuously (useful for dark environments).</p></td></tr><tr><td>Tags</td><td>Enter a list of tags separated by semicolons (e.g., <mark style="color:red;"><code>Kitchen;Bathroom;Bedroom</code></mark>). This creates a menu in the camera interface, allowing the user to select which "bucket" the photo belongs to before taking it.</td></tr><tr><td>Auto Tags</td><td>A list of tags that are permanently applied to every image captured in this session. These act as hidden system tags and cannot be removed by the user.</td></tr><tr><td>Default Tags</td><td>A specific tag from your <em>Tags</em> list that is pre-selected when the camera opens. Unlike <em>Auto Tags</em>, the user can remove or change this tag if it doesn't apply to the specific photo they are taking.</td></tr><tr><td>Aspect Ratio</td><td><p>Sets the camera's aspect ratio upon launch:<br><br>• <strong>3:4:</strong> Launches the camera in a 3:4 aspect ratio.</p><p>• <strong>9:16:</strong> Launches the camera in a 9:16 aspect ratio.</p></td></tr></tbody></table>

#### **2. Other Features**

<table data-header-hidden><thead><tr><th width="226.21875"></th><th></th></tr></thead><tbody><tr><td><strong>Permission</strong></td><td><strong>Description</strong></td></tr><tr><td>Show Compass</td><td>Adds a Compass Button to the camera interface. When clicked by the user, it toggles a directional compass overlay.</td></tr><tr><td>Allow different Mode Checkboxes</td><td><p>Checking these boxes adds the corresponding mode to the Mode Selection List on the mobile app. This allows users to manually switch between different capture types (e.g., switching from Camera to Scan) while using the app.</p><p></p><p>Available modes to allow/restrict include:</p><p></p><p>• <strong>Allow roll mode:</strong> Access to device gallery.</p><p>• <strong>Allow systemcam mode:</strong> Access to native OS camera.</p><p>• <strong>Allow scan mode:</strong> Access to document scanning.</p><p>• <strong>Allow snap and say mode:</strong> Access to audio-photo capture.</p><p>• <strong>Allow roomplan mode:</strong> Access to 3D room scanning.</p><p>• <strong>Allow video mode:</strong> Access to video recording.</p></td></tr><tr><td>Enable upload confirmation</td><td>Adds a verification step requiring the user to explicitly confirm medias before they are uploaded.</td></tr><tr><td>Enable image review</td><td>Displays each image immediately after it is captured. This allows the user to verify the quality and content of the photo on the spot; if the image is unsatisfactory, they can delete it and take another one before moving on.</td></tr><tr><td>Configure tools for annotation</td><td>Activates the annotation toolbar. Users can draw, sketch, or add text overlays to images immediately after capturing them.</td></tr><tr><td>Auto-export captured media to device</td><td>Automatically downloads media captured during form filling to the user's device.</td></tr></tbody></table>

{% hint style="warning" %}
**Note:**

More information about the different modes is explained in [Deeplink Syntax](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/mobile-app/sharinpix-mobile-app-deeplink-syntax#mode).
{% endhint %}

### Configure Capture element within Form Builder to fill PDF with Form Values.

The following configuration allows prefilling a pdf with form values using the PDF Field Mapping configuration

#### **Creation of PDF**

1. To configure new or existing PDF, refer to [SharinPix PDF Form Builder](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/lightning-web-component/sharinpix-pdf-form-builder)

#### **Creation of Form**

1. Create a form template, this is better explained in [SharinPix Form template](sharinpix-form-template-editor.md)
2. Drag and drop a Capture Element from the elements section into your layout.
3. Add an **API Name** to the fields that you want your PDF to take values from.

<figure><img src="../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

4. To create the **“Fill PDF”** button. Add a capture element and click on **Configure mobile app**

<figure><img src="../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

5. Select **Fill in PDF** in the **Mobile App Action** section.
6. Paste the link you obtained from the PDF or use your existing PDF URL into the PDF URL section.

<figure><img src="../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

In the **PDF Field Mapping** section, there are two fields : **PDF Field Name** and **Fill Value**.

1. The Field Name in the PDF Field Name section **should contain the Field Name configured in your PDF**.
2. Fill Value should be configured as follows:

* Fill Value should be configured with **api\_name.value**
* Date fields should be configured with **api\_name.displayValue**
* In cases where your form fields are in a section, the Fill Value should be configured as the API Name of the section followed by the API Name of the field.

<figure><img src="../.gitbook/assets/image (26).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (25).png" alt=""><figcaption></figcaption></figure>

After configuring, click on the back button and save your Form.

<figure><img src="../.gitbook/assets/image (12).png" alt="" width="518"><figcaption></figcaption></figure>

{% hint style="warning" %}
**Note:**

1. The Fill PDF feature is currently only supported for Text fields and checkboxes.
2. Number, Date fields on the form will be filled into a Text field in the PDF.
3. Form values will overwrite any value present in the field being prefilled in the PDF.
{% endhint %}

