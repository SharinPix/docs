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

# How to send more information for trouble shooting on the web

SharinPix can require to get access to a HAR (HTTP Archives) which records the requests and responses that your browser makes with the SharinPix Web Application.



In order to do so you have to:

1. Start the capture
2. Reproduce the behavior
3. End and save the capture
4. Send the file to Support for review



To start the capture, you can follow those steps under Chrome:

1. In Chrome, go to the page within SharinPix where you are experiencing trouble.
2. At the top-right of your browser window, click the Chrome menu (⋮).
3. Select **Tools > Developer Tools**. The Developer Tools window opens as a docked panel at the side or bottom of Chrome.
4. Click the **Network** tab.
5. Select **Preserve log**.
6. You will see a red circle at the top left of the Network tab. This means the capture has started. If the circle is black, click the **black circle** to start recording activity in your browser.
7. **Refresh the page** and reproduce the problem while the capture is running.
8. After you successfully reproduce the issue, right click on any row of the activity pane and select **Save as HAR with Content**.
9. Select the **Console** tab.
10. Right-click anywhere in the console and select **Save as...**.
11. Name the log file **Chrome-console.log**.
12. Send both files as shared links in a reply to your support request
