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

# Release Notes - Q3 2025

Known Bug with correction

* SharinPix Form: Hidden questions no longer inflate section progress indicators within forms
* SharinPix Form: Prevented invalid submissions when repeated section minimum/maximum rules were not respected
* SharinPix Form: Resolved rare cases where signature or sketch was duplicated after submission
* SharinPix Form: Form parameters (prefill, context, flow variables) now persist correctly across reloads
* SharinPix Form: Fixed issue when template ID was passed incorrectly in deep-link scenarios
* SharinPix Form: Historical responses now always display captured signatures
* SharinPix Form: Unified behaviour for all element types using “previous value” logic
* SharinPix Form: Prevents missing or duplicated images when reopening Form In Progress
* SharinPix Mobile App: Prevents mismatch between captured photos and upload indicators
* SharinPix Mobile App: Prevents camera from freezing or failing to re-enable after toggling
* SharinPix Mobile App: Restores flashlight functionality for both scanning and photo modes
* SharinPix Mobile App: Offline annotation now works consistently across iOS and Android
* SharinPix Mobile App: Fixes crashes and fallback logic when iOS device has no 4K support
* SharinPix Mobile App: Prevents crashes when images were deleted or still processing
* SharinPix Salesforce Package: Resolved missing mobile parameters on LWC-based launches
* SharinPix Album: Prevents crashes when duplicating an image that no longer exists
* SharinPix Album: Fixed bug where pressing “Delete” triggered multiple dialogs and unintended bulk deletion
* SharinPix Album: Improved screen reader support by adding accessible labels to delete actions
* SharinPix Album: Ensures HEIC images display with correct orientation after upload
* SharinPix Drawing & Annotation: Adjusted overlay opacity to improve visibility when comments are open
* SharinPix Webhook: Prevents webhook delivery failures when payload size exceeds limits

New Features

* SharinPix Form: Textarea question types now support prefilled values in both online and in-progress modes
* SharinPix Form: Radio inputs can now display previously selected values when re-opening a form
* SharinPix Form: Default values to radio, date/time, and multi-select fields
* SharinPix Form: Supports formula-based default values such as dynamic dates and conditional logic
* SharinPix Form: Automatically provides an iteration index inside repeated sections for dynamic formulas
* SharinPix Form: Conditional visibility on form elements based on logic rules
* SharinPix Form: Comparative functionality allowing answers to be shown from previous form responses
* SharinPix Form: Spacer element added to allow visual spacing between form blocks
* SharinPix Form: Dynamic rich-text panels supporting variables and conditional visibility
* SharinPix Form: Magic-Fill processed images can now be saved to albums for audit and record-keeping
* SharinPix Form: Percent and Currency field types supported when updating parent records
* SharinPix Form: Communities can now display and manage Form In Progress records
* SharinPix Form: Forms can be opened in online mode directly from draft records
* SharinPix Form: One-click PDF generation from the Form Response record
* SharinPix Form: Launcher now supports deep links for direct form access with context
* SharinPix Form: New Invocable Action to generate Form URLs from Salesforce Flows
* SharinPix Form: Community users can generate PDFs directly from forms
* SharinPix Form: Allows external systems (FSL, mobile, partner apps) to fetch templates safely.
* SharinPix Form: After form submission, the PDF URL is immediately available
* SharinPix Form: Enables switching between multiple device cameras (dual-camera support)
* SharinPix Mobile App: Users can resume unsubmitted forms directly in the app with preserved progress
* SharinPix Mobile App: Template image preview added for better visual context during form filling
* SharinPix Mobile App: Automatic re-upload of unsubmitted forms
* SharinPix Mobile App: Ability to open PDF-based form signatures directly
* SharinPix Drawing & Annotation: Draggable compact tool menu for improved annotation accessibility
* SharinPix Drawing & Annotation: New Drawing UI activated globally with smoother lines and better performance

Improvements & Enhancements<br>

* SharinPix Form: Date/time picker now respects French locale for formats and validation
* SharinPix Form: Date/time fields now support “Now” as a default value
* SharinPix Form: Return URLs now work consistently across all form entry points
* SharinPix Form: Custom filename patterns supported for generated Form PDFs
* SharinPix Form: Generated Form PDFs can now be automatically stored as Salesforce ContentDocuments
* SharinPix Form: Reporting fields added across key form objects to support analytics
* SharinPix Form: Comparative blocks now render correctly in online mode
* SharinPix Form: Start time is now stored on Form Responses for analytics and tracking
* SharinPix Form: Template thumbnails now load more reliably
* SharinPix Form: Improved PDF generation for deeply nested and repeated sections
* SharinPix Form: Faster and more reliable loading of large templates using flattened JSON
* SharinPix Mobile App: Improved sync handling ensures drafts restore correctly after restarts or offline use
* SharinPix Mobile App: Unified top bar across mobile form screens with improved behaviour
* SharinPix Mobile App: Cleaner viewer experience before final submission
* SharinPix Mobile App: Improved capture feedback and smoother transitions between capture and review
* SharinPix Mobile App: Improved handling of parameters from Salesforce Flow, Deeplinks and Universal Links
* SharinPix Mobile App: Faster navigation and improved stability when switching screens
* SharinPix Image Format: Images retain their original format (PNG/JPEG) after transformations
* SharinPix Drawing & Annotation: Improved reliability when switching between image-heavy pages

{% hint style="warning" %}
**Note:**

Latest Version containing the above Bug Fixes and New Features:

* SharinPix Mobile App: v.6.47827
* SharinPix on Salesforce App Exchange: v.1.375
{% endhint %}
