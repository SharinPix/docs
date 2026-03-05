# I got the error 'Error: Malformed JSON: Expected '\[' at the beginning of List/Set' when configuring the SharinPix Search on Community. What should I do?

![](.gitbook/assets/screenshot-sharinpix-fsl-demo-dev-ed--sitestudio.na207.force.com-2021.09.30-15_45_05.png)

If you encountered the error **Malformed JSON: Expected '\[' at the beginning of List/Set when configuring the SharinPix Search c**omponent on Salesforce Community, you should add an empty square bracket **\[]** , for both the **Tag Names (JSON)** and **Affixes (JSON)** parameters of the SharinPix Search component as demonstrated below if you are not using applying any tag or affix on the component:

![](<.gitbook/assets/2_2 (2).png>)
