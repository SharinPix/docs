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

# Error "No CONTROLLER named js://sharinpix.SharinPix found" what should i do?

The error "No CONTROLLER named js://sharinpix.SharinPix found" happen mostly when you are trying to use SharinPix Lightning Component without having a My Domain properly deployed.

To correct this you can:

* Deploy My Domain on your org, please find more information about this here :\
  [https://help.salesforce.com/articleView?id=domain\_name\_guidelines.htm\&type=5](https://help.salesforce.com/articleView?id=domain_name_guidelines.htm\&type=5)
* Use a Visual force page if you can't deploy My Domain to replace the Lightning Component
