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

# Organization Utils Methods

This article presents our organization's Utils methods, which are utility methods that modify the [organization-wide SharinPix settings](../mobile-app/sharinpix-mobile-app-global-configuration.md).

## Organization Utils Methods Example

**The organization Utils methods include:**

* [getMobileAppConfig:](organization-utils-methods.md#getmobileappconfig) Fetches your organization's SharinPix Mobile app configuration
* [updateMobileAppConfig:](organization-utils-methods.md#updatemobileappconfig) Updates your organization's SharinPix Mobile app configuration

### getMobileAppConfig

_global Object **getMobileAppConfig**()_

* Fetches your organization's SharinPix Mobile app configuration

```apex
System.debug(sharinpix.OrgUtils.getMobileAppConfig());
```

Example mobile app config on the SharinPix Admin dashboard:

![](<../.gitbook/assets/Screenshot 2025-02-20 at 11.28.36 (1) (2).png>)

Example output from the _getMobileAppConfig()_ :

```json
{
  "annotation_config": "https://app.sharinpix.com/o/bc40/annotation_configs/5c9a7083-15a5-4027-a652-2e7b94e742c6",
  "checklists": {
    "Handbags": {
      "form": [
        {
          "default_option": "",
          "label": "Status",
          "optional": false,
          "options": [
            "OK",
            "N/A",
            "Uncertain"
          ],
          "type": "select",
          "value": "status"
        }
      ],
      "tags": [
        "Zipper**5",
        "Logo**2",
        "Color**0"
      ]
    }
  }
}
```

### updateMobileAppConfig

_global Object **updateMobileAppConfig**(Map\<String, Object> **config**)_

* Updates your organization's SharinPix Mobile app configuration

#### Using the updateMobileAppConfig method to update the mobile app configurations.

Below an Apex Map\<String, Object> is initialized and used as parameter for the updateMobileAppConfig method. The update will provide the Checklist1 to be used in the mobile app with its available tags and other parameters.

```apex
Map<String, Object> config = new Map<String, Object> {
     'Checklist1' => new Map<String, Object> {
        'tags' => new List<String> { 'Middle', 'After', 'Fill Material' },
        'await_upload' => true
    }
};
    
sharinpix.OrgUtils.updateMobileAppConfig(config);
```

Example Mobile app config on the Sharinpix Admin dashboard after update:

![](<../.gitbook/assets/Screenshot 2025-01-20 at 14.08.20 (1) (2).png>)

#### Using the updateMobileAppConfig method to clear the mobile app configurations.

The example below resets the organization's mobile app configuration.

```apex
Map<String, Object> config = new Map<String, Object>();

sharinpix.OrgUtils.updateMobileAppConfig(config);
```

Example Mobile app config on the Sharinpix Admin dashboard after reset:
