---
title: "ZTSA Private Access"
chapter: false
weight: 30
pre: "<b>3. </b>"
---
## DEMO PREPARATION 
### Lab Architecture (AWS Infrastructure)

We are using Cloud Formation Templates to deploy the Demo Environment.

After you finish the Cloud Formation Template deployment, you will find the following components available for you to use:

    Cloud Formation Template description

        * 2x VPCs
            - VPC1 (The Instances running on this VPC are not exposed to the internet. The services running on this VPC can only be accessed using the ZTSA Infrastructure)
            - VPC2 (One Windows Instance is exposed to the internet. This Instance will simulate your remote clients trying to access the Private Applications running on the VPC1)

            * VPC1 
                * VPC1_WindowsServer
                    * Services (RDP, SMB Share)
                * VPC1_LinuxServer1
                    * Services (HTTP) 
                * VPC1_LinuxServer2
                    * Services (HTTP) 
                * VPC1_ZTNA-Connector
                    * Services (ZTSA Services)
                
            * VPC2 
                * VPC2_WindowsClient
                    * Exposed Services (RDP) - with the XDR Endpoint Sensor and ZTSA Private Access Module enabled
                    
----
### Vision One - Preconfiguration
#### ZTSA - Enabling the Zero Trust Secure Access Service
Access the "Zero Trust Secure Access Overview" menu, and follow the instructions on the "Deployment Wizard" tool.
![Endpoint_Deployment](/images/ztsa-wizard.png)

---
#### ZTSA – Private Access Control - Global Settings
Configure the web-based user portal to allow users using the Web Browser Based Access to access the private applications. 

More information on how to customize the companies' CNAME can be found on the following [link](https://docs.trendmicro.com/en-us/enterprise/trend-micro-vision-one/zero-trust-secure-ac/access-configuration/private-access-confi/global-settings-ztna/creating-the-custom-.aspx).
![Endpoint_Deployment](/images/ztsa-globalsettings.png)

---
#### ZTSA – Private Access Control - Private Access Connectors
Deploy groups of Private Access Connector virtual appliances and manage them on the Trend Micro Vision One console.

A connector group consists of one or multiple Private Access Connectors that are deployed to an entry point in your on-premises data center or cloud IaaS environment. The corporate applications to enforce access control are reachable by the group of Connectors in the same environment. 

- How to add the Private Access Connectors? 
{{< youtube id="uzZILZEqWIw" >}}

---
#### ZTSA – Private Access Control - Internal Applications - Client Based Access
Add your organization's private application to the internal apps list, and associate it with a Private Access Connector group in the same environment.

- How to add new Internal Applications / Client Based Access to Vision One.
{{< youtube id="DuoILZ3taiY" >}}

.

<b>- Add the following applications to your Vision One account.</b>

*   <b>VPC1-LinuxApp1</b>
        
        Application Name:
        VPC1-LinuxApp1

        Description:
        LinuxApp1Client

        Connector Group:
        VisionOne – ZTSA Demo

        Client Access:
        Protocol:
        TCP/UDP

        IP Address:
        10.0.3.10

        Port:
        Any

        End User Access:
        x Make the app visible for end user access

*   <b>VPC1-LinuxApp2</b>
        
        Application Name:
        VPC1-LinuxApp2

        Description:
        LinuxApp2Client

        Connector Group:
        VisionOne – ZTSA Demo

        Client Access:
        Protocol:
        TCP/UDP

        IP Address:
        10.0.3.11

        Port:
        Any

        End User Access:
        x Make the app visible for end user access

*   <b>VPC1-WindowsApp</b>
        
        Application Name:
        VPC1-WindowsApp

        Description:
        WindowsAppClient

        Connector Group:
        VisionOne – ZTSA Demo

        Client Access:
        Protocol:
        TCP/UDP

        IP Address:
        10.0.3.20

        Port:
        Any

        End User Access:
        x Make the app visible for end user access

---
#### ZTSA – Private Access Control - Internal Applications - Web Browser Based Access
Add your organization's private application to the internal apps list, and associate it with a Private Access Connector group in the same environment.

