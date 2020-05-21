---
title: What's new? Release notes - Automated Forms Conversion Service
description: Learn about the latest features and bug fixed for Automated Forms Conversion Service 
---

# Release Notes

Automated Forms Conversion Service receives improvements on an ongoing basis. To stay up to date with the most recent developments, visit this page regularly. This page provides you with information about:

* Early Access
* Latest releases
* New features
* improvements
* Bug fixes
* Deprecated functionality
* Special instructions
* Future plans for changes

## 20 March 2020 (AFC-2020.03.1)

### Early Access

**Automatically detect logical sections in a form**

By default, the service creates a separate top-level panel for each page of a PDF form. Now, you can use the **[!UICONTROL Auto-detect logical sections]** option to drop page level panels (page number-based panels) and create only logical panels. It also clubs the fields which do not belong to any section with preceding logical section and fields of a logical section spread across two adjacent pages into a single logical section. For example, if some fields of a logical section are at the end of page one and some are in the starting of page two, all such fields are clubbed into a single logical section. 

### What's improved

**Improvements in list detection**

The service is now more efficient in detecting bulleted and numbered lists. 

### Special instructions

**Install Automated Forms Conversion Service Connector package**

You require the connector package 1.1.38 or above to use the latest features and improvements delivered in release AFC-2020.03.1. You can download the connector package from [AEM Package Share](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/featurepack/AFCS-Connector-2020.03.1).

If you already have an up and running Automated Forms Conversion service environment, to use the latest features of the conversion service, install the latest service pack, latest AEM Forms add-on package, and latest connector package in the mentioned order. For detailed instructions, see the [Configure the Automated Forms Conversion service](configure-service.md) article.