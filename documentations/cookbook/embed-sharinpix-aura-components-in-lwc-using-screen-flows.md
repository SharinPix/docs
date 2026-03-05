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

# Embed SharinPix Aura components in LWC using Screen Flows

This article provides a workaround that will permit developers to use SharinPix Aura components in their custom LWC.

For this implementation, you will need:

* A **Screen Flow** that will embed the desired SharinPix component
* Add the Screen Flow to your LWC using the solution provided by [**UnofficialSF**](https://unofficialsf.com/developer-topic-insert-screen-flows-into-your-lwc/) site

{% hint style="warning" %}
**Note:**

* To use this workaround, make sure that you have installed the ScreenFlow package from UnofficialSF. You can do so by referring to install link in the following article: [https://unofficialsf.com/developer-topic-insert-screen-flows-into-your-lwc/](https://unofficialsf.com/developer-topic-insert-screen-flows-into-your-lwc/)
* For more information about the Aura components available in the SharinPix package, please refer to the following article: [List of SharinPix LWC and Aura components in the SharinPix package](list-of-sharinpix-lwc-and-aura-components-in-the-sharinpix-package.md)
{% endhint %}

To embed a SharinPix Aura component in a LWC, follow the steps below:

* Create a **Screen Flow** that will embed the desired SharinPix Aura component. For this example, we will be using the **SharinPix Upload Button** component
* In the Flow, create a variable of type **Text** labeled as **recordId**. Mark the variable as **Available for input** as demonstrated below:

![](<../.gitbook/assets/test (89).png>)

* Next, add the **SharinPix Upload Button** component in a **Screen** element and use the variable **recordId** for the **Album Id** parameter as shown below:

![](<../.gitbook/assets/test (90).png>)

{% hint style="success" %}
**Tip:**

You can configure the other parameters as desired for the chosen SharinPix Aura component. For more information about the parameters available for the SharinPix components, please refer to the component's related article using this link: [SharinPix Lightning Components](../lightning-web-component/overview-of-the-sharinpix-lightning-components.md)
{% endhint %}

* Save and activate the Flow when done.
* Next, configure the **ScreenFlow** LWC available in the **UnofficialSF** package so as to call your Flow along with the correct parameters. The code snippet below demonstrates how this can be performed:

customLWC.html

```html
<template>
    <c-screen-flow width='100%' height='300' flow-name='uploadButtonTest' flow-params={flowParams}></c-screen-flow>
</template>
```

customLWC.js

```js
import { LightningElement, api } from 'lwc';

export default class SharinpixUploadButton extends LightningElement {
    @api flowParam = [{
        name: 'recordId',
        type: 'String',
        value: <Your Record ID>
    }]
    get flowParams() {
        return JSON.stringify(this.flowParam)
    }
}
```

{% hint style="warning" %}
**Note:**

For more information about the **ScreenFlow** LWC implementation, refer to the following link: [https://github.com/alexed1/LightningFlowComponents/tree/master/flow\_process\_components/ScreenFlow](https://github.com/alexed1/LightningFlowComponents/tree/master/flow_process_components/ScreenFlow)
{% endhint %}

{% hint style="success" %}
**Tip:**

The above implementation can also be used in Salesforce Community. For Community Guest users to access the LWC, you should provide them access to the **screenFlow** Visualforce page.
{% endhint %}
