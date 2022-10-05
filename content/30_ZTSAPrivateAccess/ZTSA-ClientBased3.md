---
title: "ZTSA - Client Based Access - part 3"
chapter: false
weight: 33
pre: "<b>3.3 </b>"
---
 
## ZTSA – Private Access Control - Testing the Solution

---
After you finish the Cloud Formation deployment, check the Outputs tab. Take notes of the VPC2_WindowsClient public IP address. You will later RDP to this computer.
![Endpoint_Deployment](/images/ztsa-cft-outputs.png)

Now its time to access the VPC2_WindowsClient Instance using RDP. If you don't remember the credentials you defined when you deployed the CFT, you can retrieve them by checking the Cloud Formation Template / Parameters tab.
![Endpoint_Deployment](/images/ztsa-rdp.png)

After accessing the VPC2_WindowsClient, you can try to access the following Web Applications running on the VPC1.
* Using Google Chrome: http://10.0.3.10
* Using Google Chrome: http://10.0.3.11
* Using Windows Explorer: \\\10.0.3.20
* Using the RDP Client: 10.0.3.20

You will find that none of them are accessible for you at this moment.

---
### Activating the ZTSA Module
To allow the remote user to access the Private Applications running on the network 10.0.3.*, the following instructions must be followed.

The first step that must be executed is the deployment of the ZTSA Module to the VPC2_WindowsClient. You can do that using the Zero Trust Secure Access > Secure Access Configuration > Secure Access Module menu and selecting the new Windows Instance and select Deploy Module.

After you select the Deploy Module option, you can monitor the ZTSA Module Installation by monitoring the Task Manager on the VPC2_WindowsClient Instance. The installation process usually takes 2 to 3 minutes.
![Endpoint_Deployment](/images/ztsa-module.png)

The ZTSA Module deployment requires normally 3 to 5 minutes to be finished. After the deployment is done, you will find a new Trend Micro ZTSA shortcut on the VPC2_WindowsClient desktop.
![Endpoint_Deployment](/images/ztsa-module-desktop.png)

### Connecting to the Remote Applications

After the ZTSA Module installation is finished, you can log in to the ZTSA Module and find the applications available for you to access (use the AzureAD Account you listed as an authorized account when you created the ZTSA Access Policy).
![Endpoint_Deployment](/images/ztsa-connected.png)

Now its time try to access the applications running on VPC1 again. You will find they are all available for you to access now.
* Using Google Chrome: http://10.0.3.10
* Using Google Chrome: http://10.0.3.11
* Using Windows Explorer: \\\10.0.3.20
* Using the RDP Client: 10.0.3.20
![Endpoint_Deployment](/images/ztsa-connected2.png)

You can also check the Vision One / Secure Access History logs. You will find (the logs can take up to 5 minutes to be synchonized) the detection logs related to the tests you are executing.
![Endpoint_Deployment](/images/ztsa-internal-logs.png)


---
### Configuring the Zero Trust Secure Access Rules (Automated Respose)
Now its time to demonstrate that the Trend Micro Zero Trust Platform is capable to continuously monitor all the activities happening on the monitored endpoint. If an malicious or abnormal behavior if detected, a Secure Access Rule could trigger an automated remediation (Example: Isolating the affected Endpoint, Restricting the access to Private Applications, Interacting with Azure AD to disable the affected user account, etc). 

In this demo we are going to simulate some suspicious activity (T1113 - Screen Capture and Keylogging via Powershell). This event will trigger a Secure Access Rule / Risk Control Rule that will restrict the access to the private applications, allowing the VPC2_WindowsClient Instance to access only the VPC1_LinuxApp1 application. The VPC1_linuxApp2 and VPC1_WindowsApps will be restricted, and the access to these applications will only be available again when the Risk Level of the VPC2_WindowsClient is restored to the normal state.

Follow these instructions to enable the ZTSA Risk Control Rules and have this automation rule activated.

* Step 1 
Create a new Risk Control Rule and name it as "ZTSA - Automated Response"
![Endpoint_Deployment](/images/ztsa-rules.png)

* Step 2
Click on START and then select the option "Workbench alerts for device-related events" under "Create from".
![Endpoint_Deployment](/images/ztsa-rules1.png)

* Step 3
Edit the CONDITION option, and filter for the following Risk Event “Screen Capture and Keylogging via Powershell".
![Endpoint_Deployment](/images/ztsa-rules2.png)
![Endpoint_Deployment](/images/ztsa-rules3.png)

* Step 4
As response in case the condition defined on the step 3 is detected, select  the "Add action for private access", and then select the access to all the aplications, except the VPC1_LinuxApp1 applications. After you finish this Risk Control rule creation, save the policy and access again the VPC2_WindowsClient Instance using RDP.
![Endpoint_Deployment](/images/ztsa-response1.png)
![Endpoint_Deployment](/images/ztsa-response2.png)

---
### Testing the Zero Trust Secure Access Rules (Automated Respose)
Access the VPC2_WindowsClient Instance using RDP, and then open the powershell script called "tools.ps1". You will find an options menu (1 to 5).
Select the option 5, so a powershell shell script will be execute on the VPC2_WindowsClient Instance and a screenshot event will be generate. After a few minutes, a workbench will be available on Vision One describing this event.
![Endpoint_Deployment](/images/ztsa-tools.png)

If you correctly configured the Risk Control Rule (Step 1 to 4), you will find a workbench similar to te ones described in the following screenshots.
![Endpoint_Deployment](/images/ztsa-workbench.png)
![Endpoint_Deployment](/images/ztsa-workbench2.png)

After the workbench is triggered, the Risk Control Rules will also trigger the automated response. You can find it by checking the Remediation Logs (Zero Trust - Secure Access Logs).
![Endpoint_Deployment](/images/ztsa-responselog1.png)
![Endpoint_Deployment](/images/ztsa-responselog2.png)

---
Now its time try to access the applications running on VPC1 again. You will find that only the VPC1_LinuxApp1 is available now. The ZTSA Module will show a pop-up notification indicating the affected user/computer is not authorized to access the other applications anymore.
* Using Google Chrome: http://10.0.3.10
* Using Google Chrome: http://10.0.3.11
* Using Windows Explorer: \\\10.0.3.20
* Using the RDP Client: 10.0.3.20

With this demo, you learned how the Trend Micro Vision One platform could enable remote workforces to access remotely and securely the business applications, and also see how the continuouly security evaluation (Risk Insights) helps to mitigate security risks as soon as they are detected.
