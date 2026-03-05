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

# Your Salesforce Filters

## Why Affix Filters ?

* The affix filters can prove to be useful in the event you are using special album IDs on Objects, for instance, an object that contains two albums with Ids **\<ObjectID>\_Req** and **\<ObjectID>\_Other** to distinguish between images that are required and other images irrelevant images respectively, you may make use of the Affixes section to filter those images from the Search results.

## How to define Affixes for SharinPix Search

* Affixes are either prefixes or suffixes that are attached to Salesforce Object Ids retrieved from reports used for searching images. For instance, creating a prefix with value "**User\_** " and using it in search will perform a search on **IDs** prefixed with it, i.e, "0030Y00000AKAUl" will become "User\_0030Y00000AKAUl".
* To create an affix:
  * In **Salesforce Classic Experience**: Go to **Setup** > **Build** > **Develop** >**Custom Metadata Types**
  * **In Salesforce Lightning Experience:** In the **Quick Find** box, enter **Custom Metadata Types**
* Click on **Manage Records**, next to SharinPix Search Affix (as shown in the screenshot below).

<figure><img src="../../.gitbook/assets/Image from Gradio (26).png" alt=""><figcaption></figcaption></figure>

* Click on **New** to create a new prefix or suffix.
* The Label field is the text displayed on the SharinPix Image Search form; the Affix Type is whether the Affix Value entered should be prefixed (prepended) or suffixed (appended) to the ID. The Affix Type should either be "Prefix" or "Suffix". Affix Value is the actual value that is affixed to the ID; this will be used as is.
* To set an initial value on the Search form, check or uncheck the **Initial value on SharinPix Search form**.

<figure><img src="../../.gitbook/assets/Image from Gradio (27).png" alt=""><figcaption></figcaption></figure>

* Set the Affix Value as required.
* Click on **Save** when you are done.
