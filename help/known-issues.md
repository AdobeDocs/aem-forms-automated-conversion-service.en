---
title: Known Issues
seo-title: Known Issues
description: known issues and limitations for Automated Forms Conversion Service
seo-description: Before you begin using AEM Forms Automated Forms Conversion service, learn about the known issues and limitations of the service
uuid: b1dc661b-ccd3-457f-acbb-4bd25db86e1e
topic-tags: introduction
discoiquuid: 9cd2363c-47a0-46e9-98cd-1fe088b9cd6e
---
# Known issues and limitations {#known-issues-limitations}

Before you begin using AEM Forms Automated Forms Conversion service, review the following known issues and limitations:

## Known issues {#known-issues}

* Folder containing forms for conversion should not have more than 15 forms and 50 pages in total. The size of the source folder should not exceed 10 MB. Do not create subfolders in the source folder. 
* Some form objects are easily visible to the human eye but are [difficult to identify for the service](styles-and-pattern-considerations-and-best-practices.md). Use [Review and correct editor](review-correct-ui-edited.md) to identify and convert such form objects.
* Review and Correct editor:

    * Does not have undo action. The Save button saves the changes permanently.
    * Does not support repeatable panels for XFA-based form.
    * If you modify a list in a table using the Review and Correct editor, the row width does not adjust automatically and the text might spill over to the next row of the table.
    * The **[!UICONTROL Auto-detect multi-column layout from input forms]** feature does not work with Review and Correct editor and Form Fragments.
    * Scribble Signature created with Review and Correct editor fails to load for published adaptive forms.


* For XFA-based forms:
  * Extracting fragments from an XFA-based form is not supported.
  * XFA scripts are not supported. For example, scripts for automatically generating values for a drop-down component.
  * Meta-model does not work for the choice group
  * Choice Groups option with a single character are not identified 
  * When the source document is a dynamic XFA (.XDP) and it [defines behavior of XFA properties in an adaptive form](https://helpx.adobe.com/experience-manager/6-5/forms/using/xfa-api-supported-in-adaptive-form.html#supportedxfaelementsandtheirmappinginadaptiveformsbr), then the presence property of source document is not honored. For example, a field in source document is marked hidden and a script makes the field visible, then the field remains visible in the output adaptive form.

* When you use the **Use input AcroForm as Document of Record (DoR) for generated adaptive forms** option, consider the following:

<table>
    <tr>
        <td>Binding and data is lost for composite text fields. A composite text fields has multiple text boxes aligned with each other. For example, in an AcroForm, a credit card number is split in multiple text boxes and each text box has a separate binding. When the AcroForm is converted to adaptive form, the converted adaptive form has a single binding for all the text boxes. As a workaround, before converting a AcroForm to adaptive form, modify the AcroForm to use single text box to accept credit card numbers.</td>
        <td><img  src="assets/creditCard_Composite.png"/> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td>
    </tr>
    <tr>
        <td>Binding and data is lost for composite date fields. A composite date fields is composed of three different fields. For example, a date of birth field in an AcroForm is split into three separate fields. The adaptive form provides an out-of-the-box date picker component. To use the date picker component of the adaptive form while retaining binding of the AcroForm, before converting a AcroForm to adaptive form, modify the AcroForm to use single date field.</td>
        <td><img  src="assets/CompositeDateField.png"/></td>
    </tr>
    <tr>
        <td>If the size of the check boxes is larger than the accompanying text, then the check boxes are not detected and the binding in the AcroForm is lost. Modify the AcroForm to make the size of the check-boxes smaller than the accompanying text.</td>
        <td><img  src="assets/large-text-box.png"/><br/><img  src="assets/small-text-box.png"/></td>
    </tr>
    <tr>
        <td>If the input fields do not align to corresponding text-field, the input field is not detected.  </td>
        <td><img  src="assets/non-alingned-fields.png"/></td>
    </tr>
    <tr >
        <td>The service converts all the check-boxes of an AcroForm to separate choice groups. Separate choice-groups are created to preserve bindings with AcroForm. Don’t merge choice-groups in the adaptive form. It will lead to loss of bindings. If you merge the choice-groups, convert the form again to regain the lost bindings. </td>
        <td></td>
    </tr>
    <tr >
        <td>Boundraries of some tables are extended out of the page in automatically generated document of record (DoR). </td>
        <td></td>
    </tr>
</table>

## Limitations {#limitations}

* PDF forms with complex dynamic layout, fields with dotted outline, or filled fields are not supported.
* Images and text inside the images are not identified. Manually add images to converted forms.
* Artwork XDP documents are not supported.
* PDF forms larger than 15 pages are not supported.
* Encrypted, password-protected, and secured documents are not converted. Remove encryption or passwords before running the conversion.
* Complex tables like borderless tables, nested tables, and tables with placeholder values are not supported. Use adaptive form editor to add or modify complex tables, after the conversion. Only simple tables, with empty fields, proper headers, and clear boundaries are supported.  
* The service converts only English-language forms to adaptive forms. You can translate converted adaptive forms to another language using [AEM translation workflow](https://helpx.adobe.com/experience-manager/6-5/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.html).
* AEM 6.4 Forms does not support automatic detection of multi-column layout of input forms.
* Information encoded using colors in source PDF form is not carried over to adaptive form.
* Colors of source PDF Form are not carried over to adaptive form themes.
* Colored PDF Forms are treated as greyscale forms and fields are detected accordingly.

