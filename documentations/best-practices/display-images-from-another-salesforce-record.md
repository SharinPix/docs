# Display Images from another Salesforce record

When you use a SharinPix component on a page record, it give you access to SharinPix image storage corresponding to this specific record.

But sometimes you may need to have access to images stored in other(s) record(s) from another specific record.

Let's take an example of a WorkOrder.

As a desktop user you may want to see from the WorkOrder record page :

\- Images stored in the Case from which the WorkOrder was created

\- Images from different WorkOrder Line Items related to this WorkOrder

## Showing images from another single record

To show images from another record, you can use the SharinPix Album component and set the AlbumID value to the recordID of the record you want to see.

To do so, you can either develop your own SharinPix Lightning Component and pass a specific value to the parameter, or more easily if you are not a developer, you can rely on a Flow implementation to do so.

This flow can then be added to the Page record.

In our example, the result will be to display the images stored in the cases on which we have a lookup field set directly on the WorkOrder page record.

Here are the full explanation steps by steps on how to implement this : [Display another record's album on a page record using a Flow (Admin-friendly)](../cookbook/display-another-record-s-album-on-a-page-record-using-a-flow-admin-friendly.md)

## Showing images from related records

To show images from related record you have 2 different SharinPix Lightning Components that you can use.

[**SharinPix Related Search**](../lightning-web-component/sharinpix-related-search.md)

This component permits to configure in few clicks a SharinPix search on related records.

It takes a related list as a parameter and show all the images in the same Search result. Those results can be filtered on tags selection to only display some images.

In our example it can show in a tab named After Images all the images tagged as After in the WorkOrder Line Items related to a workorder.\
And in a tab named Before images all the images tagged as Before.

Here you can find a full description for this component : [SharinPix Related Search](../lightning-web-component/sharinpix-related-search.md)

[**SharinPix Related Record Albums**](../lightning-web-component/sharinpix-related-record-albums.md)

This component permits to display the related list on one side using the field that you want as a label and the SharinPix Album if ever on item in the list is clicked.

In our example it can show all the WorkOrder Line Item and in one click on any WOLI display the corresponding Album to show images from that specific Work Order Line Item.

Here you can find a full description of this component :[SharinPix Related Record Albums](../lightning-web-component/sharinpix-related-record-albums.md)

![](<../.gitbook/assets/screenshot-spx-fsl-summer20-dev-ed.lightning.force.com-2020.08.26-17_08_20 (1) (2).png>)
