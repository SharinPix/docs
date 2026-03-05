# Basic Setup - Step 3a for Classic Users - Setup SharinPix for Salesforce Classic

Now you are ready to add the SharinPix album to your Page Layout.

The Canvas App is the easiest way to create a space there to add photos, so we'll use that.

**Note:**

* You should keep in mind though that these instructions are applicable for Classic User Interface. Lightning and Mobile User Interfaces will show up with the Canvas App, but need the extra tweaking in the next two articles to work well.
* Since Canvas apps have some limitations such as limited number of calls within 24-hour, we strongly recommend the usage of the \*\*SharinPix Visualforce Component \*\*over the **SharinPix Canvas App** for implementations. However, the SharinPix Canvas App can still be used for testing purposes.

For more information about Canvas app limitations, please refer to the following link:

[https://developer.salesforce.com/docs/atlas.en-us.platform\_connect.meta/platform\_connect/canvas\_framework\_limits.htm](https://developer.salesforce.com/docs/atlas.en-us.platform_connect.meta/platform_connect/canvas_framework_limits.htm)

## Canvas App - Drag and Drop on the layout

Click EDIT next to the Layout(s) where you want to display photos

![](<../../.gitbook/assets/e71a2f9e-2c68-4e66-b532-49d25b9c0f45 (1) (1).jpg>)

## Find "Canvas Apps" at the bottom of the list at left in page layout

![](<../../.gitbook/assets/1921099f-997f-415e-81fb-53a0047d3fc5 (1) (1).jpg>)

## Click on Canvas Apps and you'll see Albums in the field box.

Create Section on the page layout, then Save Layout. The Albums won't go into the Albums section until after it has been saved.

![](<../../.gitbook/assets/c7873c96-ea5c-4c43-9e76-a96a9165e73d (1) (1).jpg>)

## Click the wrench on the canvas app to adjust the settings.

* Set the Height to 500 pixels.
* Ok
* Save

![](<../../.gitbook/assets/c6a6b8d1-c5b5-48ec-af49-db2338b23fbc (1) (1).jpg>)

You can put the Canvas App anywhere on the page. But the best practice is to put all your photos in their own section. Here's how:

1. Add a new section on your layout
2. Use the wrench icon on the section to make it one column
3. Save the layout (not quick saving, use the save button) This step is necessary because if the section isn't saved first, the section won't accept Visual Force or the Canvas App.
4. Re-open the layout
5. Drag and drop the Canvas App into the new section.

## Test by adding a photo!

Drag & Drop or Choose from photo files.

![](/broken/files/ITMGTMTc07jgfl8M7bTU)

The image above shows a photo in the **Thumbnail View**. For more information about the Thumbnail View and the options it provides, refer to the following article: [Thumbnail View](../../features/user-interface/thumbnail-view.md)

Click to see one photo in full size

## Play with the icons at the top to learn what you can do!

![](<../../.gitbook/assets/40b349e3-57c1-46d1-adf5-72c2efb85d7b (1) (1).jpg>)

## What's next?

The Canvas App works well for Classic. For the best user experience of SharinPix, you'll need to add the SharinPix component to Lightning and the Mobile app.

* Setup[ SharinPix for Lightning Experience](basic-setup-step-3b-for-lightning-users-setup-sharinpix-for-lightning-experience.md)
* Setup [SharinPix for Salesforce mobile App](basic-setup-step-3d-for-old-salesforce-mobile-app-users-setup-sharinpix-for-mobile-classic-implement.md)

If you need even more control over your users' experience, go with the [Visual Force page implementation.](../advanced-setup/advanced-setup-using-inline-visual-force-page.md) No need for a developer, either, to get this done!
