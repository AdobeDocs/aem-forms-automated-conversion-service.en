---
title: Configure the Automated Forms Conversion service
description: Ready your AEM instance to use Automated Forms Conversion service
---

# Configure the Automated Forms Conversion service {#about-this-help}

This help describes how an AEM administrator can configure Automated Forms Conversion service to automate conversion of their PDF forms to adaptive forms. This help is for IT and AEM administrators at your organization. The information provided is based on the assumption that anyone reading this Help is familiar with the following technologies:

* Installing, configuring, and administering Adobe Experience Manager and AEM packages,

* Using Linux and Microsoft Windows operating systems,

* Configuring SMTP mail servers

>[!VIDEO](https://video.tv.adobe.com/v/29267/)

**Watch the video or read the article to configure Automated Forms Conversion service**

## Onboarding{#onboarding}

The service is available for free to AEM 6.4 Forms and AEM 6.5 Forms On-Premise term customers and Adobe Managed Service enterprise customers. You can contact Adobe Sales team or your Adobe representative to request access to the service.

Adobe enables access for your organization and provide required privileges to the person designated as administrator in your organization. The administrator can grant access to your AEM Forms developers (users) of your organization to connect to the service.

## Prerequisites {#prerequisites}

You require the following to use the Automated Forms Conversion Service:

* Automated Forms Conversion service is enabled for your organization
* An Adobe ID account with administrator privileges for the conversion service
* An up and running AEM 6.4 or AEM 6.5 author instance with latest AEM Service Pack
* An AEM user (on your AEM instance) which is member of forms-user group

## Set up the environment {#setuptheservice}

Before using the service, prepare your AEM author instance to connect to the service running on Adobe Cloud. Perform the following steps in the listed sequence to prepare your instance for the service:

1. [Download and install AEM 6.4 or AEM 6.5](#aemquickstart)
1. [Download and install latest AEM Service Pack](#servicepack)
1. [Download and install latest AEM Forms add-on package](#downloadaemformsaddon)
1. [Download and install latest connector package](#installConnectorPackage)
1. [Create custom themes and templates](#referencepackage)

### Download and install AEM 6.4 or AEM 6.5 {#aemquickstart}


Automated Forms Conversion service runs on AEM author instance. You require AEM 6.4 or AEM 6.5 to set up an AEM author instance. If you do not have AEM up and running, download it from the following locations:

* If you are an existing AEM customer, download AEM 6.4 or AEM 6.5 from [Adobe Licensing website](http://licensing.adobe.com).

* If you are an Adobe partner, use [Adobe Partner Training Program](https://adobe.allegiancetech.com/cgi-bin/qwebcorporate.dll?idx=82357Q) to request AEM 6.4 or AEM 6.5.

After you download AEM, for instructions to set up an AEM author instance, see [deploying and maintaining](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/deploy.html#defaultlocalinstall).

### Download and install AEM latest Service Pack {#servicepack}

Download and install latest AEM Service Pack. For detailed instructions see,  or [AEM 6.4 Service Pack Release Notes](https://helpx.adobe.com/experience-manager/6-4/release-notes/sp-release-notes.html) or [AEM 6.5 Service Pack Release Notes](https://helpx.adobe.com/experience-manager/6-5/release-notes/sp-release-notes.html).

### Download and install AEM Forms add-on package  {#downloadaemformsaddon}

An AEM instance contains basic forms capabilities. The conversion service requires full capabilities of AEM Forms. Download and install AEM Forms add-on package to avail all the capabilities of AEM Forms. The package is required to set up and run the conversion service. For detailed instructions, see [Install and configure data capture capabilities.](https://helpx.adobe.com/experience-manager/6-5/forms/using/installing-configuring-aem-forms-osgi.html)

>[!NOTE]
> Ensure that you perform the mandatory post-installation configurations after installing the add-on package.
>

### Download and install connector package  {#installConnectorPackage}

You require the connector package 1.1.38 or above to use the latest features and improvements delivered in release AFC-2020.03.1. You can [download the connector package from AEM Package Share](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq650/featurepack/AFCS-Connector-2020.03.1).

>[!NOTE]
> If you already have an up and running Automated Forms Conversion service environment, to use the latest features of the conversion service, install the latest service pack, latest AEM Forms add-on package, and latest connector package in the mentioned order.


### Create custom themes and templates {#referencepackage}

If you start AEM in [production mode](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/production-ready.html) (nosamplecontent runmode), the reference packages are not installed. The reference packages contain sample themes and templates. Automated Forms Conversion service requires at least one theme and one template to convert a PDF forms to an adaptive form. Create a custom theme and template of your own and point [service configuration](#configure-the-cloud-service) to use custom templates and themes before using the service.

## Configure the service {#configure-the-service}

Before you proceed to configure the service and connect your local instance with the service running on Adobe Cloud, learn about the personas and privileges required to connect to the service. The service uses two different types of personas, administrators and developers:

* **Administrators**: Administrators are responsible for managing Adobe software and services for their organization. Administrators grant access to developers in their organization to connect to Automated Forms Conversion service running on Adobe Cloud. When an administrator is provisioned for an organization, the administrator receives an email with title **[!UICONTROL 'You now have administrator rights to manage Adobe software and services for your organization']**. If you are an administrator, check your mailbox for email with aforementioned title and proceed to [grant access to developers of your organization](#adduseranddevs).

![admin access grant email](assets/admin-console-adobe-io-access-grantedx75.png)

* **Developers**: A developer connects a local AEM Forms author instance to Automated Forms Conversion service running on Adobe Cloud. When an administrator grants rights to a developer to connect to Automated Forms Conversion service, an email with title You now have developer access to manage Adobe API integrations for your organization is sent to the developer. If you are a developer, check your mailbox for email with aforementioned title and proceed to [Connect your local AEM instance to Automated Forms Conversion service on Adobe Cloud.](#connectafcadobeio)  
  
![developer access grant email](assets/email-developer-accessx94.png)  

### (For administrators only) Grant access to developers of your organization {#adduseranddevs}

After Adobe enables access for your organization and provides required privileges to the administrator, the administrator can log into Admin Console (detailed instructions below), create a profile, and add developers to the profile. Developers can connect a local instance of AEM Forms to Automated Forms Conversion service on Adobe Cloud.

Developers are members of your organization designated to run the conversion service. Only those developers which are added to Adobe Automated Forms Conversion service profile are entitled to use the Automated Forms Conversion service. Perform the below steps to create a profile and add developers to it:

1. Log in to [Admin Console](https://adminconsole.adobe.com/). Use **Adobe ID** of administrator provisioned to use Automated Forms Conversion service to login. Do not any other ID or Federated ID to login.
1. Click the **[!UICONTROL Automated Forms Conversion]** option.
1. Click **[!UICONTROL New Profile]** in the **[!UICONTROL Products]** tab.
1. Specify **[!UICONTROL Name]**, **[!UICONTROL Display Name]**, and **[!UICONTROL Description]** for the profile. Click **[!UICONTROL Done]**. A profile is created.

   ![Specify details for the new profile.](assets/create-new-profile-details.png)

1. Add developer to the profile. To add the developers:
   1. In the [Admin Console](https://adminconsole.adobe.com/enterprise), navigate to the Overview tab.
   1. Click **[!UICONTROL Assign Developers]** on the required product card.
   1. Enter the developers email address and, optionally, first and last names.
   1. Select product profiles. Tap **[!UICONTROL Save]**.

Repeat above steps for all the users.  For more details about adding developers,see [Manage developers](https://helpx.adobe.com/enterprise/using/manage-developers.html).

Once an administrator adds developers to Adobe I/O profile, the developers are notified via email. After receiving the email, the developers can proceed to [connect a local AEM Forms instance with Automated Forms Conversion service on Adobe Cloud](#connectafcadobeio).

### (For developers only) Connect your local AEM Forms instance to Automated Forms Conversion service on Adobe Cloud {#connectafcadobeio}

After an administrator provides you developer access, you can connect your local AEM Forms instance to Automated Forms conversion service running on Adobe Cloud. Perform the following steps in the listed sequence to connect your AEM Forms instance to the service:

* [Configure email notifications](configure-service.md#configureemailnotification)
* [Add user to the forms-users group](#adduserstousergroup)
* [Obtain public certificates](#obtainpubliccertificates)
* [Create Adobe I/O integration](#createintegration)
* [Configure the cloud service](configure-service.md#configure-the-cloud-service)

#### Configure email notification {#configureemailnotification}

Automated Forms Conversion service uses the Day CQ mail service to send email notifications. These email notifications contain information about successful or failed conversions. If you choose not receive notification, skip these steps. Perform the following steps to configure the Day CQ Mail Service:

1. Go to AEM configuration manager at `http://localhost:4502/system/console/configMgr`
1. Open the Day CQ Mail Service configuration. Specify a value for the **[!UICONTROL SMTP server host name]**, **[!UICONTROL SMTP server port]**, and **[!UICONTROL From address]** fields. Click **[!UICONTROL Save]**.

   You can contact your email service provider or IT administrator for information about host name and port of SMTP server. You can use any valid email address in the from field. For example, notification@example.com or donotreply@example.com.

1. Open the **[!UICONTROL Day CQ Link Externalizer]** configuration. In the **[!UICONTROL Domains]** field, specify the actual host name or IP address and port number for local, author, and publish instances. Click **[!UICONTROL Save]**.

#### Add user to the forms-users group {#adduserstousergroup}

Specify an email address in the profile of the AEM user designated to run the service. Ensure that the user is the member of the [forms user](https://helpx.adobe.com/experience-manager/6-4/forms/using/forms-groups-privileges-tasks.html) group. Emails are sent to the email address of user running the conversion. To specify an email address for the user and add user to the forms user group:

1. Log in to your AEM Forms author instance as an AEM administrator. Use your local AEM credentials to login. Do not use Adobe ID to login. Tap **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Users]**.

1. Select a user designated to run the conversion service and tap **[!UICONTROL Properties]**. The Edit User Settings page opens.
1. Specify an email address in the **[!UICONTROL Email]** field and tap **[!UICONTROL Save]**. The emails are sent to specified email address on successful completion or failure of the conversion.
1. Tap the **Groups** tab. In the select group tab, type and select the **forms-users** group. Tap **Save & Close**. The user is now a member of the forms-users group.

#### Obtain public certificates {#obtainpubliccertificates}

A public certificate allows you to authenticate your profile on Adobe I/O.

1. Log in to your AEM Forms author instance. Navigate to **[!UICONTROL Tools]**> **[!UICONTROL Security]** > **[!UICONTROL Adobe IMS Configurations]**. Tap **[!UICONTROL Create]**. The **[!UICONTROL Adobe IMS Technical Account Configuration]** page appears.

   ![The Adobe IMS Technical Account Configuration page](assets/adobe-ims-technical-account-configuration.png)

1. Select **[!UICONTROL Automated Forms Conversion Service]** in Cloud Solution.  

1. Select the **[!UICONTROL Create new certificate]** check box and specify an alias. The alias serves as name of the dialog. Tap **[!UICONTROL Create certificate]**. A dialog appears. Click **[!UICONTROL OK]**. The certificate is created.

1. Tap **[!UICONTROL Download Public Key]** and save the *AEM-Adobe-IMS.crt* certificate file on your machine. The certificate file is used to [create integration on Adobe I/O Console](#createintegration). Tap **[!UICONTROL Next]**.  

1. Specify the below:

    * Title: Specify a title.  
    * Authorization Server: [https://ims-na1.adobelogin.com](https://ims-na1.adobelogin.com)

   Leave the other fields blank for now (to be provided later). Keep the page open.

   <!--
   Comment Type: draft

   <li> </li>
   -->

   <!--
   Comment Type: draft

   <li>Step text</li>
   -->

#### Create Adobe I/O integration {#createintegration}

To use Automated Forms Conversion service, create an integration in Adobe I/O. The integration generates API Key, Client Secret, Payload (JWT).

1. Log in to [https://console.adobe.io/](https://console.adobe.io/). Use your Adobe ID, developer account that your administrator has provisioned to login to Adobe I/O console to login.

1. Tap **[!UICONTROL View Integrations]**. A screen with all the available integrations appears.
1. Select your organization from the drop-down under **[!UICONTROL Integrations]**. Tap **[!UICONTROL New Integration]**, select **[!UICONTROL Access an API]**, and tap **[!UICONTROL Continue]**.
1. Select **[!UICONTROL Experience Cloud]** > **[!UICONTROL Automated Forms Conversion]** and tap **[!UICONTROL Continue]**. If the Automated Forms Conversion option is disabled for you, ensure that you have selected correct organization from the drop-down box above the **[!UICONTROL Adobe Services]** option. If you do not know your organization, contact your administrator.

   ![Select Automated Forms Conversion](assets/create-new-integration.png)

1. Specify name and description for the integration. Tap **[!UICONTROL Select a File from your computer]** and upload the AEM-Adobe-IMS.crt file downloaded in the [Obtain Public Certificates](#obtainpubliccertificates) section.
1. Select the profile created while [granting access to developers of your organization](#adduseranddevs) and tap **[!UICONTROL Create Integration]**. The integration is created.
1. Tap **[!UICONTROL Continue to integration details]** to view the integration information. The page contains API Key, Client Secret, and other information required to connect your local AEM instance to Automated Forms Conversion service. The information on the page is used to create IMS configuration on your local machine.

   ![API Key, Client Secret, and payload information of an integration](assets/integration-details.png)

1. Open the IMS Configuration page on your local instance. You kept the page open at the end of section, [Obtain public certificate](#obtainpubliccertificates).

   ![Specify Title, API Key, Client Secret, and payload ](assets/ims-configuration-details.png)

1. On the Adobe IMS Technical page, specify API Key and Client Secret. Use the values specified on the integration page.

   **For payload, use the code provided in the JWT tab of the integration page.** Tap  **[!UICONTROL Save]**. The IMS configuration is created. Close the integration page.

   ![Use values of JWT field for payload field](assets/jwt.png)

   >[!CAUTION]
   >
   >Create only one IMS configuration. Do not create more than one IMS configurations.

1. Select the IMS configuration and tap **[!UICONTROL Check Health]**. A dialog box appears. Tap **[!UICONTROL Check]**. On successful connection, the *Token retrieved successfully* message appears.

   ![On successful connection, the token retrieved successfully message appears. ](assets/health-check.png)

   <br/> <br/>

#### Configure the cloud service {#configure-the-cloud-service}

Create a cloud service configuration to connect your AEM instance to the conversion service. It also allows you to specify a template, theme, and form fragments for a conversion. You can create multiple cloud service configurations separate for each set of forms. For example, you can have a separate configuration for sales department forms and a separate one for customer support forms. Perform the following steps to create a cloud service configuration:

1. On your AEM Forms instance, tap **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Tools]**> **[!UICONTROL Cloud Services]** > **[!UICONTROL Automate Forms Conversion Configuration]**.
1. Tap the **[!UICONTROL Global]** folder and tap **[!UICONTROL Create]**. The page to create Automated Forms Conversion configuration appears. The configuration is created in the Global folder. You can also create the configuration in a different folder that already exists or create a new folder for your configurations.

1. On the **[!UICONTROL Create Automated Forms Conversion Configuration]** page, specify value for the following fields and tap **[!UICONTROL Next]**.

   |Field|Description|
   |--- |--- |
   |Title|Unique title for the configuration. The title is displayed in the UI used to start conversion.|
   |Name|Unique name for the configuration. The configuration is saved in the CRX-Repository with the specified name. The name can be identical to the title.|
   |Thumbnail location|Location of the thumbnail for the configuration.|
   |Service URL|URL of the Automated Forms Conversion service on Adobe Cloud. Use the `https://aemformsconversion.adobe.io/` URL.|
   |Template|Default template to be applied to converted forms. You can always specify a different template before starting the conversion. A template contains basic structure and initial content for an adaptive form. You can choose a template from the templates provided out-of-the-box. You can also create a custom template.|
   |Theme|Default theme to be applied to converted forms. You can always specify a different theme before starting the conversion.  You can click the icon to choose a theme provided out-of the box. You can also create a custom theme.|
   |Existing Fragments|Location of existing fragments, if any.|
   |Custom Meta-model|Path of the .schema.json file of custom meta-model.|

   

1. In the **[!UICONTROL Advanced]** tab of the **[!UICONTROL Create Automated Forms Conversion Configuration]** page, specify value for the following field:

   <table>
   <thead>
   <tr>
   <th>Field</th>
   <th>Description</th>
   </tr>
   </thead>
   <tbody>
   <tr>
   <td >Generate Document of Record</td>
   <td>Select the option to automatically generate Document of Record for converted forms. The option is only for XFA-based forms (XDP and PDF Forms). When you enable the option, after submitting a form, you can allow your customers to keep a record, in print or in document format, of the information they have filled in the form for their future reference. This is referred to as a document of record.</td>
   </tr>
   <tr>
   <td>Enable Analytics</td>
   <td>Select the option to enable Adobe Analytics on all the converted forms. Before using the option, ensure Adobe Analytics is enabled for your AEM Forms instance.</td>
   </tr>
   </tbody>
   </table>

   * When the source is an XFA-based form with extension .XDP, then the output DOR retains the XFA layout, else the conversion service uses an out-of-the-box template to generate DOR for other XFA-based forms.
   * When an XFA form is submitted, submit data of the form is saved as an XML element or an attribute. For example, `<Amount currency="USD"> 10.00 </Amount>`. The currency is saved as an attribute and currency amount, 10.00 is saved as an element. Submit data of an adaptive form does not have attributes, it has only elements. So, when an XFA-based form is converted to adaptive form, the adaptive form submit data contains an element for each such attribute. For example,

   ```css
      {
         "Type": "Principal",

         "Amount": "10.00",

         "currency": "USD"
      }
   ```

1. Tap **[!UICONTROL Create]**. The cloud configuration is created. Your AEM Forms instance is ready to start converting legacy forms to adaptive forms.
