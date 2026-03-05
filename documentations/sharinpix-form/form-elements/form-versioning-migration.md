# Form Versioning Migration

## Overview

{% hint style="info" %}
Before versioning, a form template was a single record. Every save in the [Form Template Editor](sharinpix-form-template-editor.md) overwrote that same form. There was no history of earlier designs, and no distinction between a draft you were still editing and the form people were actually filling out.

Form Versioning changes that. Each template can now have multiple versions. From the editor, you can switch between them in the version dropdown, see which one is currently active, and keep older versions instead of replacing them.
{% endhint %}

## Main Template vs Version Template

A main template is the form itself: the named record you created and opened in Salesforce, and manage. It is the parent. It does not hold a specific snapshot of questions and layout, as the live working copy after versioning exists.

A version template is one snapshot of that form’s design. Each save that creates a new version adds another snapshot under the same main template. Versions are numbered (Version 1, Version 2, …), and only one of them can be active.

### How they relate

<table><thead><tr><th width="196.3203125"></th><th>Main template</th><th>Version template</th></tr></thead><tbody><tr><td>Role</td><td>The form you work from</td><td>A specific design of that form</td></tr><tr><td>How many</td><td>One per form</td><td>Many under that main template</td></tr><tr><td>In the editor</td><td>Record page where the version dropdown appears</td><td>An item in the Template Versions dropdown</td></tr><tr><td>Active</td><td>Not the live design</td><td>One version is marked active</td></tr><tr><td>Custom Field RecordType__c</td><td>'main'</td><td>'version'</td></tr></tbody></table>

### List view

<figure><img src="../.gitbook/assets/Form template Migration (5).png" alt=""><figcaption></figcaption></figure>

On the SharinPix Form Templates tab, a new list view named Main Template is available. Open the list view selector at the top of the page and choose Main Template (you can pin it so it stays the default).

This view shows only main templates — the top-level form records such as Car Inspection Form, Fire Safety, and Health & Safety Inspection. It does not list version records.

{% hint style="warning" %}
Without this filter, the default list mixes every version with every form, so the same form name appears many times. Main Template keeps the list to one row per form. Open a row to manage that form, switch versions, and see all responses.
{% endhint %}

### What you see in the UI

On the main form template record, the editor shows a Template Versions dropdown. You pick a version to view or edit. The active version is labeled as such.

If you open a version record directly, you are looking at that snapshot only. Saving still belongs to the parent main template. A version with no parent cannot be saved.

<figure><img src="../.gitbook/assets/Form template Migration.png" alt=""><figcaption></figcaption></figure>

### Saving and Activate

* Save updates a draft that has never been activated.
* Activate publishes a version, making it the live form. Only one version is active at a time.

In practice, you can iterate on a draft until you are ready, activate it when it should go live, and later save again to start a new version without losing the previous one.

<figure><img src="../.gitbook/assets/Form template Migration (1).png" alt=""><figcaption></figcaption></figure>

**When a version is created or saved as a draft**\
A new or updated draft is stored as inactive. Active stays false for this new version/draft until someone activates it.

**When the user activates a version**\
The editor sends an activate action for the version currently selected in the dropdown, along with the activation timestamp from the form editor.

Once a Form Template has been activated, you can no longer update this Form Version because it is in use by end users. Modifying an active version creates a new version, as shown in the picture above.

{% hint style="warning" %}
Other versions keep records of when they were last activated, and that field is not cleared when they become inactive. It records when that version was last made live.
{% endhint %}

The version dropdown refreshes so the active version is labeled as active. On subsequent saves, a version that already has the Last Activated At field is treated as published history: saving creates a new version rather than overwriting it. A draft that has never been activated (with an empty Last Activated At) continues to update in place.

### Main vs Version layout

<figure><img src="../.gitbook/assets/Form template Migration (2).png" alt=""><figcaption></figcaption></figure>

#### Main template (the form)

This record is the container. Related lists roll up activity across every version:

* SharinPix Form Templates — the versions of this form (Version 1, Version 2, …).
* Form Responses (All Versions) — every submitted response for any version of this form.
* Forms In Progress (All Versions) — every in-progress form for any version of this form.

#### Version template

This record is one snapshot of the form. Related lists are only for that version:

* Form Questions — the questions and structure for this version.
* Form Responses — responses submitted using this version only.
* Forms In Progress — forms in progress for this version only.
