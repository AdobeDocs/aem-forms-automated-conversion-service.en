---
title: Known Issues
seo-title: Known Issues
description: null
seo-description: null
uuid: b1dc661b-ccd3-457f-acbb-4bd25db86e1e
topic-tags: introduction
discoiquuid: 9cd2363c-47a0-46e9-98cd-1fe088b9cd6e
privatebeta: true
---

# Known Issues{#known-issues}

Before you begin using AEM Forms Automated Forms Conversion service, review the following known issues and limitations:

## Known issues {#known-issues}

* Folder containing forms for conversion should not have more than 15 forms and 50 pages in total. The size of the source folder should not exceed 10 MB. Do not create subfolders in the source folder. 
* Some form objects are easily visible to the human eye but are [difficult to identify for the service](styles-and-pattern-considerations-and-best-practices.md). Use [Review and correct editor](review-correct-ui-edited.md) to identify and convert such form objects. Review and Correct editor:

    * Does not support form fragments and tables. Use adaptive form editor to fix conversions that had the Extract Fragmentor Existing Fragments option enabled during conversions and fix table-related issues.  
    * Does not have undo action. The Save button saves the changes permanently.
    * Does not support repeatable panels for XFA-based form.

* For XFA-based forms:

    * Extracting fragments from an XFA-based form is not supported.
    * XFA scripts are not supported. For example, scripts for automatically generating values for a drop-down component.
    * Meta-model does not work for the choice group
    * Choice Groups option with a single character are not identified 
    * When the source document is a dynamic XFA (.XDP) and it [defines behavior of XFA properties in an adaptive form](https://helpx.adobe.com/experience-manager/6-5/forms/using/xfa-api-supported-in-adaptive-form.html#supportedxfaelementsandtheirmappinginadaptiveformsbr), then the presence property of source document is not honored. For example, a field in source document is marked hidden and a script makes the field visible, then the field remains visible in the output adaptive form.

* The **[!UICONTROL Auto-detect multi-column layout from input forms]**** **feature does not work with Review and Correct editor and Form Fragments.   

* If you modify a list in a table using the Review and Correct editor, the row width does not adjust automatically and the text might spill over to the next row of the table.

* When you use the **Use input AcroForm as Document of Record (DoR) for generated adaptive forms** option, consider the following:

* 
* 
* 
* If the input fields do not align to corresponding text-field, the input field is not detected. 

  ![Input field non-aligned with a text field](assets/non-alingned-fields.png)

  Input field non-aligned with a text field

* The service converts all the check-boxes of an AcroForm to separate choice groups. Separate choice-groups are created to preserve bindings with AcroForm. Don’t merge choice-groups in the adaptive form. It will lead to loss of bindings. If you merge the choice-groups, convert the form again to regain the lost bindings.

* Boundraries of some tables are extended out of the page in automatically generated document of record (DoR).

## Limitations {#limitations}

* PDF forms with complex dynamic layout, fields with dotted outline, filled fields, or colored fields are not supported.
* Images and text inside the images are not identified. Manually add images to converted forms.
* Artwork XDP documents are not supported.
* Encrypted, password-protected, and secured documents are not converted. Remove encryption or passwords before running the conversion.
* Complex tables like borderless tables, nested tables, table with colored rows, and tables with placeholder values are not supported. Use adaptive form editor to add or modify complex tables, after the conversion. Only simple tables, with empty fields, proper headers, and clear boundaries are supported.  
* The service converts only English-language forms to adaptive forms. You can translate converted adaptive forms to another language using [AEM translation workflow](https://helpx.adobe.com/experience-manager/6-5/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.html).
* You can only use Google Chrome as the browser to access Review and Correct editor.

