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

# Why is the SharinPix Image Related List not displaying after being added to the layout?

If the SharinPix Image Related List does not appear on the screen after you have added it to the layout, the most likely reason is insufficient field-level access.

**Possible Cause:**

* The lookup field linking the object to the [**SharinPix Image Object**](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/image-sync/the-sharinpix-image-object) does not have the required access permissions.

**Solution:**

1. **Check Field-Level Security** :
   * Navigate to **Setup** → **Object Manager** → **SharinPix Image Object**.
   * Locate the lookup field related to your object.
   * Verify its **Field-Level Security** settings.
2. **Provide Minimum Read Access** :
   * Ensure that at least **Read** access is granted to the field for the relevant user profiles.

After updating the permissions, refresh your page and check if the related list is now visible.

{% hint style="success" %}
**Tips:**

* You can refer to the [**Setup SharinPix Image Sync**](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/image-sync/setup-sharinpix-image-sync) Documentation for more information on its configuration.
* If the Related List is still not visible after providing access to the field, contact [**SharinPix Support**](https://app.gitbook.com/s/2putv2B9RAZpym8daOH2/how-to-contact-support) for further assistance.
{% endhint %}
