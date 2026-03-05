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

# Filter albums by Tags (Tag Filter)

SharinPix albums can be filtered by tags to ensure that only relevant images are exposed to end users.

For example, you may want to display only images that have been reviewed and approved by your internal team. In that case, validated images can be assigned a specific tag (e.g., "Validated"), and the album can be configured to display only images with that tag.

To apply tag filtering on albums, you can configure the **Tag Filter** parameter in the [SharinPix Permission record](../../access-and-security/sharinpix-permission-object-how-to-create-and-assign-custom-permission.md) assigned to the album component.

The **Tag Filter** parameter on the _SharinPix Permission_ record accepts a list of tags as values, separated by semicolons. When applied to an album, only images with the specified tags are displayed. Example values can include <mark style="color:$danger;">`FireExtinguisher;FireHose`</mark>, to filter an album by images tagged with _Fire Extinguisher_ and _FireHose_ as demonstrated below.

### Filtering an album with the Tag Filter Example

Here is an example of an album containing images with different tags and two untagged images:

<figure><img src="../../.gitbook/assets/DOC SF - 1920 x 600 (3).png" alt=""><figcaption></figcaption></figure>

You can filter the available images by tag using the **Tag Filter** parameter found in the _Tag_ section of the SharinPix Permission record.

<figure><img src="../../.gitbook/assets/2 (12).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/3 (12).png" alt=""><figcaption></figcaption></figure>

You can also filter by **untagged images** using the checkbox **Include untagged**

<figure><img src="../../.gitbook/assets/4 (9).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/DOC SF - 1920 x 600 (4).png" alt=""><figcaption></figcaption></figure>
