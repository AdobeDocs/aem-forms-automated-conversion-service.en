---
title: Submit adaptive forms to database using Forms Portal
description: Extend the default meta-model to add pattern, validations, and entities specific to your organization and apply configurations to adaptive form fields while running the Automated Forms Conversion service.
uuid: f98b4cca-f0a3-4db8-aef2-39b8ae462628
topic-tags: forms
discoiquuid: cad72699-4a4b-4c52-88a5-217298490a7c
---

# Integrate adaptive forms with database using Forms Portal {#submit-forms-to-database-using-forms-portal}

Automated Forms Conversion service allows you to convert a non-interactive PDF form, an Acro Form, or an XFA based PDF form into an adaptive form. While initiating the conversion process, you have the option of generating an adaptive form either with or without data bindings.
If you select to generate an adaptive form without data bindings, you can integrate the converted adaptive form with a Form Data Model, XML schema, or a JSON schema after conversion. However, if you generate an adaptive form with data bindings, the conversion service automatically associates the adaptive form(s) with a JSON schema and creates a data binding between the fields available in the adaptive form and JSON schema. You can then integrate the adaptive form with a database of your choice, fill data in the form, and submit it to the database using the Forms Portal.

The following figure depicts different stages of integrating a converted adaptive form with a database using Forms Portal:

![database integration](assets/database_integration.gif)

This article describes the step-by-step instructions to successfully execute all these integration stages.
The sample, discussed in this article, is a reference implementation of customized data and metadata services to integrate a Forms Portal page with a database. The database used in the sample implementation is MySQL 5.6.24. However, you can integrate Forms Portal page with any database of your choice.

## Pre-requisites {#pre-requisites}

* AEM 6.5 author instance with latest AEM 6.5 Service Pack
* Latest version of the AEM Forms add-on package
* [Automated Forms Conversion service](configure-service.md)
* A database to integrate with. The database used in the sample implementation is MySQL 5.6.24. However, you can integrate Forms Portal with any database of your choice.

## Set up connection between AEM instance and database {#set-up-connection-aem-instance-database}

Setting up a connection between an AEM instance and a MYSQL database consists of:

