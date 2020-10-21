---
title: Frequently asked questions
seo-title: Frequently asked questions
description: Common queries or frequently asked questions
seo-description: frequently asked questions for Automated Forms Conversion Service
uuid: 0f6dc39c-99b7-49a4-8e9e-ecc4a35110c0
topic-tags: introduction
discoiquuid: e17c2d2c-8300-4467-aa01-57365697939f
---

# Frequently asked questions{#frequently-asked-questions}

1. **Which version of AEM Forms does the Automated Forms Conversion service support?** 
    <p>Automated Forms Conversion service supports AEM 6.4 Forms and AEM 6.5 Forms. It works with both AEM Forms on OSGi and AEM forms on JEE. You require the latest AEM Forms add-on package on top of AEM author instance to use the service. For detailed instructions, see <a href="configure-service.md">Configure the Automated Forms Conversion</a> service.</p> 
    <br>

 1. **Can the service be installed on-premise?** 
    <p>Adobe trains AI and ML algorithms of Automated Forms Conversion service on a regular basis with new data set to improve conversion accuracy. The updated algorithms are deployed to the conversion service running on Adobe Cloud at periodic intervals. All the customers of the service are benefitted from the updated algorithms. So, cloud-hosted central deployment is best suited for Automated Forms Conversion service to continuously learn and deliver improvements to all the customers.</p> 
    <p>The service converts blank forms to adaptive forms. The service does not support filled forms and extraction of data from filled forms. Remove data from filled forms and remove or allowlist proprietary information from the forms before sending the forms to service for conversion</p> <br>

