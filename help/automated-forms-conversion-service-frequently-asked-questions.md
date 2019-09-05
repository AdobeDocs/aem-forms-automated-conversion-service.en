---
title: Frequently asked questions
seo-title: Frequently asked questions
description: null
seo-description: null
uuid: 0f6dc39c-99b7-49a4-8e9e-ecc4a35110c0
topic-tags: introduction
discoiquuid: e17c2d2c-8300-4467-aa01-57365697939f
privatebeta: true
---

# Frequently asked questions{#frequently-asked-questions}

**Which version of AEM Forms does the Automated Forms Conversion service support?** 
 <p>Automated Forms Conversion service beta supports AEM 6.5 Forms. It works with both AEM Forms on OSGi and AEM forms on JEE. You require the latest AEM Forms add-on package and Conversion Manager (Connector) package on top of AEM author instance to use the service. For detailed instructions, see <a href="configure-the-automated-forms-conversion-service.md">Configure the Automated Forms Conversion</a> service.</p> 
 <p>We are in the process of adding support for more versions. Keep a watch on Automated Forms Conversion service documentation for information on the availability of more versions. </p> 



 **Can the service be installed on-premise?** 
 <p>Adobe trains AI and ML algorithms of Automated Forms Conversion service on a regular basis with new data set to improve conversion accuracy. The updated algorithms are deployed to the conversion service running on Adobe Cloud at periodic intervals. All the customers of the service are benefitted from the updated algorithms. So, cloud-hosted central deployment is best suited for Automated Forms Conversion service to continuously learn and deliver improvements to all the customers.</p> 
 <p>The service converts blank forms to adaptive forms. The service does not support filled forms and extraction of data from filled forms. Remove data from filled forms and remove or whitelist proprietary information from the forms before sending the forms to service for conversion</p> 



 **Does the service support all formats of PDF forms? What all languages are supported?** 
 <p>The service can convert non-interactive PDF forms, XFA-based XDP and PDF forms, and AcroForms to adaptive forms. The service does not support scanned or filled forms. For other limitations, see the <a href="known-issues.md">known issues</a> article.<br /> </p> 
 <p>We are regularly adding support for other source types. Keep the <a href="introduction-to-automated-form-conversion-service.md">supported languages and PDF forms</a> section on your watchlist for a regular update on newly added features and capabilities.</p> 



 **Can the service produce an XDP instead of an adaptive form?**
 <p>The service does not produce an XDP output for the time being. We are regularly adding features and to the service. Keep the <a href="introduction-to-automated-form-conversion-service.md">supported languages and PDF forms</a> section on your watchlist for a regular update on newly added features and capabilities.</p> 



 **What is the type of generated schema?** 
 <p>You can use the service to generate: </p> 
 <ul> 
  <li>an adaptive form bound to a JSON schema and <br /> </li> 
  <li>an adaptive form not bound to any schema</li> 
 </ul> 



 **Can the service convert a Microsoft Word form to adaptive forms?**
 <p>No, the service does not convert a Microsoft Word form to adaptive yet. You can save a Microsoft Word forms to PDF form and convert the PDF form to an adaptive form.</p> 



 **Can the service convert scanned paper forms and colored forms to adaptive forms?** 
 <p>The service can convert PDF forms to adaptive forms. The service does not support scanned or filled forms. For other limitations, see the <a href="known-issues.md">known issues</a> article.</p> 
 <p>We are regularly adding features and to the service. Keep the <a href="introduction-to-automated-form-conversion-service.md">supported languages and PDF forms</a> section on your watchlist for a regular update on newly added features and capabilities.</p> 



 **Can the service convert a scanned form or only image of a form to an adaptive form?**
 <p>The service does not support converting scanned forms or an image of a form to an adaptive out-of-the-box. However, you use Adobe Acrobat to convert the image of a form to a PDF Form. Then, use the service to convert the PDF Form to an adaptive form. Always use a high-quality image of the form for conversion in Acrobat. It improves the quality of the conversion. <br /> </p> 



 **Some XDP-based forms use form fragments, where should these form fragments be uploaded?** 
 <p> </p> 
 <p class="MsoNormal">Upload form fragments to the conversion folder and preserve the original folder structure. It helps preserve relative paths used in XDP-based forms and form fragments.</p> 
 <p> </p> 
 <p> </p> 



 **Does the service support schema bound XDP forms? If I have an XDP bound to a schema, do I need to embed schema to XDP?** 
 <p>Yes, the service supports schema-bound XDP forms and requires the schema to be embedded to the source XDP form. When you convert a schema-bound XDP form, the service generates a JSON schema. The JSON schema is structurally similar to the XSD schema of source XDP forms.</p> 



 **The service has failed to convert forms. What is the reason and how to resolve the issue?** 
 <p>The most common reasons for the conversion to fail are:</p> 
 <ul> 
  <li>Secured PDF forms are provided for the conversion. Do not use password protected, Document Security protected, or any other protected PDF forms for conversion.</li> 
  <li>Internet connection is interrupted. Ensure that you are connected to the internet during the conversion.</li> 
  <li>Source PDF has an image of the form instead of the actual form.<br /> </li> 
  <li>Service is configured incorrectly, service URL is not provided, or provided service URL is incorrect. Check the <a href="configure-the-automated-forms-conversion-service.md#configure-the-cloud-service">service configuration</a> at <span class="uicontrol">AEM </span>&amp;gt; <span class="uicontrol">Tools </span>&amp;gt; <span class="uicontrol">Cloud Services </span>&amp;gt; <span class="uicontrol">Automated Forms Conversion configuration</span>.</li> 
  <li>IMS Configuration is not configured properly. Perform a health check on the IMS configuration to ensure it is working properly. To check if the IMS Configuration is correct or not: 
   <ol> 
    <li>Go to http://&amp;lt;servername&amp;gt;:&amp;lt;port&amp;gt;/libs/cq/adobeims-configuration/content/configurations.html</li> 
    <li>Select the configuration. Click the <strong>Check Health</strong> from the header and click <strong>Check</strong>. If successful, you get <strong>Token retrieved successfully! </strong>message.</li> 
   </ol> </li> 
 </ul> 



 **Does using custom fonts impact conversion?** 
 <p>When a non-interactive PDF form is converted to an adaptive form, to improve the quality of conversion, the fonts are embedded in the PDF form. The support for embedding fonts is restricted to non-interactive PDF forms. To optimize the conversion of AcroForm and XFA-based PDF forms, fallback fonts are used.</p> 
 <p>Only forms available in the custom fonts directory listed in the <strong><span class="uicontrol">Customer fonts directory</span></strong> field of the <strong><span class="uicontrol">CQ-DAM-Handler-Gibson Font Manager Service</span></strong> configuration are embedded in non-interactive PDF form.</p> 
 <p> </p> 



 **Does the service identify and use fonts of source PDF in output adaptive forms?** 
 <p>Style and layout of a responsive HTML form is generally different from a PDF or paper-based form. To support consistent layout and styling across the organizations, adaptive forms use <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/themes.html">themes to style a form</a>. The conversion service uses the fonts and font styles specified in the theme applied during the conversion. You can change fonts and font styles of the theme to provide a distinct look and feel to the components of an adaptive form.</p> 



 **Does the service automatically extract JavaScript from XDP-based forms and applies it to corresponding adaptive forms?** 
 <p>The service does not automatically convert scripts of XFA-based forms or Acro Forms to corresponding adaptive form rules. You (form-authors) can use the <a href="https://helpx.adobe.com/experience-manager/6-5/forms/using/rule-editor.html">Rule editor</a> to add interactivity to an adaptive form.</p> 



 **Some form objects are not converted correctly to adaptive form components. How to resolve the issue?** 
 <p>Automated Forms Conversion service is trained on a large set of forms. But AI/ML-based applications are limited by their training data and patterns. There could be multiple field types, layouts, patterns, and context discernible to human perception but difficult for automated recognition. The service may fail to identify such objects or may recognize them incorrectly. You may use <a href="review-correct-ui-edited.md" target="_blank">Review and Correct</a> editor to make necessary modifications in the familiar paper form based layout of the input form.</p> 



 **Some corrections are repeated across forms. Can the service identify and fix all such instances in future conversions?**
 <ul> 
  <li>The service is consistently training on your forms and patterns. It learns new patterns on daily-basis. It is yet to start auto-applying corrections repeated across the forms. Keep an eye on prerelease forms for the availability of such a feature.<br /> </li> 
  <li>You can use meta-model to map the form objects to adaptive form component of your choice and pre-configure validations, rules, data patterns, help text, and accessibility properties for the components. All the specified properties are applied during the conversion. You can use meta-model to apply common properties to fields. It can help you reduce some repeated issues across forms. </li> 
 </ul> 



 **What are the options for forms with sensitive data like personally identifiable information (PII) information?** 
 <p>The service supports only blank or unfilled forms. Do not upload filled forms or forms with personally identifiable information (PII). Also, remove pre-filled data and white-label PII, confidential, and proprietary information in source forms.<br /> </p> 



 **Where should the header and footers be placed?** 
 <p>Place header and footer in an adaptive forms template. If the source PDF form has header and footer, the service detects and replaces detected header and footer with header and footer available in adaptive form template, during the conversion. If any extra header or footer is included in the adaptive form, you can use the <a href="review-correct-ui-edited.md">Review and Correct</a> editor to fix or remove such header or footer.</p> 



 **How much time does the service save in comparison to the manual process of planning, creating assets (themes, templates), creating, and publishing an adaptive form?**
 <p>The amount of time depends on the size and complexity of input forms and number of requests. The service intends to significantly reduce time to value by converting PDF Forms to adaptive forms at a much faster pace in comparison to the manual process of converting forms. </p> 

 **What to do if I encounter an error related to RSA libraries? The error message is similar to the message mentioned below:** 
 <p><em>*ERROR* [0:0:0:0:0:0:0:1 [1565757652491] POST /content/dam/formsanddocuments/demo004.affBatchProcessor.html HTTP/1.1] org.apache.sling.engine.impl.SlingRequestProcessorImpl service: Uncaught Throwable java.lang.NoClassDefFoundError: Could not initialize class com.rsa.cryptoj.o.dl at com.rsa.jsafe.JSAFE_SecureRandom.getInstance(Unknown Source) at com.adobe.internal.pdfm.util.Util.appendRandomNumberToPrefix(Util.java: 169) [com.adobe.aemfd.adobe-aemfd-assembler:6.0.34] at com.adobe.internal.pdfm.logging.JobLog.&amp;lt;init&amp;gt;(JobLog.java:126) [com.adobe.aemfd.adobe-aemfd-assembler:6.0.34]</em></p> 
 <p>The aforementioned error occurs when boot delegation is not configured for RSA/BouncyCastle libraries. Perform the below steps to resolve the issue:</p> 
 <p> </p> 
 <ol> 
  <li>Stop the AEM instance. Navigate to the [AEM installation directory]\crx-quickstart\conf\ folder. Open the sling.properties file for editing. If you use [AEM installation directory]\crx-quickstart\bin\start.bat to start an AEM instance, edit the sling.properties located at [AEM_root]\crx-quickstart\. </li> 
  <li>Add the following properties to the sling.properties file:<br /> <em>sling.bootdelegation.class.com.rsa.jsafe.provider.JsafeJCE=com.rsa.*<br /> sling.bootdelegation.class.org.bouncycastle.jce.provider.BouncyCastleProvider=org.bouncycastle.*</em></li>
  <li>Save and Close the file. <br /> </li>
  <li>Start the AEM instance<br /> </li>
 </ol>

  **How to automatically change casing of all the text of an adaptive form?**
  <p>You can use adaptive from themes or style editor to change casing of a field of adaptive form. For example, you can open the theme editor and set value of Case property of all the text of form to uppercase, lowercase, or camelCase. You can also use the CSS Override option in theme editor to create different types of styles.</p>