* [Installing a MYSQL connector package](#install-mysql-connector-java-file)

* [Creating schema and tables in the database](#create-schema-and-tables-in-database)

* [Configuring connection settings](#configure-connection-between-aem-instance-and-database)

* [Setting up and configuring the sample package for Forms Portal integration](#set-up-and-configure-sample)

### Install mysql-connector-java-5.1.39-bin.jar file {#install-mysql-connector-java-file}

Perform the following steps, on all the author and publish instances, to install the mysql-connector-java-5.1.39-bin.jar file:

1. Navigate to http://[server]:[port]/system/console/depfinder and search for com.mysql.jdbc package.
1. In the Exported by column, check if the package is exported by any bundle. Proceed if the package is not exported by any bundle.
1. Navigate to http://[server]:[port]/system/console/bundles and click **[!UICONTROL Install/Update]**.
1. Click **[!UICONTROL Choose File]** and browse to select the mysql-connector-java-5.1.39-bin.jar file. Also, select **[!UICONTROL Start Bundle]** and **[!UICONTROL Refresh Packages]** checkboxes.
1. Click **[!UICONTROL Install]** or **[!UICONTROL Update]**. Once complete, restart the server.
1. (Windows only) Turn off the system firewall for your operating system.

### Create schema and tables in the database {#create-schema-and-tables-in-database}

Perform the following steps to create schema and tables in the database:

1. Create a schema in the database using the following SQL statement:

    ```sql
    CREATE SCHEMA `formsportal` ;
    ```
    where **formsportal** refers to the name of the schema.

1. Create a **data** table in the database schema using the following SQL statement:

   ```sql
    CREATE TABLE `data` (
        `owner` varchar(255) DEFAULT NULL,
        `data` longblob,
        `metadataId` varchar(45) DEFAULT NULL,
        `id` varchar(45) NOT NULL,
        PRIMARY KEY (`id`)
        ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
    ```

1. Create a **metadata** table in the database schema using the following SQL statement:

    ```sql
    CREATE TABLE `metadata` (
        `formPath` varchar(1000) DEFAULT NULL,
        `formType` varchar(100) DEFAULT NULL,
        `description` text,
        `formName` varchar(255) DEFAULT NULL,
        `owner` varchar(255) DEFAULT NULL,
        `enableAnonymousSave` varchar(45) DEFAULT NULL,
        `renderPath` varchar(1000) DEFAULT NULL,
        `nodeType` varchar(45) DEFAULT NULL,
        `charset` varchar(45) DEFAULT NULL,
        `userdataID` varchar(45) DEFAULT NULL,
        `status` varchar(45) DEFAULT NULL,
        `formmodel` varchar(45) DEFAULT NULL,
        `markedForDeletion` varchar(45) DEFAULT NULL,
        `showDorClass` varchar(255) DEFAULT NULL,
        `sling:resourceType` varchar(1000) DEFAULT NULL,
        `attachmentList` longtext,
        `draftID` varchar(45) DEFAULT NULL,
        `submitID` varchar(45) DEFAULT NULL,
        `id` varchar(60) NOT NULL,
        `profile` varchar(255) DEFAULT NULL,
        `submitUrl` varchar(1000) DEFAULT NULL,
        `xdpRef` varchar(1000) DEFAULT NULL,
        `agreementId` varchar(255) DEFAULT NULL,
        `nextSigners` varchar(255) DEFAULT NULL,
        `eSignStatus` varchar(45) DEFAULT NULL,
        `pendingSignID` varchar(45) DEFAULT NULL,
        `agreementDataId` varchar(255) DEFAULT NULL,
        `enablePortalSubmit` varchar(45) DEFAULT NULL,
        `submitType` varchar(45) DEFAULT NULL,
        `dataType` varchar(45) DEFAULT NULL,
        `jcr:lastModified` varchar(45) DEFAULT NULL,
        PRIMARY KEY (`id`),
        UNIQUE KEY `ID_UNIQUE` (`id`)
        ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
    ```

1. Create a **additionalmetadatatable** table in the database schema using the following SQL statement:

    ```sql
    CREATE TABLE `additionalmetadatatable` (
        `value` text,
        `key` varchar(255) NOT NULL,
        `id` varchar(60) NOT NULL,
        PRIMARY KEY (`id`,`key`),
        CONSTRAINT ‘additionalmetadatatable_fk’ FOREIGN KEY (`id`) REFERENCES `metadata` (`id`) ON DELETE CASCADE
        ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
    ```

1. Create a **commenttable** table in the database schema using the following SQL statement:

    ```sql
    CREATE TABLE `commenttable` (
        `commentId` varchar(255) DEFAULT NULL,
        `comment` text DEFAULT NULL,
        `ID` varchar(255) DEFAULT NULL,
        `commentowner` varchar(255) DEFAULT NULL,
        `time` varchar(255) DEFAULT NULL);
    ```

### Configure connection between AEM instance and database {#configure-connection-between-aem-instance-and-database}

Perform the following configuration steps to create a connection between AEM instance and the MYSQL database:

1. Go to AEM Web Console Configuration page at *http://[host]:[port]/system/console/configMgr*.
1. Click to open **[!UICONTROL Forms Portal Draft and Submission Configuration]** in edit mode.
1. Specify the values for properties as described in the following table:

    <table> 
    <tbody> 
    <tr> 
    <th><strong>Property</strong></th> 
    <th><strong>Description</strong></th>
    <th><strong>Value</strong></th> 
    </tr> 
    <tr> 
    <td><p>Forms Portal Draft Data Service</p></td> 
    <td><p>Identifier for draft data service</p></td>
    <td><p>formsportal.sampledataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Forms Portal Draft Metadata Service</p></td> 
    <td><p>Identifier for draft metadata service</p></td>
    <td><p>formsportal.samplemetadataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Forms Portal Submit Data Service</p></td> 
    <td><p>Identifier for submit data service</p></td>
    <td><p>formsportal.sampledataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Forms Portal Submit Metadata Service</p></td> 
    <td><p>Identifier for submit metadata service</p></td>
    <td><p>formsportal.samplemetadataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Forms Portal Pending Sign Data Service</p></td> 
    <td><p>Identifier for Pending Sign data service</p></td>
    <td><p>formsportal.sampledataservice</p></td> 
    </tr>
    <tr> 
    <td><p>Forms Portal Pending Sign Metadata Service</p></td> 
    <td><p>Identifier for Pending Sign metadata service</p></td>
    <td><p>formsportal.samplemetadataservice</p></td> 
    </tr>
    </tbody> 
    </table>
1. Leave other configurations as is and click **[!UICONTROL Save]**.
1. Find and click to open **[!UICONTROL Apache Sling Connection Pooled DataSource]** in edit mode in the Web Console Configuration. Specify the values for properties as described in the following table:

    <table> 
    <tbody> 
    <tr> 
    <th><strong>Property</strong></th> 
    <th><strong>Value</strong></th> 
    </tr> 
    <tr> 
    <td><p>Datasource name</p></td> 
    <td><p>A datasource name for filtering drivers from the data source pool. The sample implementation uses FormsPortal as the datasource name.</p></td>
    </tr>
    <tr> 
    <td><p>JDBC driver class</p></td> 
    <td><p>com.mysql.jdbc.Driver</p></td>
    </tr>
    <tr> 
    <td><p>JDBC connection URI</p></td> 
    <td><p>jdbc:mysql://[host]:[port]/[schema_name]</p></td>
    </tr>
    <tr> 
    <td><p>Username</p></td> 
    <td><p>A username to authenticate and perform actions on database tables</p></td>
    </tr>
    <tr> 
    <td><p>Password</p></td> 
    <td><p>Password associated with the username</p></td>
    </tr>
    <tr> 
    <td><p>Transaction Isolation</p></td> 
    <td><p>READ_COMMITTED</p></td>
    </tr>
    <tr> 
    <td><p>Max Active Connections</p></td> 
    <td><p>1000</p></td>
    </tr>
    <tr> 
    <td><p>Max Idle Connections</p></td> 
    <td><p>100</p></td>
    </tr>
    <tr> 
    <td><p>Min Idle Connections</p></td> 
    <td><p>10</p></td>
    </tr>
    <tr> 
    <td><p>Initial Size</p></td> 
    <td><p>10</p></td>
    </tr>
    <tr> 
    <td><p>Max Wait</p></td> 
    <td><p>100000</p></td>
    </tr>
     <tr> 
    <td><p>Test on Borrow</p></td> 
    <td><p>Checked</p></td>
    </tr>
     <tr> 
    <td><p>Test while Idle</p></td> 
    <td><p>Checked</p></td>
    </tr>
     <tr> 
    <td><p>Validation Query</p></td> 
    <td><p>Example values are SELECT 1(mysql), select 1 from dual(oracle), SELECT 1(MS Sql Server) (validationQuery)</p></td>
    </tr>
     <tr> 
    <td><p>Validation Query timeout</p></td> 
    <td><p>10000</p></td>
    </tr>
    </tbody> 
    </table>

### Set up and configure the sample {#set-up-and-configure-sample}

Perform the following steps, on all the author and publish instances, to install and configure the sample:

1. Download the following **aem-fp-db-integration-sample-pkg-6.1.2.zip** package to your file system.

    [Get File](assets/aem-fp-db-integration-sample-pkg-6.1.2.zip)

1. Go to AEM package manager at *http://[host]:[port]/crx/packmgr/*.
1. Click **[!UICONTROL Upload Package]**.
1. Browse to select the **aem-fp-db-integration-sample-pkg-6.1.2.zip** package and click **[!UICONTROL OK]**.
1. Click **[!UICONTROL Install]** next to the package to install the package.

## Configure the converted adaptive form for Forms Portal integration {#configure-converted-adaptive-form-for-forms-portal-integration}

Execute the following steps to enable adaptive form submission using the Forms Portal page:
1. [Run the conversion](convert-existing-forms-to-adaptive-forms.md#start-the-conversion-process) to convert a source form into an adaptive form.
1. Open the adaptive form in edit mode.
1. Tap Form Container and select Configure ![Configure adptive form](assets/configure-adaptive-form.png).
1. In the **[!UICONTROL Submission]** section, select **[!UICONTROL Forms Portal Submit Action]** from the **[!UICONTROL Submit Action]** drop-down list.
1. Tap ![Save template policy](assets/edit_template_done.png) to save the settings.

## Create and configure the Forms Portal page {#create-configure-forms-portal-page}

Perform the following steps to create a Forms Portal page and configure it so that you can submit adaptive forms using this page:

1. Log on to the AEM author instance and tap **[!UICONTROL Adobe Experience Manager]** >  **[!UICONTROL Sites]**.
1. Select the location where you want to save the new Forms Portal page and tap **[!UICONTROL Create]** > **[!UICONTROL Page]**.
1. Select the template for the page, tap **[!UICONTROL Next]**, specify a title for the page and tap **[!UICONTROL Create]**.
1. Tap **[!UICONTROL Edit]** to configure the page.
1. In the page header, tap ![Edit template](assets/edit_template_sites.png)  > **[!UICONTROL Edit Template]** to open the template of the page.
1. Tap Layout Container and tap ![Edit template policy](assets/edit_template_policy.png). In the **[!UICONTROL Allowed Components]** tab, enable the **[!UICONTROL Document Services]** and **[!UICONTROL Document Services Predicates]** options, and tap ![Save template policy](assets/edit_template_done.png).
1. Insert **[!UICONTROL Search & Lister]** component in the page. As a result, all existing adaptive forms available on your AEM instance are listed on the page.
1. Insert **[!UICONTROL Drafts & Submissions]** component in the page. Two tabs, **[!UICONTROL Draft Forms]** and **[!UICONTROL Submitted Forms]**, display on the Forms Portal page. The **[!UICONTROL Draft Forms]** tab also displays the converted adaptive form generated using the steps mentioned in [Configure the converted adaptive form for Forms Portal integration](#configure-converted-adaptive-form-for-forms-portal-integration)

1. Tap **[!UICONTROL Preview]**, tap the converted adaptive form, specify values for adaptive form fields and submit it. The values that you specify for adaptive form fields get submitted to the integrated database.