1. **Does the service support all formats of PDF forms? What all languages are supported?** 
    <p>The service can convert non-interactive PDF forms, XFA-based XDP and PDF forms, and AcroForms to adaptive forms. The service does not support scanned or filled forms. For other limitations, see the <a href="known-issues.md">known issues</a> article.<br /> </p> 
    <p>We are regularly adding support for other source types. Keep the <a href="introduction.md">supportedPDF forms</a> section on your watchlist for a regular update on newly added features and capabilities.</p> 

    The service can convert only English-language forms to adaptive forms. You can translate the generated adaptive forms to another language using [AEM translation workflow.](https://helpx.adobe.com/experience-manager/6-5/forms/using/using-aem-translation-workflow-to-localize-adaptive-forms.html)</br> </br>

1. **Can the service produce an XDP instead of an adaptive form?**
    <p>The service does not produce an XDP output. We are regularly adding features and to the service. Keep the <a href="introduction.md">supported languages and PDF forms</a> section on your watchlist for a regular update on newly added features and capabilities.</p> <br>

 1. **What is the type of generated schema?** 
    <p>You can use the service to generate: </p> 

    *   an adaptive form bound to a JSON schema and  
    *   an adaptive form not bound to any schema <br><br>

 1. **Can the service convert a Microsoft Word form to adaptive forms?**
    <p>No, the service does not convert a Microsoft Word form to adaptive form. You can save a Microsoft Word forms to PDF form and convert the PDF form to an adaptive form. The complete process is </p> <br>

    1. Use Adobe Acrobat to [convert Word Dococument to an non-interactive PDF](https://helpx.adobe.com/acrobat/how-to/create-pdf-files-word-excel-website.html).
    1. Use Adobe Acrobat to [convert the produced PDF forms to fillable PDF Form](https://helpx.adobe.com/acrobat/how-to/convert-word-excel-paper-pdf-forms.html).
    1. Use Adobe Acrobat to manually update and fix form fields.
    1. Save the PDF form. Now, you can use the form with the conversion service to generate an adaptive form. You can also use the form as a Document of Record template.


 1. **Can the service convert scanned paper forms and colored forms to adaptive forms?**
    <p>The service can convert color PDF forms to adaptive forms. The service does not support scanned or filled forms. For other limitations, see the <a href="known-issues.md">known issues</a> article.</p> <br>

 1. **Can the service convert a scanned form or only image of a form to an adaptive form?**
    <p>The service does not support converting scanned forms or an image of a form to an adaptive out-of-the-box. However, you use Adobe Acrobat to convert the image of a form to a PDF Form. Then, use the service to convert the PDF Form to an adaptive form. Always use a high-quality image of the form for conversion in Acrobat. It improves the quality of the conversion.</p> <br>

1.  **Some XDP-based forms use form fragments, where should these form fragments be uploaded?** 
    <p class="MsoNormal">Upload form fragments to the conversion folder and preserve the original folder structure. It helps preserve relative paths used in XDP-based forms and form fragments.</p> <br>
 
 1. **Does the service support schema bound XDP forms? If I have an XDP bound to a schema, do I need to embed schema to XDP?** 
    <p>Yes, the service supports schema-bound XDP forms and requires the schema to be embedded to the source XDP form. When you convert a schema-bound XDP form, the service generates a JSON schema. The JSON schema is structurally similar to the XSD schema of source XDP forms.</p> <br>

 1. **The service has failed to convert forms. What is the reason and how to resolve the issue?** 
The most common reasons for the conversion to fail are:</p> 
    *   Secured PDF forms are provided for the conversion. Do not use password protected or secured PDF forms for conversion.
    *   Internet connection is interrupted. Ensure that you are connected to the internet during the conversion.
    *   Source PDF has an image of the form instead of the actual form.  
    *   Service is configured incorrectly, service URL is not provided, or provided service URL is incorrect. Check the [service configuration](configure-service.md#configure-the-cloud-service) at **[!UICONTROL AEM]** > **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Automated Forms Conversion configuration]**.
    *   IMS Configuration is not configured properly. Perform a health check on the IMS configuration to ensure it is working properly. To check if the IMS Configuration is correct or not:
        1.  Go to `http://[servername]:[port]/libs/cq/adobeims-configuration/content/configurations.html`
        2.  Select the configuration. Click the **[!UICONTROL Check Health]** from the header and click **[!UICONTROL Check]**. If successful, you get **[!UICONTROL Token retrieved successfully!]** message. <br> <br>

 1. **Does using custom fonts impact conversion?** 
    <p>When a non-interactive PDF form is converted to an adaptive form, to improve the quality of conversion, the fonts are embedded in the PDF form. The support for embedding fonts is restricted to non-interactive PDF forms. To optimize the conversion of AcroForm and XFA-based PDF forms, fallback fonts are used.</p> 
    <p>Only forms available in the custom fonts directory listed in the <strong>Customer fonts directory</strong> field of the <strong> CQ-DAM-Handler-Gibson Font Manager Service</strong> configuration are embedded in non-interactive PDF form.</p> 
    <p> </p> <br>

1. **Does the service identify and use fonts of source PDF in output adaptive forms?** 
    <p>Style and layout of a responsive HTML form is generally different from a PDF or paper-based form. To support consistent layout and styling across the organizations, adaptive forms use <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/themes.html">themes to style a form</a>. The conversion service uses the fonts and font styles specified in the theme applied during the conversion. You can change fonts and font styles of the theme to provide a distinct look and feel to the components of an adaptive form.</p> <br>

1.  **Does the service automatically extract JavaScript from XDP-based forms and applies it to corresponding adaptive forms?** 
     <p>The service does not automatically convert scripts of XFA-based forms or Acro Forms to corresponding adaptive form rules. You (form-authors) can use the <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/rule-editor.html">Rule editor</a> to add interactivity to an adaptive form.</p> <br>

1. **Some form objects are not converted correctly to adaptive form components. How to resolve the issue?** 
    <p>Automated Forms Conversion service is trained on a large set of forms. But AI/ML-based applications are limited by their training data and patterns. There could be multiple field types, layouts, patterns, and context discernible to human perception but difficult for automated recognition. The service may fail to identify such objects or may recognize them incorrectly. You may use <a href="review-correct-ui-edited.md" target="_blank">Review and Correct</a> editor to make necessary modifications in the familiar paper form based layout of the input form.</p> <br/>

1. **Some corrections are repeated across forms. Can the service identify and fix all such instances in future conversions?**
  
    The service is consistently training on your forms and patterns. It learns new patterns on daily-basis. It is yet to start auto-applying corrections repeated across the forms. Keep an eye on prerelease forms for the availability of such a feature. <br/><br/>

    You can use meta-model to map the form objects to adaptive form component of your choice and pre-configure validations, rules, data patterns, help text, and accessibility properties for the components. All the specified properties are applied during the conversion. You can use meta-model to apply common properties to fields. It can help you reduce some repeated issues across forms.<br/><br/>

1.  **What are the options for forms with sensitive data like personally identifiable information (PII) information?** 
    The service supports only blank or unfilled forms. Do not upload filled forms or forms with personally identifiable information (PII). Also, remove pre-filled data, personally identifiable information (PII), confidential, and proprietary information in source forms. <br/>
    
1. **Where should the header and footers be placed?** 
    <p>Place header and footer in an adaptive forms template. If the source PDF form has header and footer, the service detects and replaces detected header and footer with header and footer available in adaptive form template, during the conversion. If any extra header or footer is included in the adaptive form, you can use the <a href="review-correct-ui-edited.md">Review and Correct</a> editor to fix or remove such header or footer.</p> <br />

1. **How much time does the service save in comparison to the manual process of planning, creating assets (themes, templates), creating, and publishing an adaptive form?**
    <p>The amount of time depends on the size and complexity of input forms and number of requests. The service intends to significantly reduce time to value by converting PDF Forms to adaptive forms at a much faster pace in comparison to the manual process of converting forms. </p> <br />

 1. **What to do if I encounter an error related to RSA libraries? The error message is similar to the message mentioned below:** <br/>
    `*ERROR* [0:0:0:0:0:0:0:1 [1565757652491] POST /content/dam/formsanddocuments/demo004.affBatchProcessor.html HTTP/1.1] org.apache.sling.engine.impl.SlingRequestProcessorImpl service: Uncaught Throwable java.lang.NoClassDefFoundError: Could not initialize class com.rsa.cryptoj.o.dl at com.rsa.jsafe.JSAFE_SecureRandom.getInstance(Unknown Source) at com.adobe.internal.pdfm.util.Util.appendRandomNumberToPrefix(Util.java: 169) [com.adobe.aemfd.adobe-aemfd-assembler:6.0.34] at com.adobe.internal.pdfm.logging.JobLog.&amp;lt;init&amp;gt;(JobLog.java:126) [com.adobe.aemfd.adobe-aemfd-assembler:6.0.34]` <br>
    The aforementioned error occurs when boot delegation is not configured for RSA/BouncyCastle libraries. Perform the below steps to resolve the issue:
    <p> </p> 

    1. Stop the AEM instance. Navigate to the `[AEM installation directory]\crx-quickstart\conf\` folder. Open the sling.properties file for editing. If you use `[AEM installation directory]\crx-quickstart\bin\start.bat` to start an AEM instance, edit the sling.properties located at `[AEM_root]\crx-quickstart\`.
    1. Add the following properties to the sling.properties file:<br/> `sling.bootdelegation.class.com.rsa.jsafe.provider.JsafeJCE=com.rsa.*`<br />  `sling.bootdelegation.class.org.bouncycastle.jce.provider.BouncyCastleProvider=org.bouncycastle.*`<br /> `sling.bootdelegation.xerces=org.apache.xerces.*` 
    1. Save and close the file. <br/>
    1. Start the AEM instance.<br/> 
    <br/>

  1. **How to automatically change casing of adaptive form text?**
      <p>You can use adaptive from themes or style editor to change casing of a field of adaptive form. For example, you can open the theme editor and set value of Case property of all the text of form to uppercase, lowercase, or camelCase. You can also use the CSS Override option in theme editor to create different types of styles.</p> 

 1. **Can I use Adobe Sign text tags with Automated Forms Conversion service?**
      <p> When you use Automated Forms Conversion Service to convert a PDF form to an adaptive form and the PDF form has Adobe Sign text tags, those tags are converted to corresponding adaptive form fields and signer details are automatically populated.  The feature is available for only for Acro Forms and adaptive forms support a limited number of Adobe Sign fields.</p>  </br>

    <p> For the complete list of supported tags, open a form in adaptive forms editor and add an Adobe Sign block. Use Adobe Sign block to find all supported Adobe Sign fields. It provides a drop-down to select all the supported fields.</p>

 1. **How to create an Adobe Sign enabled PDF form?**
      </p>To create an Adobe Sign enabled PDF form:</p> Add [Adobe Sign text tags](https://helpx.adobe.com/sign/using/text-tag.html) to field names or use the [Convert to Adobe Sign Form](https://helpx.adobe.com/sign/using/create-forms-with-acrobat.html) option. </br>