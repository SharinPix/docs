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

# Append images to a Rich Text field using a Batch (Developer-Oriented)

The **SharinPixToRichTextAutomation** class includes the method **appendToRichText**, which can be used to populate images within records in batch.<br>

The variables available in the Params inner class are as follows:

<table data-header-hidden><thead><tr><th width="206.8203125"></th><th width="306.109375"></th><th></th></tr></thead><tbody><tr><td><strong>Variable API Name</strong></td><td><br><strong>Description</strong></td><td><strong>Is Field Value Mandatory?</strong></td></tr><tr><td>recordId<br></td><td>The record ID.</td><td>Yes</td></tr><tr><td>richTextFieldApiName</td><td>The <strong>API name</strong> of target Rich Text field.<br></td><td>Yes</td></tr><tr><td>imageUrlFieldApiName<br></td><td>The <strong>API name</strong> of the image URL field.<br>Some available values are:<br><strong>sharinpix__ImageURLFull__c</strong>, <br><strong>sharinpix__ImageURLOriginal__c</strong>,<br><strong>sharinpix__ImageURLThumbnail__c</strong>,<br><strong>sharinpix__ImageURLMini__c</strong>.<br>You can also create a custom image URL field on the <strong>SharinPix Image</strong> <strong>object</strong>.<br></td><td>Yes</td></tr><tr><td>imageIds</td><td><p>The list of public IDs of images to be included in the Rich Text field.</p><p>If no value is provided for this field, all images available on the record's album will be included in the Rich Text field.</p></td><td>No</td></tr><tr><td>replaceContent</td><td>When value is set to <strong>true</strong>, the existing content of target Rich Text Area will be replaced.<br></td><td>No<br></td></tr><tr><td>imageCaptionText</td><td>The <strong>API name</strong> of the field containing the text to be displayed alongside the image.<br>Some accepted values here are any <strong>API name</strong> of <strong>Text</strong> fields <strong>available for the SharinPix Image object</strong> such as <strong>Name</strong>, <strong>sharinpix__Title__c</strong> or <strong>Title &#x26; Description</strong>.</td><td>No<br></td></tr><tr><td>columns</td><td>The number of columns to be included in the Rich Text field.<br>The default column value is <strong>1</strong> and the accepted value ranges from <strong>1</strong> to <strong>10</strong> columns.<br></td><td>No</td></tr></tbody></table>

The example below demonstrates how the **appendToRichText** method can be used in a Batch to generate images on multiple Account records:

```java
public class myBatch implements Database.Batchable<sObject>, Database.Stateful {

    public list<Account> acclist;

    public myBatch(list<Account> acclist) {
        this.acclist = acclist;
    }

    public Database.QueryLocator start(Database.BatchableContext bc) {
        return Database.getQueryLocator('select id from Account where Id IN :acclist');
    }

    public void execute(Database.BatchableContext bc, List<Account> scope){
        sharinpix.SharinPixToRichTextAutomation.Params params = new sharinpix.SharinPixToRichTextAutomation.Params();
        List<sharinpix.SharinPixToRichTextAutomation.Params> paramsList = new List<sharinpix.SharinPixToRichTextAutomation.Params>();
        for(Account acc : scope) {
            params.recordId = acc.Id;
            params.imageUrlFieldApiName = 'sharinpix__ImageURLThumbnail__c';
            params.columns = 4;
            params.replaceContent = true;
            params.richTextFieldApiName = 'MyRichTextField__c'; 
            paramsList.add(params);
            
        }
        sharinpix.SharinPixToRichTextAutomation.appendToRichText(paramsList);
    }

    public void finish(Database.BatchableContext bc){}
}
```

{% hint style="danger" %}
When running the batch, the number of records to be passed in the Database.executeBatch method should be limited to **one**: `Database.executeBatch(new myBatch(acclist), 1);`
{% endhint %}