- How to add new Internal Applications / Web Browser Based Access to Vision One.
{{< youtube id="2nZmagt6RqU" >}}

.

<b>- Add the following applications to your Vision One account.</b>

*   <b>VPC1-WindowsApp-RDP</b>
       
        Application Name:
        VPC1-WindowsApp-RDP

        Description:
        WindowsAppWeb

        Connector Group:
        VisionOne – ZTSA Demo

        Browser Access:
        x Allow users to access via a user portal provided by Trend Miro
        Protocol:
        Web-Based RDP
        
        Internal URL / FQDN / Port:
        10.0.3.20 : 3389
        
        External URL / Prefix:
        winrdp

        End User Access:
        x Make the app visible for end user access

*   <b>VPC1-LinuxApp1-Web</b>
        
        Application Name:
        VPC1-LinuxApp1-Web

        Description:
        LinuxApp1Web

        Connector Group:
        VisionOne – ZTSA Demo

        Browser Access:
        x Allow users to access via a user portal provided by Trend Miro
        Protocol:
        HTTP
        
        Internal URL / FQDN / Port:
        10.0.3.10 : 80
        
        External URL / Prefix:
        linuxapp1

        End User Access:
        x Make the app visible for end user access

*   <b>VPC1-LinuxApp2-Web</b>
        
        Application Name:
        VPC1-LinuxApp2-Web

        Description:
        LinuxApp2Web

        Connector Group:
        VisionOne – ZTSA Demo

        Browser Access:
        x Allow users to access via a user portal provided by Trend Miro
        Protocol:
        HTTP
        
        Internal URL / FQDN / Port:
        10.0.3.11 : 80
        
        External URL / Prefix:
        linuxapp2

        End User Access:
        x Make the app visible for end user access

----
### ZTSA – Private Access Control - Configuring the Secure Access Rules / Private Access Control
The Secure Access Rules are the key to allow your remote workforce to access the private applications. In our case, the VPC2 Windows Client will only be able to connect to the applications running on the VPC1 after we create the Secure Access Rule that allows access from specific devices/users to the private applications created/added to the Vision One in the previous step of this lab.

#### ZTSA – Private Access Control Rules
The following instructions will guide you and enable the VPC2_WindowsClient Instance to Access the applications hosted on the VPC1.

{{< youtube id="0VstN03vW1U" >}}

.

<b>- Add the following Secure Access Rules to your Vision One account</b>

* <b>App01</b>
     
        Rule Name: VPC1-WindowsApp

        Users: All Users

        Devices: All Devices

        Location: All Locations

        Destination: VPC1-WindowsApp, VPC1-WindowsApp-Web

        Schedule: Always

        Actions: Monitor Internal App Access

* <b>App02</b>
       
        Rule Name: VPC1-LinuxApp1

        Users: All Users

        Devices: All Devices

        Location: All Locations

        Destination: VPC1-LinuxApp1, VPC1-LinuxApp1-Web

        Schedule: Always

        Actions: Monitor Internal App Access

* <b>App03</b>
        
        Rule Name: VPC1-LinuxApp2

        Users: All Users

        Devices: All Devices

        Location: All Locations

        Destination: VPC1-LinuxApp2, VPC1-LinuxApp2-Web

        Schedule: Always

        Actions: Monitor Internal App Access

---

### Deploying the Cloud Formation Template
Using your AWS Account, deploy the following Cloud Formation Template and follow the instructions provided in the following video. 
<a href="https://console.aws.amazon.com/cloudformation/home#/stacks/new?stackName=ZTSAWorkshop&templateURL=https://v1demoplatform.s3.us-west-1.amazonaws.com/v1-ztsa-demo/demo-aws-ztsa.yaml" target="_blank"><img src="https://cdn.rawgit.com/buildkite/cloudformation-launch-stack-button-svg/master/launch-stack.svg" /></a>

- How to deploy the Cloud Formation Template?

{{< youtube id="mnXvJoUrUqw" >}}

