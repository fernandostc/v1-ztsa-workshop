---
title: "ZTSA - Client Based Access - part 3"
chapter: false
weight: 33
pre: "<b>3.3 </b>"
---
 
### ZTSA – Private Access Control - Testing the Solution

---
After you finishing the steps 3.1 and 3.2, open the AWS Management Console and check the Outputs tab. Take notes of the VPC2_WindowsClient public IP address. You can also check the tab Parameters in case you don't remember the Windows Credentials you used when deployed the CFT.

With the VPC2_WindowsClient Public IP Address in hands, you must RDP to this EC2 Instance using Terminal Services. Note that the Vision One XDR Agent is installed and monitoring this computer (task manager).

> Connecting to the VPC2 WindowsClient Instance and checking the Vision One XDR Agent status. 

{{< youtube id="STJEAZ47OL4" >}}

---
After accessing the VPC2_WindowsClient, you can try to access the following Applications running on the VPC1.
* Using Google Chrome: http://10.0.3.10
* Using Google Chrome: http://10.0.3.11
* Using Windows Explorer: \\\10.0.3.20
* Using the RDP Client: 10.0.3.20

You will find that none of them are accessible for you at this moment.

{{< youtube id="YjaurBMUDYU" >}}

---
### Activating the ZTSA Module
To allow the remote users to access the Private Applications running on the network 10.0.3.*, the following instructions must be followed.

The first step that must be executed is the deployment of the ZTSA Module to the VPC2_WindowsClient. You can do that using the Zero Trust Secure Access > Secure Access Configuration > Secure Access Module menu and selecting the new Windows Instance and select Deploy Module.

After you select the Deploy Module option, you can monitor the ZTSA Module Installation by monitoring the Task Manager on the VPC2_WindowsClient Instance. The installation process usually takes 3 to 5 minutes to be finished. After the deployment is finished, you will find a new Trend Micro ZTSA shortcut on the VPC2_WindowsClient desktop.

{{< youtube id="5NyxhWz3Cf4" >}}

---

### Connecting to the Remote Applications

After the ZTSA Module installation is finished, you can log in to the ZTSA Module and find the applications available for you to access (use the AzureAD Account you listed as an authorized account when you created the ZTSA Access Policy).

Now its time try to access the applications running on VPC1 again. You will find they are all available for you to access now.

* Using Google Chrome: http://10.0.3.10
* Using Google Chrome: http://10.0.3.11
* Using Windows Explorer: \\\10.0.3.20
* Using the RDP Client: 10.0.3.20

{{< youtube id="8uZhmJJ57c8" >}}

---
You can also check the Vision One / Secure Access History logs. You will find (the logs can take up to 5 minutes to be synchonized) the detection logs related to the tests you are executing.
![Endpoint_Deployment](/images/ztsa-internal-logs.png)


---
### Configuring the Zero Trust Secure Access Rules (Automated Respose)
Now its time to demonstrate how the Trend Micro Zero Trust Platform is capable to continuously monitor all the activities happening on the monitored endpoint. If an malicious or abnormal behavior is detected, a Secure Access Rule can trigger an automated response (Example: Isolating the affected Endpoint, Restricting the access to Private Applications, Interacting with Azure AD to disable the affected user account, etc). 

In this demo we are going to simulate some suspicious activity (T1113 - Screen Capture and Keylogging via Powershell). This event will trigger a Secure Access Rule / Risk Control Rule that will restrict the access to the private applications, allowing the VPC2_WindowsClient Instance to access only the VPC1_LinuxApp1 application. The access to the VPC1_linuxApp2 and VPC1_WindowsApps applications will be restricted, and the access to these applications will only be available again when the Risk Level of the VPC2_WindowsClient is restored to the normal state.

Follow these instructions to enable the ZTSA Risk Control Rules and have this automation rule activated.

* Step 1 
Create a new Risk Control Rule and name it as "ZTSA - Automated Response"

* Step 2
Click on START and then select the option "Workbench alerts for device-related events" under "Create from".

* Step 3
Edit the CONDITION option, and filter for the following Risk Event “Screen Capture and Keylogging via Powershell".

* Step 4
As response in case the condition defined on the step 3 is detected, select  the "Add action for private access", and then select the access to all the aplications, except the VPC1_LinuxApp1 applications. After you finish this Risk Control rule creation, save the policy and access again the VPC2_WindowsClient Instance using RDP.

> How to create a Risk Control Rule (Private Access)

{{< youtube id="-6v_YVlgl30" >}}

---
### Testing the Zero Trust Secure Access Rules (Automated Respose)
Access the VPC2_WindowsClient Instance using RDP, and then open the powershell script called "tools.ps1". You will find an option menu (1 to 5).
Select the option 5, so a powershell shell script will be execute on the VPC2_WindowsClient Instance and a screenshot event will be generate. After a few minutes, a workbench will be available on Vision One describing this event.

If you correctly configured the Risk Control Rule (Step 1 to 4), you will find a workbench called "Screen Capture and Keylogging via Powershell". This workbench

After the workbench is triggered, the Risk Control Rules will also trigger the automated response. You can find it by checking the Remediation Logs (Zero Trust - Secure Access Logs).

Now its time try to access the applications running on VPC1 again. You will find that only the VPC1_LinuxApp1 is available now. The ZTSA Module will show a pop-up notification indicating the affected user/computer is not authorized to access the other applications anymore.
* Using Google Chrome: http://10.0.3.10
* Using Google Chrome: http://10.0.3.11
* Using Windows Explorer: \\\10.0.3.20
* Using the RDP Client: 10.0.3.20

{{< youtube id="iNAFyRbKbJQ" >}}

---

With this demo, you learned how the Trend Micro Vision One platform could enable remote workforces to access remotely and securely the business applications, and also see how the continuouly security evaluation (Risk Insights) helps to mitigate security risks as soon as they are detected.
