# SharinPix Component displays a blank screen in the Salesforce Mobile App. What should I do?

This article explains a known issue where the SharinPix Album or other SharinPix iframe-based components show a blank screen in the Salesforce Mobile App, and how to fix it.

**Who is affected:** This issue was observed in version 264.000 of the Salesforce Mobile App, on iOS devices only. Desktop access and iPad browser access were reported as working.

## Issue Summary

Users may see a blank screen instead of the SharinPix Album loading.

* The issue affects iframe-based, or Visualforce-related, embedded components in the Salesforce Mobile App.
* It is not limited to only SharinPix components, but any component relying on an iframe.

**Root cause summary:** Salesforce Support confirmed that additional security measures related to session settings and trusted domains require extra configuration for components that rely on iframes to load correctly in the Salesforce Mobile App.

## Symptoms

* The SharinPix Album does not load in the Salesforce Mobile App.
* Users only see a blank page or blank component area.
* No visible error message appears in the app.
* The same component can still work on desktop.
* Browser access on iPad can work even when the mobile app does not.

## Solution

To restore access, a Salesforce administrator must add the SharinPix domain to **Trusted Domains for Inline Frames** in Salesforce Session Settings for **both** required iframe types.

1. Log in to Salesforce from a desktop browser using an administrator account.
2. Open **Setup**.
3. In the **Quick Find** box, search for **Session Settings**.
4. Open **Session Settings**.
5. Scroll to **Trusted Domains for Inline Frames**.
6.  Add the following two entries:

    Domain 1:

    * **Domain:** https://app.sharinpix.com
    * **iFrame Type:** Visualforce Pages

    Domain 2:

    * **Domain:** https://app.sharinpix.com
    * **iFrame Type:** UI Embedding

**Expected result:** Salesforce should now show two trusted-domain entries for `https://app.sharinpix.com` — one for **Visualforce Pages** and one for **UI Embedding**, as shown below:

<figure><img src=".gitbook/assets/image (30).png" alt=""><figcaption></figcaption></figure>

## Verification

1. Fully close the Salesforce Mobile App on the affected device.
2. Reopen the app.
3. Open an affected record.
4. Go to the SharinPix tab or album area.
5. Confirm that the album loads correctly and that users can view or upload photos.

## Salesforce Reference

* [Specify Trusted Domains for Inline Frames](https://help.salesforce.com/s/articleView?id=xcloud.security_clickjack_specify_iframe_trusted_domains.htm\&type=5)

{% hint style="success" %}
If you still have issues, please [contact our support team](https://app.gitbook.com/s/2putv2B9RAZpym8daOH2/how-to-contact-support) for help.
{% endhint %}
