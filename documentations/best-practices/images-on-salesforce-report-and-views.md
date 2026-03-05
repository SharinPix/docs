# Images on Salesforce Report and Views

To access SharinPix images in Salesforce report and Salesforce views you can either:

* rely on [SharinPix Image records](../image-sync/the-sharinpix-image-object.md) (which are automatically generated once you [setup SharinPix Image Sync](../image-sync/setup-sharinpix-image-sync.md))
* automatically populate your standard or custom object fields with images

![](<../.gitbook/assets/Screenshot_2020-11-28_at_22.36.04 (1).png>)

To populate fields with images the easiest way is to use the [SharinPix Tag Action](../features/working-with-tags/tag-action.md) feature.

When applying a tag, an URL field can be automatically updated with an URL specifying a version of the image. This URL value can be [rendered in a Formula field ](../cookbook/display-an-image-in-a-salesforce-field-using-tag-action.md)which can then be used elsewhere in Salesforce, such as in Views, Reports, Emails or Documents.

**B\*\*\*\*est Practice: you can rely on SharinPix Single Image to simplify the UI and the automation you need after uploads, including saving the Image in a field.**

As an example 4 different Single Image Components can be used to upload different car views (such as front, back, right and left). Each Single Image can be associated with a specific tag value (respectfully front, back, right, left) and fields can be populated accordingly (example: front URL, back URL, right URL and left URL). For each view, those URLs can be rendered in Formula fields (front image, back image, right image and left image).

Then, you just have to use the formula fields in a view to get an overview of the image taken by line of report very easily. This of course requires the usage of Tag Action for each tag.
