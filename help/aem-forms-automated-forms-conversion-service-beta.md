---
title: AEM Forms Automated Forms Conversion service prerelease notes
seo-title: AEM Forms Automated Forms Conversion service prerelease notes
description: null
seo-description: null
uuid: 70b5af51-7940-450c-a4fd-96858bd4b202
contentOwner: vishgupt
topic-tags: migration
discoiquuid: 3e01b5b5-d9e1-4592-b084-9ddc7fb3fc12
privatebeta: true
---

# AEM Forms Automated Forms Conversion service prerelease notes{#aem-forms-automated-forms-conversion-service-prerelease-notes}

Welcome to the AEM Automated Forms Conversion prerelease program. Read on for resources and instructions to get started and make the best of the prerelease program.

Automated Forms Conversion service by AEM Forms helps accelerate digitization and modernization of data capture experience through automated conversion of legacy print forms to adaptive forms. The service, powered by Adobe Sensei, automatically converts your PDF forms to device-friendly and responsive adaptive forms. While leveraging the existing investments in PDF Forms, the service can automatically apply appropriate validations to adaptive form fields during conversion.

## What's new and improved {#what-s-new-and-improved}

<details>
 <summary>May 16, 2019 release</summary>
 <ul> 
  <li>Added support for IMS integration. The service is now accessible only via Adobe I/O. <a href="configure-the-automated-forms-conversion-service.md#adduseranddevs">Create an Adobe I/O integration</a> to use the service.</li> 
  <li>Added the Preview features tab for the experimental features on the <a href="convert-existing-forms-to-adaptive-forms.md#start-the-conversion-process">conversion settings dialog</a>. </li> 
 </ul> 
</details>

<details>
 <summary>May 07, 2019 release</summary>
 <ul> 
  <li>Added support to identify and preserve multi-column layouts of source forms and automatically generate corresponding layouts for adaptive forms. These layouts help display multi-column forms on large screen displays. For example, when a source PDF has two-column layout, the service generates an output adaptive form with two-column layout for large screen displays such as desktops and laptops and single-column layout for mobile devices and tablets. </li> 
  <li>Improvements in identifying lists and performance of Review and Correct editor.</li> 
  <li>Improved the message displayed in Review and Correct editor on deleting a panel.</li> 
  <li>General performance improvements in responsiveness and speed of the conversions. </li> 
 </ul> 
</details>

<details>
 <summary>March 03, 2019 release</summary>
 <ul> 
  <li>Added limited support to detect and edit tables in Review and Correct editor.</li> 
  <li>Added support to convert an XFA-based form to an adaptive form. For example, XFA-based PDF forms or XDP forms. When an XFA-based form is converted to adaptive form, on submission, the adaptive form produces a JSON schema instead of XML schema. JSON schema of a converted adaptive form is complaint with XML schema of an XFA-based form. You can use the <a href="https://sling.apache.org/apidocs/sling5/org/apache/sling/commons/json/xml/XML.html#toString" target="_blank">org.apache.sling.commons.json.xml API</a> to convert a JSON schema to XML schema.</li> 
  <li>Added support to use XFA-based forms with .xdp extension as a template for document of record of converted forms. </li> 
 </ul> 
</details>

<details>
 <summary>January 19, 2019 release</summary>
 <ul> 
  <li>Added support for dynamic XFA.</li> 
  <li>Added support to enable Adobe Analytics during conversion. </li> 
  <li>Added support to identify and convert <a href="assets/hidden-fields.gif" target="_blank">hidden fields for XFA</a>.</li> 
  <li>Improved identification of tables, Acro Forms fields, and choice group fields.</li> 
 </ul> 
</details>

<details>
 <summary>January 04, 2019 release </summary>
 <ul> 
  <li>Improvements in Review and Correct editor:
   <ul> 
    <li>Added support to move components of a form within the content browser (tree view) of the form. When a component is moved, the JSON data is also moved and updated in the data XML accordingly.</li> 
    <li>Added ability to provide name and title for each page of the adaptive form.</li> 
    <li>Added the ability to provide multiline text for field components of type text. The <strong>Allow Multiline</strong> option is added to properties browser to enable the functionality.</li> 
    <li>Review and Correct editor was slowing down while working on large forms. Now the editor works smoothly with large forms.</li> 
   </ul> </li> 
  <li>Improved performance of service and detection accuracy for choice fields and choice groups.</li> 
  <li>Improved strings of configuration dialog UI.</li> 
 </ul> 
</details>

## What's supported in the current prerelease build {#what-s-supported-in-the-current-prerelease-build}

The current prerelease build of Automated Forms Conversion service **supports non-interactive PDF forms **and** XFA-based forms (XDP and PDF Forms) **for conversion to adaptive forms. The service also offers support for automatically **generating Document of Record **for XFA-based forms. The service also has limited support for Acroforms.

## Download the latest prerelease software builds {#download-the-latest-prerelease-software-builds}

Download the following software packages for the prerelease program to set up Automated Forms Conversion service.

