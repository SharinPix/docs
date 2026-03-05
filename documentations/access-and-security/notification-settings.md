---
description: Choose recipients for SharinPix notifications.
---

# Notification settings

Use notification settings to choose who receives SharinPix notifications.

This tab is for Salesforce administrators with the SharinPix admin permission.

### Open the Notifications tab

1. In Salesforce, open the **SharinPix Settings** tab.
2. Select **Notifications**.

<figure><img src="../.gitbook/assets/Form Component Doc  (8).png" alt=""><figcaption></figcaption></figure>

### Notification types

Each row represents one email address. Select a checkbox to enable that notification type.

| Column                   | What it covers                                                                                                                                                                 |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Technical Errors**     | Integration failures and processing issues. This includes webhook delivery failures, form submission (form response) errors, and other technical failures requiring attention. |
| **Import Errors**        | Failed imports.                                                                                                                                                                |
| **App Updates & Alerts** | New releases, package upgrades, scheduled maintenance, security advisories, usage alerts, and other important product announcements.                                           |

<figure><img src="../.gitbook/assets/Form Component Doc  (9).png" alt=""><figcaption></figcaption></figure>

### Add a recipient

1. Select **Add email** below the table.
2. Enter the email address in the new row.
3. Select the notification types that address should receive.
4. Once the values are filled, it will be automatically saved.

<figure><img src="../.gitbook/assets/Form Component Doc  (10).png" alt=""><figcaption></figcaption></figure>

### Remove a recipient

1. Select the remove control at the end of the row.
2. Save the settings page.

<figure><img src="../.gitbook/assets/Form Component Doc  (11).png" alt=""><figcaption></figcaption></figure>

### Muted Notifications

If you receive many technical or import errors, contact [SharinPix Support.](https://app.gitbook.com/s/2putv2B9RAZpym8daOH2/how-to-contact-support) They can mute these notification types for you.

{% hint style="info" %}
* In order to unmute notifications, contact [SharinPix Support](https://app.gitbook.com/s/2putv2B9RAZpym8daOH2/how-to-contact-support).
* Only technical and import errors can be muted, App updates & Alerts **cannot** be muted.
{% endhint %}

### I am not receiving error emails

Check the following:

* Your address appears in the recipients table.
* The relevant **Technical Errors** or **Import Errors** checkbox is selected.
* The notification type is not **Muted**.
* Your spam filters do not block SharinPix emails.
