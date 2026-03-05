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

# How to use a static AlbumID on an online Visualforce page

SharinPix Visualforce page integrations permits to retrieve automatically the current recordID and use this value to display the SharinPix Album accordingly.

In some cases, you want to display an album from a static record and would like to use a Hard coded Album ID.

This sample of code show you how to do this:\
(Just replace the HARD\_CODED\_ALBUM\_ID text by your 18digits record ID)

```html
<apex:page StandardController="Site_Survey__c">
	<!-- HARD-CODED ALBUM ID -->
	<sharinpix:SharinPix height="500px" parameters="
		<sharinpix:SharinPix height="500px" parameters="{'abilities':{'HARD_CODED_ALBUM_ID':{'Access':{'see':true,'image_list':true,'image_upload':true,'image_delete':true,'fullscreen':true,'image_caption':true,'trash':true}}},'Id':'HARD_CODED_ALBUM_ID'}"></sharinpix:SharinPix>" >
	</sharinpix:SharinPix>
	<!--- DYNAMIC ALBUM ID -->
	<sharinpix:SharinPix height="500px" parameters="{'abilities':{'{! CASESAFEID($currentPage.parameters.Id) }':{'Access':{'see':true,'image_list':true,'image_upload':true,'image_delete':true,'fullscreen':true,'image_caption':true,'trash':true}}},'Id':'{! CASESAFEID($currentPage.parameters.Id) }'}'}"></sharinpix:SharinPix>
</apex:page>
```
