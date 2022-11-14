---
title: "ZTSA - Internet Access Control"
chapter: false
weight: 41
pre: "<b>4.1 </b>"
---
## ZTSA – Internet Access Control 

### Activating the ZTSA Module
<b>If you already deployed the ZTSA Module and still have access to the demo environment -Zero Trust Private Access-, you can skip this step.</b>

To allow the users to access the Internet using the Zero Trust Infrastructure, the ZTSA Module is required to be installed and activated. 

The first step that must be executed is the deployment of the ZTSA Module to the VPC2_WindowsClient. You can do that using the Zero Trust Secure Access > Secure Access Configuration > Secure Access Module menu and selecting the new Windows Instance and select Deploy Module.

After you select the Deploy Module option, you can monitor the ZTSA Module Installation by monitoring the Task Manager on the VPC2_WindowsClient Instance. The installation process usually takes 2 to 3 minutes.

The ZTSA Module deployment requires normally 3 to 5 minutes to be finished. After the deployment is done, you will find a new Trend Micro ZTSA shortcut on the VPC2_WindowsClient desktop.

{{< youtube id="5NyxhWz3Cf4" >}}

---

### ZTSA – Internet Access Control - Creating the First Policy
Configure an internet access control rule to protect your users' internet access whether they are on or off your corporate network.

 <b>- Internet Access Control rule</b>

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

Now that the ZTSA Internet Access Module is enabled, you will find a green status on the ZTSA Client. That means all he internet traffic is being inspected by Trend Micro, and any security risk should be detected and blocked.

You can access the following URL (https://wicar.org/test-malware.html) and then check the SSL Certificate used by this application. You will find the original certificate was replaced by the Trend Micro Web Security certificate, which means even the SSL traffic is being analyzed, and any security risk should/could be stopped by the ZTSA Internet Access Infrastructure.

Now its time to access malicious URLs and download malicious files. You can do this test using the files available on https://wicar.org/test-malware.html. 

<b>- Creating the Internet Access Control rule and testing the effectiviness of this component.</b>

{{< youtube id="-EwlmWmN3WU" >}}