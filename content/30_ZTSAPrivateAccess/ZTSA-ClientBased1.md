---
title: "ZTSA - Client Based Access - part 1"
chapter: false
weight: 31
pre: "<b>3.1 </b>"
---
## ZTSA - Activating and Configuring the Service
---
## ZTSA - Enabling the Zero Trust Secure Access Service
Access the "Zero Trust Secure Access Overview" menu, and follow the instructions provided on the "Deployment Wizard" tool.
![Endpoint_Deployment](/images/ztsa-wizard.png)

---
## ZTSA – Private Access Control 
### ZTSA – Private Access Control - Global Settings
Configure a web-based user portal to ensure that all user traffic is validated even when the Secure Access Module is not available.
![Endpoint_Deployment](/images/ztsa-globalsettings.png)

More information on how to integrate customize the companies' CNAME can be find on the following [link](https://docs.trendmicro.com/en-us/enterprise/trend-micro-vision-one/zero-trust-secure-ac/access-configuration/private-access-confi/global-settings-ztna/creating-the-custom-.aspx)

---
### ZTSA – Private Access Control - Private Access Connectors
Deploy groups of Private Access Connector virtual appliances and manage them on the Trend Micro Vision One console.

A connector group consists of one or multiple Private Access Connectors that are deployed to an entry point in your on-premises data center or cloud IaaS environment. The corporate applications to enforce access control are reachable by the group of Connectors in the same environment. 

* Click Add Private Access Connector Group.
* On the Add Private Access Connector Group panel that appears, specify a name and description for the group.
* To save the connector group and add Connectors at a later stage, click Save.

![Endpoint_Deployment](/images/ztsa-connector.png)

![Endpoint_Deployment](/images/ztsa-connector2.png)

---

### ZTSA – Private Access Control - Internal Applications - Client Based Access
Add your organization's private application to the internal apps list, and associate it with a Private Access Connector group in the same environment.

On the Internal Applications tab, click "Add Internal Application / Client Access".
![Endpoint_Deployment](/images/ztsa-app1.png)
![Endpoint_Deployment](/images/ztsa-app2.png)

Add the following applications to your Vision One account.

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

### ZTSA – Private Access Control - Internal Applications - Web Browser Based Access
Add your organization's private application to the internal apps list, and associate it with a Private Access Connector group in the same environment.

On the Internal Applications tab, click "Add Internal Application / Browser Access".
![Endpoint_Deployment](/images/ztsa-app1.png)
![Endpoint_Deployment](/images/ztsa-app3.png)

Add the following applications to your Vision One account.

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
