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

# Export media to internal storage

This article illustrates the process of exporting files captured with SharinPix to your device's internal storage.

Various export options covered include:

* [Exporting a single file](export-media-to-internal-storage.md#exporting-a-single-file)
* [Exporting files from a job](export-media-to-internal-storage.md#exporting-files-from-a-job)
* [Automatic file export](export-media-to-internal-storage.md#automatic-file-export)

{% hint style="warning" %}
**Note:**

To enable the export feature, on the [Global Setting](sharinpix-mobile-app-global-configuration.md#set-up-the-parameters-on-your-organization):

* Set the '**allow\_file\_export**' parameter to true.
* Ensure that the '[**auto\_destroy\_after**](sharinpix-mobile-app-global-configuration.md#configure-the-auto_destroy_after-parameter)' parameter is not configured with a value of zero.
{% endhint %}

## Exporting a single file

After submitting files using the SharinPix App, open the SharinPix application and choose the respective job, as demonstrated in the diagram below.

<figure><img src="../.gitbook/assets/Export media to internal storage -1 .png" alt=""><figcaption></figcaption></figure>

Next, select the desired file for export and use the export icon on top, as illustrated in the below diagram, to initiate the export process.

<figure><img src="../.gitbook/assets/Export media to internal storage - 2.png" alt=""><figcaption></figcaption></figure>

## Exporting files from a job

After submitting files with the SharinPix App, navigate to the SharinPix application and select the corresponding job. Next, use the export icon located at the top, as demonstrated in the diagram below, to initiate the export process. This action will export all files associated with that job to your internal storage.

<figure><img src="../.gitbook/assets/Export media to internal storage - 3.png" alt=""><figcaption></figcaption></figure>

## Automatic file export

To enable automatic file export when capturing or selecting files in the SharinPix App, configure the following settings in the [Global Setting](sharinpix-mobile-app-global-configuration.md#set-up-the-parameters-on-your-organization):

* Set the "allow\_auto\_file\_export" parameter to true.
* Ensure that the '[auto\_destroy\_after](sharinpix-mobile-app-global-configuration.md#configure-the-auto_destroy_after-parameter)' parameter is not set to zero.

**Note**: Activating this feature means all files, including those selected from the roll, will be exported to your internal storage.

{% hint style="success" %}
**Tips:**

To locate the exported file on your device, follow these steps:

* For iOS: Navigate to 'On my Phone' -> 'SharinPix Folder'.
* For Android: Go to 'File' -> 'Downloads'.
{% endhint %}
