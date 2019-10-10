---
title: [DO NOT PUBLISH] Best practices and considerations 
seo-title: [DO NOT PUBLISH] Best practices and considerations 
description: null
seo-description: null
page-status-flag: never-activated
uuid: c2821264-39e2-44f8-b234-835c46f33fd5
topic-tags: introduction
discoiquuid: b786e40a-202e-4e17-a2f5-1f77c46538c2
privatebeta: true
index: no
---

# [DO NOT PUBLISH] Best practices and considerations {#do-not-publish-best-practices-and-considerations}

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

<table border="1" cellpadding="1" cellspacing="0" style="border-collapse: separate; border-spacing: 0px;" width="100%"> 
 <tbody>
  <tr>
   <td width="30%">Known patterns and resolution</td> 
   <td width="70%">Example</td> 
  </tr>
  <tr>
   <td><p><strong>Pattern</strong></p> <p>Service does not convert colored PDF forms to adaptive form.</p> <p> </p> <p><strong>Resolution</strong></p> <p>Use black and white or grayscale PDF forms. </p> </td> 
   <td style="text-align: left;"> <img src="assets/coloured-form.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>Pattern</strong></p> <p>Service does not convert filled PDF forms to adaptive form.</p> <p> </p> <p><strong>Resolution</strong></p> <p>Use empty adaptive forms.</p> </td> 
   <td style="text-align: left;"><img src="assets/pre-filled-form.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>Pattern</strong></p> <p>Service can fail to recognize text and fields in a dense form.</p> <p> </p> <p><strong>Resolution</strong></p> <p>Increase the width between text and fields of a dense form before starting the conversion.</p> </td> 
   <td style="text-align: left;"><img src="assets/dense%20form.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>Pattern</strong></p> <p>Service does not support scanned forms.</p> <p> </p> <p><strong>Resolution</strong></p> <p>Do not use scanned forms. </p> </td> 
   <td><img src="assets/scanned-form.jpg" /></td> 
  </tr>
  <tr>
   <td><p><strong>Pattern</strong></p> <p>Service does not extract images and text within images. </p> <p> </p> <p><strong>Resolution</strong></p> <p>Manually add images or text to converted forms.</p> </td> 
   <td><img src="assets/image-in-adaptive-form.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>Pattern</strong></p> <p>Tables with dotted or non-clear boundaries and borders are do not convert.</p> <p><strong>Resolution</strong></p> <p>Use tables with clear explicit boundaries and borders. supported.</p> </td> 
   <td><img src="assets/border-less-tables.png" /></td> 
  </tr>
 </tbody>
</table>

## Choice Group  {#choice-group}

<table border="1" cellpadding="1" cellspacing="0" width="100%"> 
 <tbody>
  <tr>
   <td width="30%">Pattern</td> 
   <td width="70%">Example</td> 
  </tr>
  <tr>
   <td><p><strong>Pattern</strong></p> <p>Choice group options with shapes other than box or circle are not converted to corresponding adaptive form components. </p> <p> </p> <p><strong>Resolution</strong></p> <p>Change choice options shapes to box or circle or use Review and Correct editor to identify the shapes.</p> </td> 
   <td><img src="assets/shaded-box-patterns.png" /> </td> 
  </tr>
 </tbody>
</table>

## Form fields {#form-fields}

<table border="1" cellpadding="1" cellspacing="0" width="100%"> 
 <tbody>
  <tr>
   <td width="30%">Pattern</td> 
   <td width="70%">Example</td> 
  </tr>
  <tr>
   <td width="25%"><p><strong>Pattern</strong></p> <p>Service does not identify fields without clear borders.</p> <p> </p> <p><strong>Resolution</strong></p> <p>Use Review and Correct editor to identify such fields.</p> <p> </p> <p> </p> </td> 
   <td width="50%"><br /> <img src="assets/fields-without-clear-borders.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>Pattern</strong></p> <p>Service leaves some form fields with captions at the bottom or right unidentified.</p> <p> </p> <p><strong>Resolution</strong></p> <p>Use Review and Correct editor to identify such fields</p> </td> 
   <td><br /> <img src="assets/forms-with-clear-borders-scale.png" /><br /> </td> 
  </tr>
  <tr>
   <td><p><strong>Pattern</strong></p> <p>Service merges or assigns a wrong type to some form fields which are placed very near to each other or do not have clear borders. </p> <p> </p> <p><strong>Resolution</strong></p> <p>Use Review and Correct editor to identify such fields.</p> </td> 
   <td><img src="assets/forms-with-fields-placed-nearby.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>Pattern</strong></p> <p>Service can fail to recognize fields with far away captions or a dotted line between the caption and input field.</p> <p> </p> <p><strong>Resolution</strong></p> <p>Use forms fields with clear boundaries or use Review and Correct editor to fix such issues.</p> </td> 
   <td><img src="assets/form-fields-with-far-away-captions.png" /></td> 
  </tr>
 </tbody>
</table>

## Lists {#lists}

<table border="1" cellpadding="1" cellspacing="0" width="100%"> 
 <tbody>
  <tr>
   <td width="30%">Pattern</td> 
   <td width="70%">Example</td> 
  </tr>
  <tr>
   <td><p><strong>Pattern</strong></p> <p>Lists containing form fields are merged or not converted to corresponding adaptive form components</p> <p><strong>Resolution</strong></p> <p>Use forms fields with clear boundaries or use Review and Correct editor to fix such issues.</p> </td> 
   <td><img src="assets/lists-with-fields.png" /></td> 
  </tr>
  <tr>
   <td><p><strong>Pattern</strong></p> <p>Service can leave a few nested lists unidentified</p> <p> </p> <p><strong>Resolution</strong></p> <p>Use Review and Correct editor to fix such issues.</p> </td> 
   <td><img src="assets/nested-lists.png" /> </td> 
  </tr>
  <tr>
   <td><p><strong>Pattern</strong></p> <p>Service merges some lists containing choice groups with each other</p> <p><strong>Resolution</strong></p> <p>Use Review and Correct editor to fix such issues.</p> </td> 
   <td><img src="assets/lists-containing-choice-groups.png" /> </td> 
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
<li>Form fiields without bordes are not supported.</li>
<li>Hidden form fields are not supported.</li>
<li>Button in PDF forms are not converted to adaptive form buttons.<br /> </li>
<li>Tables with clear explicit boundaries and borders are supported.</li>
<li>Fields with far away captions are not supported.<br /> </li>
<li>Choice groups with only box or circle shaped selectors are supported. </li>
</ul>
-->

