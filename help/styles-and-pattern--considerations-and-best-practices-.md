---
title: Best practices and considerations 
seo-title: Best practices and considerations 
description: null
seo-description: null
uuid: e24773a2-be14-4184-a168-48aa976d459a
topic-tags: introduction
discoiquuid: 79f2026e-73a5-4bd1-b041-d1399b4ad23e
privatebeta: true
index: y
internal: n
snippet: y
---

# Best practices and considerations {#best-practices-and-considerations}

AEM Forms Automated Conversion service converts a PDF form to an adaptive form. The service uses artificial intelligence and machine learning algorithms to understand the layout and fields of the source form. Every machine learning service continuously learns from source data and produces an improved output with every churn. These services learn from the experience like humans.

Automated Forms Conversion service is trained on a large set of forms. It easily identifies fields in a source form and produces adaptive forms. However, there are some fields and styles in PDF forms which are easily visible to the human eye but difficult to understand for the service. The service can assign different than applicable field types or panels to some fields or styles. All such field and style patterns are listed below.

The service would start identifying and assigning correct fields or panels to these patterns as it keeps learning from the source data. For the time being, you can use [Review and Correct](review-correct-ui-edited.md) editor to fix such issues. Before start fixing the issues or reading further, familiarize yourself with [adaptive form components](https://helpx.adobe.com/experience-manager/6-5/forms/using/introduction-forms-authoring.html).

## General {#general}

<!--
Comment Type: draft

<ul>
<li>Service does not convert filled PDF forms to adaptive form. Use empty adaptive forms.Service does not convert colored PDF forms to adaptive form. Use black and white or grayscale adaptive forms. <br /> </li>
<li>Service does not convert filled PDF forms to adaptive form. Use empty adaptive forms.</li>
<li>Service does not support scanned forms. Do not use scanned forms. </li>
<li>Service can fail to recognize text and fields in a dense form. Increase the width between text and fields of a dense form before starting the conversion.</li>
<li>Service does not extract images. Manually add images to converted forms.</li>
<li>Service does not extract text present within an image. Manually add text to the adaptive form.</li>
</ul>
-->

<table cellspacing="0" style="border-collapse: separate; border-spacing: 0.0px;" width="100%"> 
 <tbody>
  <tr>
   <td width="30%">Pattern</td> 
   <td width="70%">Resolution</td> 
  </tr>
  <tr>
   <td><p>Service does not convert colored PDF forms to adaptive form.</p> <p> </p> </td> 
   <td style="text-align: left;"><p>Use black and white or grayscale PDF forms. </p> </td> 
  </tr>
  <tr>
   <td>Service does not convert filled PDF forms to adaptive form.</td> 
   <td style="text-align: left;">Use empty adaptive forms.</td> 
  </tr>
  <tr>
   <td>Service can fail to recognize text and fields in a dense form.</td> 
   <td style="text-align: left;">Increase the width between text and fields of a dense form before starting the conversion.</td> 
  </tr>
  <tr>
   <td>Service does not support scanned forms.</td> 
   <td>Do not use scanned forms.<br /> </td> 
  </tr>
  <tr>
   <td>Service does not extract images and text within images. </td> 
   <td>Manually add images or text to converted forms.</td> 
  </tr>
  <tr>
   <td><p>Tables with dotted or non-clear boundaries and borders do not convert.</p> <p> </p> </td> 
   <td>Use tables with clear explicit boundaries and borders. supported.</td> 
  </tr>
 </tbody>
</table>

## Choice Group  {#choice-group}

<table border="1" cellpadding="1" cellspacing="0" width="100%"> 
 <tbody>
  <tr>
   <td width="30%">Pattern</td> 
   <td width="70%">Resolution</td> 
  </tr>
  <tr>
   <td><p>Choice group options with shapes other than box or circle are not converted to corresponding adaptive form components. </p> <p> </p> </td> 
   <td>Change choice options shapes to box or circle or use <a href="review-correct-ui-edited.md">Review and Correct</a> editor to identify the shapes.</td> 
  </tr>
 </tbody>
</table>

## Form fields {#form-fields}

<table border="1" cellpadding="1" cellspacing="0" width="100%"> 
 <tbody>
  <tr>
   <td width="30%">Pattern</td> 
   <td width="70%">Resolution</td> 
  </tr>
  <tr>
   <td width="25%">Service does not identify fields without clear borders.</td> 
   <td width="50%"><br /> Use <a href="review-correct-ui-edited.md">Review and Correct</a> editor to identify such fields.</td> 
  </tr>
  <tr>
   <td>Service may not identify some choice group form fields with captions at the bottom or right side of a form.</td> 
   <td><br /> Use <a href="review-correct-ui-edited.md">Review and Correct</a> editor to identify such fields</td> 
  </tr>
  <tr>
   <td>Service merges or assigns a wrong type to some form fields which are placed very near to each other or do not have clear borders.</td> 
   <td>Use <a href="review-correct-ui-edited.md">Review and Correct</a> editor to identify such fields.</td> 
  </tr>
  <tr>
   <td>Service can fail to recognize fields with far away captions or a dotted line between the caption and input field.</td> 
   <td>Use forms fields with clear boundaries or use <a href="review-correct-ui-edited.md">Review and Correct</a> editor to fix such issues.</td> 
  </tr>
 </tbody>
</table>

## Lists {#lists}

<table border="1" cellpadding="1" cellspacing="0" width="100%"> 
 <tbody>
  <tr>
   <td width="30%">Pattern</td> 
   <td width="70%">Resolution</td> 
  </tr>
  <tr>
   <td><p>Lists containing form fields are merged or not converted to corresponding adaptive form components</p> <p> </p> </td> 
   <td>Use forms fields with clear boundaries or use <a href="review-correct-ui-edited.md">Review and Correct</a> editor to fix such issues.</td> 
  </tr>
  <tr>
   <td>Service can leave a few nested lists unidentified</td> 
   <td>Use <a href="review-correct-ui-edited.md">Review and Correct</a> editor to fix such issues.</td> 
  </tr>
  <tr>
   <td>Service merges some lists containing choice groups with each other</td> 
   <td>Use <a href="review-correct-ui-edited.md">Review and Correct</a> editor to fix such issues.</td> 
  </tr>
 </tbody>
</table>

<!--
Comment Type: draft

<h3>Choice groups</h3>
-->

<!--
Comment Type: draft

<ul>
<li>Lists with form fields, nested lists, and nested choice groups are not supported.</li>
<li>Form fields with captions at bottom or right are not supported.</li>
<li>Form fields without borders are not supported.</li>
<li>Hidden form fields are not supported.</li>
<li>Button in PDF forms are not converted to adaptive form buttons.<br /> </li>
<li>Tables with clear explicit boundaries and borders are supported.</li>
<li>Fields with far away captions are not supported.<br /> </li>
<li>Choice groups with only box or circle shaped selectors are supported. </li>
</ul>
-->

