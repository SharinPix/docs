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

# Multiple Image download (ZIP) - how to add download:true to a VisualForce page

To enable multiple image download using the zip button, a Visualforce page should be implemented. Using this VF page, one can then modify the abilities accordingly.

After creation of the Visualforce page, the latter can be added on a page layout or on a record page using the Visualforce Lightning Component.

In order to display the zip button, the **download:true** option should be added before the ability list in the Visualforce page as shown in the code snippet below:

```
<apex:page standardController="Opportunity"> 
 <sharinpix:SharinPix height="500px" 
    parameters="{
         'Id': '{!CASESAFEID($CurrentPage.parameters.Id)}', 
         'download': true, 
         'abilities':{'{!CASESAFEID($CurrentPage.parameters.Id)}':
            {'Access': {
                'image_tag:true,
                'paste':true,
                'image_copy':true,
                'image_download':true,
                'image_rotate':true,
                'image_crop':true,
                'image_delete':true,
                'image_upload':true,
                'image_list':true,
                'see':true }
            }
        }
    }" 
    /> 
</apex:page>
```
