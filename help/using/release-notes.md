---
title: What's new? Release notes - Automated Forms Conversion Service
description: Learn about the latest features and bug fixed for Automated Forms Conversion Service
solution: Experience Manager Forms
feature: Adaptive Forms
topic: Administration
topic-tags: forms
role: Admin, Developer
level: Beginner, Intermediate
exl-id: fccafbc9-28c1-4736-922c-24d675b25213
TQID: https://experienceleague.adobe.com/5c2zcJqsjOyH--SIp-DbEyQtflWnBy67-ja0BZY8aC8
product_v2:
  - id: e8f6de9b-cf88-4405-8d10-15efa08c230e
    internal-label: Experience Manager Forms
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
    internal-label: Experience Manager
feature_v2:
  - id: d49d6117-dd89-469c-a774-cc96b7eee433
    internal-label: Administration
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
    internal-label: Beginner
topic_v2:
  - id: eddd9b14-83bd-4ff4-9072-54a4a484abb7
    internal-label: Administration
---
# Release Notes

Automated Forms Conversion Service receives improvements on an ongoing basis. To stay up to date with the latest developments, visit this page regularly. This page provides you with information about:

* Early Access
* Latest releases
* New features
* improvements
* Bug fixes
* Deprecated functionality
* Special instructions
* Future plans for changes

## 24 Feb 2022 (AFC-2022.02.0) {#feb-2022}

* Added capability to [automaticaly convert sections to fragments](convert-existing-forms-to-adaptive-forms.md) to help improve rendering speed of converted forms and makes it easier to load large forms in adaptive form editor.

## 29 Aug 2021 (AFC-2021.08.0) {#aug-2021}

* Added capability to convert PDF Forms in Italian  and Portuguese languages to an Adaptive Form.

## 29 July 2021 (AFC-2021.07.2) {#july-2021}

* Added capability to convert a PDF Form in French, German, and Spanish language to an Adaptive Form.

## 24 June 2021 (AFC-2021.06.2) {#june-2021}

### What's improved {#june-2021-improvements}

Improved accuracy for automatically detecting logical sections in the source forms and converting those into corresponding adaptive form panels.

## 03 Mar 2021 (AFC-2021.02.2) {#mar-2021}

### What's improved {#march-2021-improvements}

Improvements in organizing form content into choice groups and fields while converting a source form to an adaptive form.

## 02 Feb 2021 (AFC-2021.01.2) {#feb-2021}

### What's improved {#feb-2021-improvements}

Improvements in organizing form content into panels and generating titles for panels while converting a source form to an adaptive form.

## 16 July 2020 (AFC-2020.07.2) {#jul-2020}

### What's New {#whats-new-jul-2020-}

Added support to convert colored PDF forms to adaptive forms.

### What's improved {#jul-2020-improvements}

Improvements in the automated conversion of text, form, and choice group fields to corresponding adaptive form components.  

## 20 March 2020 (AFC-2020.03.1) {#mar-2020}

### Early Access {#early-access}

**Automatically detect logical sections in a form**

By default, the service creates a separate top-level panel for each page of a PDF form. Now, you can use the **[!UICONTROL Auto-detect logical sections]** option to drop page level panels (page number-based panels) and create only logical panels. It also clubs the fields which do not belong to any section with preceding logical section and fields of a logical section spread across two adjacent pages into a single logical section. For example, if some fields of a logical section are at the end of page one and some are in the starting of page two, all such fields are clubbed into a single logical section.

### What's improved {#mar-2020-improvements}

**Improvements in list detection**

The service is now more efficient in detecting bulleted and numbered lists.

### Special instructions {#special-instructions}

**Install Automated Forms Conversion Service connector package**

You require the connector package 1.1.38 or above to use the latest features and improvements delivered in release AFC-2020.03.1.

If you already have an up and running Automated Forms Conversion service environment (AEM 6.5 or AEM 6.5 LTS), to use the latest features of the conversion service, install the latest service pack, latest AEM Forms add-on package, and latest connector package in the mentioned order. For AEM Forms as a Cloud Service, updates are delivered automatically. For detailed instructions, see the [Configure the Automated Forms Conversion service](configure-service.md) article.

