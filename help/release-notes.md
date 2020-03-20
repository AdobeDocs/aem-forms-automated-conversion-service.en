---
title: What's new? Release notes - Automated Forms Conversion Service
description: Learn about the latest features and bug fixed for Automated Forms Conversion Service 
---

# Automated Forms Conversion Service: Release Notes

Automated Forms Conversion Service receives improvements on an ongoing basis. To stay up to date with the most recent developments, visit this page regularly. This page provides you with information about:

* Latest releases
* New features
* Bug fixes
* Deprecated functionality
* Special instructions
* Future Plans for changes

This page is updated monthly, so revisit it regularly.

## 20 March 2020 (AFC-2020.03.1)

### What's New

**Automatically detect logical sections in a form**

By default, the service creates a separate top-level panel for each page of an input PDF form. Now, you can select the **[!UICONTROL Auto-detect logical sections]** option to remove the notion of creating a separate top-level panel for each PDF page and automatically detect logical sections. The service clubs related fields of a form to a logical section. For example, all fields related to the billing address are clubbed to one section and all fields related to the shipping address are clubbed to a different section. The service also creates a separate top-level panel for each automatically detected logical section.

### What's improved

**Improvements in list detection**

The service is now more efficient in detecting bulleted and numbered lists. It can now easily detect multi-level lists.

### Special instructions

**Install Automated Forms Conversion Service Connector package**

You require the connector package 1.1.38 or above to use the latest features and improvements delivered in release AFC-2020.03.1. You can download the connector package from [AEM Package Share](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/servicepack/fd/AEM-Forms-6.5.4.0-WIN).

If you already have an up and running Automated Forms Conversion service environment, to use the latest features of the conversion service, install the latest service pack, latest AEM Forms add-on package, and latest connector package in the aforementioned order. For detailed instructions, see the [Configure the Automated Forms Conversion service](configure-service.md) article.
