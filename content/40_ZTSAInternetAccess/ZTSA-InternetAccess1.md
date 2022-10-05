---
title: "ZTSA - Internet Access Control"
chapter: false
weight: 41
pre: "<b>4.1 </b>"
---
## ZTSA – Internet Access Control 

### Activating the ZTSA Module
To allow the users to access the Internet using the Zero Trust Infrastructure, the ZTSA Module is required to be installed and activated. 

The first step that must be executed is the deployment of the ZTSA Module to the VPC2_WindowsClient. You can do that using the Zero Trust Secure Access > Secure Access Configuration > Secure Access Module menu and selecting the new Windows Instance and select Deploy Module.

After you select the Deploy Module option, you can monitor the ZTSA Module Installation by monitoring the Task Manager on the VPC2_WindowsClient Instance. The installation process usually takes 2 to 3 minutes.
![Endpoint_Deployment](/images/ztsa-module.png)

The ZTSA Module deployment requires normally 3 to 5 minutes to be finished. After the deployment is done, you will find a new Trend Micro ZTSA shortcut on the VPC2_WindowsClient desktop.
![Endpoint_Deployment](/images/ztsa-module-desktop.png)

---

### ZTSA – Internet Access Control - Creating the First Policy
Configure an internet access control rule to protect your users' internet access whether they are on or off your corporate network.

On the Secure Access Rules screen, click the Internet Access Control tab, then click Create Rule and follow the instructions described below:
![Endpoint_Deployment](/images/ztsa-internet1.png)

        _Basic information
        Rule Name: Zero Trust Internet Access Rule

        _Source
        User/Groups/Private IP Groups: All users/groups

        Locations: All locations

        _Traffic
        URLs/Cloud Apps: Any traffic

        File types: Any file

        _Schedule
        Schedule: Always

        _Action
        Access Control: Monitor URL/Cloud app access

        Advanced security settings: x Enable Threat Protection / Default Threat Protection Rule

---


### ZTSA – Internet Access Control - Testing the Solution
Now that the ZTSA Internet Access Module is enabled, you will find a green status on the ZTSA Client. That means all he internet traffic is being inspected by Trend Micro, and any security risk should be detected and blocked.
![Endpoint_Deployment](/images/ztsa-internet-status.png)

You can access the following URL (https://wicar.org/test-malware.html) and then check the SSL Certificate used by this application. You will find the original certificate was replaced by the Trend Micro Web Security certificate, which means even the SSL traffic is being analyzed, and any security risk should/could be stopped by the ZTSA Internet Access Infrastructure.
![Endpoint_Deployment](/images/ztsa-internet-2.png)

Now its time to access malicious URLs and download malicious files. You can do this test using the files available on https://wicar.org/test-malware.html. 
![Endpoint_Deployment](/images/ztsa-internet-3.png)
![Endpoint_Deployment](/images/ztsa-internet-4.png)
![Endpoint_Deployment](/images/ztsa-internet-5.png)

---
### ZTSA - Internet Access - Configuring the Zero Trust Secure Access Rules (Automated Respose)
Now its time to demonstrate that the Trend Micro Zero Trust Platform is capable to continuously monitor all the activities happening on the monitored endpoint. If an malicious or abnormal behavior if detected (like a malware download), a Secure Access Rule could trigger an automated remediation (Example: Isolating the affected Endpoint, Restricting the access to Private Applications, Interacting with Azure AD to disable the affected user account, etc).

In this demo we are going to simulate some suspicious activity (access to a malicious website). This event will trigger a Secure Access Rule / Risk Control Rule that will isolate the VPC2_WindowsClient Instance.

![Endpoint_Deployment](/images/ztsa-internet-6.png)
![Endpoint_Deployment](/images/ztsa-internet-7.png)
![Endpoint_Deployment](/images/ztsa-internet-8.png)