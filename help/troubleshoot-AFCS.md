---
title: Troubleshoot Automated Forms Conversion Service 
seo-title: Troubleshoot Automated Forms Conversion Service (AFCS) 
description: Common AFCS issues and their solutions 
seo-description: Common AFCS issues and their solutions
contentOwner: khsingh
topic-tags: forms
---

# Troubleshoot Automated Forms Conversion Service


The article provides information on installation, configuration and administration issues that may arise in an Automated Forms Conversion Service production environment. The document also provides basic troubleshooting steps and explanation for common error messages. 

## Common errors {#commonerrors}

|Error|Example|
|--- |--- |
|**Error Message** <br> The access token header is not available. <br><br>**Reason** <br> An administrator has created multiple IMS configurations or IMS configuration is not able to reach AFCS service on Adobe Cloud. <br><br>**Resolution** <br> If there are multiple configurations, delete all the configurations and [create a new configuration](configure-service.md#obtainpubliccertificates). <br> If there is single configuration, use **[!UICONTROL Health Check]** to [check connectivity](configure-service.md#createintegrationoption).|![The access token header is not available](assets/invalid-ims-configuration.png)|
|**Error Message** <br> Unable to connect to the service.  <br><br>**Reason** <br> Incorrect service URL or no service URL is mentioned in Automated Forms Conversion Service cloud services. <br><br>**Resolution** <br> Correct [Service URL](configure-service.md#configure-the-cloud-service) in Automated Forms Conversion Service Cloud services.|![Unable to connect to the service.](assets/wrong-endpoint-configured.png)|
|**Error Message** <br> The service failed to convert the form.  <br><br>**Reason** <br> Network connectivity issues at your end or  the service is down due to scheduled maintenance or outage on Adobe Cloud. <br><br>**Resolution** <br> Resolve network connectivity issues at your end and check status of the service on https://status.adobe.com/# for planned or unplanned outage.|![Unable to connect to the service.](assets/service-failure.png)|