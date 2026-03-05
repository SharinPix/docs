# I am unable to save a Flow with an Apex Action after the Salesforce Winter ‘26 release. What should I do?

## Question

After the Salesforce Winter ‘26 release, when I try to add an Apex Action to the _Run Immediately_ path on a record-triggered Flow, I can’t save the Flow. The following error appears:

“A record-triggered flow’s Run Immediately path can’t execute transaction-controlled actions. Remove this element from the flow, or move it to a scheduled path.”

![](<.gitbook/assets/Copy of DOC SF - 1920 x 480.png>)

## Answer

This change is expected behavior introduced in Winter ‘26. Transaction-controlled actions (such as Apex Actions with certain settings) are no longer supported in the _Run Immediately_ path. They must be placed in an **asynchronous path** instead.

{% hint style="info" %}
⚠️ **Important:**

This rule applies to all **new Flows created from Winter ‘26 onwards**. Flows created before the Winter ‘26 release will continue to work as-is until further notice from Salesforce.
{% endhint %}

## How to fix the error

1. Open your Flow in Salesforce.
2. Select the **Apex Action Element**.
3. Click **Show advanced options**.
4. Under **Transaction Control**, set the option to **Always continue in current transaction**.
   * ⚠️ If you choose either of the other two options, the Flow will not save, and the error will continue.

{% hint style="info" %}
**Important Notes:**

* **Always continue in the current transaction** means the action will run in the same transaction.
* If the Apex Action makes a callout while there are pending operations, the Flow will fail.
* If your use case requires callouts or asynchronous handling, you must add an **Asynchronous Path** in the Flow’s Start element and place the Apex Action there.
{% endhint %}

{% hint style="success" %}
**Additional Resources:**

Salesforce Knowledge Article: [_Unable to Save Flow with Apex Action in Immediate Path After Winter ‘26 release_](https://help.salesforce.com/s/articleView?id=005167102\&type=1)
{% endhint %}
