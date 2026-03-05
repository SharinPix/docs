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
  actions:
    visible: true
  anchors:
    visible: true
---

# Images features in your Salesforce Flow

Most of the SharinPix components are available in Salesforce flow and can be added to Flow screens.

For each component, a description indicating its availability on Page Builder, Community, Flow and more is available in its corresponding article.

![](<.gitbook/assets/Screenshot_2020-11-29_at_02.03.20 (1).png>)

The SharinPix components are listed here: [Overview of the SharinPix Lightning Components](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/lightning-web-component/overview-of-the-sharinpix-lightning-components)

**Best Practice is to use the SharinPix Components in Flows:**

If you only need to upload one picture and apply a specific tag to it, you should use the [SharinPix Single Image](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/lightning-web-component/sharinpix-single-image)

If you need to upload multiple pictures and apply the same tag to all of them, you can either use the [SharinPix Album](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/lightning-web-component/sharinpix-album) or the smaller [SharinPix Upload Button](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/lightning-web-component/sharinpix-upload-button). Both can be personalized using a [SharinPix Permission object](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/access-and-security/sharinpix-permission-object-how-to-create-and-assign-custom-permission) on which you can set the required abilities/features and the tags which can be applied.

To enable the usage of a flow in Field Service, you should use a clickable text that will handle a deeplink URL. To implement this, refer to the following article: [Integration of SharinPix App with SFS (FSL) App using Flows](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/integrations/salesforce-field-service/integration-of-sharinpix-app-with-sfs-fsl-app-using-flows)

Last but not least if you have mobile users using the Salesforce mobile App, you may want them to have a quick access to great features even without good connectivity. To make this happen, you can rely on the SharinPix mobile App, which can be launched from a specific record and with a specific behaviour using the [SharinPix Mobile Launcher](https://app.gitbook.com/s/5EvYRrLbUyvRh8o1jmMG/lightning-web-component/sharinpix-mobile-launcher).
