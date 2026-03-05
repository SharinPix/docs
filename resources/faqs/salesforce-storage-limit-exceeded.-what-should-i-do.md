# Salesforce Storage Limit exceeded. What should I do?

If you have received an alert from Salesforce that your storage limits have been exceeded, don't panic! SharinPix stores your actual photos outside of Salesforce, and resolving this issue is usually a straightforward process of managing metadata records or generated files.

This guide will help you identify the root cause and safely free up space in your org.

## 1. How does SharinPix handle storage?

To troubleshoot storage issues, it is important to understand the two different types of storage in Salesforce:

* **File Storage**: This accounts for physical documents, attachments, and files. SharinPix does not use Salesforce File Storage for your photos. All images uploaded via SharinPix are stored securely on our AWS servers, giving you unlimited storage for the pictures themselves.
* **Data Storage**: This includes standard and custom Salesforce records (metadata, text, and relationships). SharinPix consumes Data Storage when it creates records to represent your images or form answers within Salesforce.

## 2. Identifying Which Storage is Full

Before taking action, you must determine whether _Data Storage_ or _File Storage_ is causing the overage.

#### How to check:

1. In Salesforce, go to **Setup**.
2. Search for and click on **Storage Usage**.
3. Review the breakdown to determine whether the issue falls under **Data Storage** (Records) or **File Storage** (Files/Content Documents). Look specifically for SharinPix-related objects that occupy a large percentage of the space.

<figure><img src=".gitbook/assets/DOC SF - 1920 x 1080.png" alt=""><figcaption></figcaption></figure>

## 3. If Data Storage (Records) is Exceeded

If your Data Storage is full, it is likely due to the accumulation of SharinPix custom records over time.

### Cause A: `SharinPix Image` Records

When [Image Sync](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/image-sync/what-is-sharinpix-image-sync) is enabled, SharinPix generates one `SharinPix Image` Salesforce record for every file uploaded. This object stores metadata (URL, filename, associated record) so you can use the images in Salesforce automations, reports, or document generation.

* The Solution: You can safely bulk delete old `SharinPix Image` records (e.g., via SOQL query or Data Loader) for closed Opportunities, old Work Orders, etc.
* Will deleting these records delete the photos? No. Deleting the `SharinPix Image` record does not delete the original photo from AWS. Users will still see all photos normally in the SharinPix Album component.

{% hint style="danger" %}
Important Note: Before deleting `SharinPix Image` records, confirm internally if they are actively being used in reports, automated PDF generation, or customer-facing documents. If they are, those specific records should be retained.
{% endhint %}

#### What if I need the Image records back later?

As long as the original file exists on AWS, `SharinPix Image` records can be recreated at any time:

* For individual records: Use the [Resync button](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/lightning-web-component/sharinpix-album-resync) on the SharinPix Album.
* For bulk records: Run a [batch resync operation](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/image-sync/how-to-use-image-sync-on-multiple-albums-batch).

{% hint style="warning" %}
Note: Users performing a resync must have the `SharinPix Image Sync Permission` permission set.
{% endhint %}

### Cause B: SharinPix Form Feature Records

If your organization uses SharinPix Forms, you may have a high volume of `Form Response` and `Form Answers` records. Every time a form is completed, these records are generated to capture the input data.

* **The Solution**: Similar to Image records, evaluate your data retention policy. You can export and archive older `Form Response` and `Form Answers` records to free up Salesforce Data Storage.

{% hint style="warning" %}
Note: Removing `Form Answers` does not affect the associated `Form Response`. The submitted form data is still available in SharinPix.
{% endhint %}

#### What if I need the Form Answers records back later?

Try to upsert its Form Response on Salesforce:

1. Go to **SharinPix Settings**.
2. Click **Go to Administrative Dashboard**.
3. Open the **Form Responses** tab.
4. Identify the Form Response you want to upsert using its Public ID or **Salesforce Record ID**.
5. Click **Upsert on Salesforce** to upsert the record.

If you need help, contact [SharinPix Support](https://app.gitbook.com/s/2putv2B9RAZpym8daOH2/how-to-contact-support).

<figure><img src=".gitbook/assets/Form template Editor Doc (7).jpg" alt=""><figcaption></figcaption></figure>

<figure><img src=".gitbook/assets/Form template Editor Doc (8).jpg" alt=""><figcaption></figcaption></figure>

## 4. If File Storage (Files/Documents) is Exceeded

If your File Storage is full, it is not due to the photos themselves, but rather to files generated and explicitly saved in Salesforce.

### Cause: Generated PDFs & Content Documents

If your org uses SharinPix to generate PDFs (such as inspection reports, summaries, or customer-facing documents) and you have configured the system to save these PDFs as standard Salesforce Files/Content Documents, this can quickly consume File Storage.

* **The Solution**: If you still need access to these generated documents, you can upload the PDFs directly into SharinPix, using the [album component](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/lightning-web-component/sharinpix-album-lwc), for instance. Once uploaded, users can view them seamlessly through standard SharinPix components. Because the PDFs are now safely stored in SharinPix's unlimited AWS storage, you can safely delete the original Content Documents from Salesforce to recover your File Storage space.
