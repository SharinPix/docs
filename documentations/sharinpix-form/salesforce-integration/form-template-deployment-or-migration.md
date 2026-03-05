# Form Template Deployment (or Migration)

[SharinPix Form Templates](../form-elements/sharinpix-form-template-editor.md) can be migrated from one Salesforce org (for example, a sandbox) to another Salesforce org (for example, a production org). This is useful when a Form Template has been built and tested in a sandbox and needs to be deployed to production.

There are two ways to deploy a Form Template between Salesforce orgs:

* [Deploy Using the SharinPix Salesforce CLI Plugin](form-template-deployment-or-migration.md#migrate-using-the-sharinpix-salesforce-cli-plugin)
* [Deploy Manually](form-template-deployment-or-migration.md#migrate-manually)

### Deploy Using the SharinPix Salesforce CLI Plugin&#x20;

The SharinPix Salesforce CLI Plugin syncs SharinPix forms between a Salesforce org and files on your computer. Use it to pull a Form Template from your sandbox and push it to production. This method is recommended when deploying multiple Form Templates or repeating the migration as part of a deployment process.

For step-by-step instructions, see [SharinPix Salesforce CLI Plugin](https://docs.sharinpix.com/documentation/cookbook/sharinpix-salesforce-cli-plugin).

### Deploy Manually&#x20;

For a single Form Template, copy the JSON from the Advanced Settings in the source org and paste it into a new Form Template record in the target org.

1. Open the Form Template in your Sandbox and go to Advanced Settings.
2. Copy the Form Template JSON.
3. In Production, create a new Form Template record. You can keep the same name for the template.
4. Paste the same JSON into the new Form Template.

<figure><img src="../.gitbook/assets/Copy of DOC SF - 1920 x 1080 (1) (1).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
The manual method works well for a single, occasional deployment. If you need to migrate multiple Form Templates or repeat the migration regularly, use the SharinPix Salesforce CLI Plugin instead.
{% endhint %}