| Software |Build location |
|---|---|
| AEM 6.5 Quickstart | [cq-quickstart-6.5.0](https://artifactory.corp.adobe.com/artifactory/maven-aem-dev/com/day/cq/cq-quickstart/6.5.0/cq-quickstart-6.5.0.jar) |
| AEM 6.5 Forms add-on package  |
Windows: [AEMFD-Win-6.0.80](https://artifactory.corp.adobe.com/artifactory/maven-aemforms-release-local/com/adobe/aemds/adobe-aemfd-win-pkg/6.0.80/) 
Linux: [AEMFD-Linux-6.0.80](https://artifactory.corp.adobe.com/artifactory/maven-aemforms-release-local/com/adobe/aemds/adobe-aemfd-linux-pkg/6.0.80/)  |
| AEM Forms Automated Forms Conversion service package | [Automated-Forms-Conversion-package-1.1.4](https://artifactory.corp.adobe.com/artifactory/maven-aemforms-release-local/com/flamingo/automated-forms-conversion/1.1.4/automated-forms-conversion-1.1.4.zip) |

## Documentation resources {#documentation-resources}

See the following documentation resources for detailed information about using AEM Forms Automated Forms Conversion service.

| Document |Coverage |
|---|---|
| [Automated Forms Conversion service](introduction-to-automated-form-conversion-service.md) |
Introduction to the Automated Forms Conversion service and conversion workflow  |
| [Best practices and considerations](styles-and-pattern-considerations-and-best-practices.md) |Patterns and styles of form fields to consider before starting the conversion |
| [Configure the Automated Forms Conversion service](configure-the-automated-forms-conversion-service.md) |Prerequisites and steps to install and configure the Automated Forms Conversion service |
| [Use Automated Forms Conversion service](convert-existing-forms-to-adaptive-forms.md) |Steps to run the Automated Forms Conversion service  |
| [Review and correct converted adaptive forms](review-correct-ui-edited.md) |Use Review and Correct editor to review and make corrections to converted adaptive forms  |
| [Frequently asked questions](automated-forms-conversion-service-frequently-asked-questions.md) |List of frequently asked questions |
| [Known issues](known-issues.md) |List of known issues and possible workarounds |

## Known issues and workarounds {#known-issues-and-workarounds}

Before you begin using AEM Forms Automated Forms Conversion service, review the [Known issues](known-issues.md) and the [Best practices and considerations](styles-and-pattern-considerations-and-best-practices.md) articles, and make suggested changes to your forms.

## Share feedback {#share-feedback}

Your feedback is important as it helps us improve our offerings. To share your experiences and report feedback on the conversion service and related documentation, log a JIRA issue with the details listed in table below.

### Before you start {#before-you-start}

* Add the source PDF form and produced adaptive form to an archive. Create and add these to a collateral zip/archive.
* Take screen-shots or create video recordings of any issue encountered in Review and Correct editor. Add the screen-shot or video to collateral zip/archive.
* Identify and report the visual patterns with proper screenshots or videos. For example, fields with a caption at the bottom are not be extracted in many forms, choice groups with circular widget are not working in many forms, and similar reoccurring issues. Do not report each and every issue related to missed fields.

### Log JIRA issue {#log-jira-issue}

<table border="1" cellpadding="1" cellspacing="0" width="100%"> 
 <tbody>
  <tr>
   <td>JIRA field</td> 
   <td>Options description</td> 
  </tr>
  <tr>
   <td>Project</td> 
   <td>
    <ul> 
     <li>CQ: Use the CQ<strong> </strong>project to report bug or improvements in the conversion service.</li> 
     <li>CQDOC: Use the CQDOC<strong> </strong>project to report bug or improvements in the documentation.</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>Issue Type</td> 
   <td>
    <ul> 
     <li>Bug: Use the Bug issue type when the behavior is not as expected or documented instructions are incorrect.</li> 
     <li>Improvement: Use the Improvement issue type when a key aspect of the feature is missing and should be provided or documented instructions are insufficient to understand or use the feature. </li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>Component<br /> </td> 
   <td>Forms - Sensei</td> 
  </tr>
  <tr>
   <td>FixVersion<br /> </td> 
   <td>AFF 1.0.0 L&lt;xx&gt;, where &lt;xx&gt; is the version number of the <a href="https://wiki.corp.adobe.com/pages/viewpage.action?spaceKey=lc&amp;title=Automated+Forms+Conversion+Service+Beta+-+Latest+Builds" target="_blank">release</a>. </td> 
  </tr>
  <tr>
   <td>Label<br /> </td> 
   <td>Flamingo-BETA</td> 
  </tr>
  <tr>
   <td>Description</td> 
   <td>Provide the following information in the description field:<br /> 
    <ul> 
     <li>Problem statement</li> 
     <li>Steps to reproduce the issue<br /> </li> 
     <li>Actual result of the conversion<br /> </li> 
     <li>Expected result of the conversion<br /> </li> 
     <li>Attach collaterals or provide links to download</li> 
    </ul> </td> 
  </tr>
 </tbody>
</table>

**Guidelines to use a label other than Flamingo-BETA**

* Prefix Flamingo-BETA to your custom label. For example, Flamingo-BETA-XXXXXX
* Use hyphen (-). Do not add a space between label text.  
* Do not change the Flamingo-BETA section of any label.
* Custom section of the label (XXXXXX) should not exceed 6 letters.   
* Use only capital letters for custom section of the label.

