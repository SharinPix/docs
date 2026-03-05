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

# Using on Lightning with "SharinPix Album" Lightning Action

The present article shows the different ways to use a Lightning Action within the Salesforce Lightning Experience. You'll be able to launch SharinPix from an Action on any Page Layout, and you can access it from your mobile phone as well.

## Open SharinPix Album with Lightning Action

* Go to Setup -> Object Manager. Select the Object Type on which you intend to add the custom action. In the present case, it will be added on the Account Object.
* On the left-hand-side of the screen, select the Button, Links and Actions item.

![](<../../.gitbook/assets/image (59) (1) (1).png>)

* For the Action Type picklist, select Lightning Component.
* For the Lightning Component field, select \<sharinpix>:SharinPixAlbum. (as shown in the figure below).

![](<../../.gitbook/assets/image (58) (1).png>)

1. Adjust the Height to a minimum of 525px.
2. Select a Standard Label Type.
3. Label: SharinPix Album
4. Name: SharinPix\_Album
5. Click on save.
6. The next step is now to add the Custom Action to the Account Page Layout.
7. Head over to the Account Page Layout most relevant to your case.
8. From Mobile & Lightning Actions, drag and drop the SharinPix Album action inside the Salesforce Mobile and Lightning Experience Actions section. Click on save.

* Access an account record. The newly-created custom action should appear on the page-layout.

![](<../../.gitbook/assets/image (57) (1).png>)

* When the action is selected, the SharinPix Album is launched as shown in the image below.

![](<../../.gitbook/assets/image (56) (1).png>)

{% hint style="success" %}
Don't hesitate to name your Lightning Action with something more relevant than SharinPix Album corresponding to your business.

Something such as "Camera" / "Photos" ....

Please note than those actions could be available on mobile under Salesforce mobile App. Refer to articles on the Mobile App for more information.

If you want your action to use a camera icon, you can find some while searching for SharinPix or Camera when adding the icon to the action.
{% endhint %}
