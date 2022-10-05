---
title: "ZTSA - Client Based Access - part 2"
chapter: false
weight: 32
pre: "<b>3.2 </b>"
---
 
## ZTSA – Private Access Control - Configuring the Secure Access Rules / Private Access Control

Before you connect to the VPC2_WindowsClient computer, its important to make sure there are policies allowing this computer to remotely access (using the ZTSA Infrastructure) the applications hosted on the VPC1.

The following instructions will guide you and enable the VPC2_WindowsClient Instance to Access the applications hosted on the VPC1.

---
### ZTSA – Private Access Control Rules
<b> 1 - On the Secure Access Rules screen, click the Private Access Control tab and then click Create Rule. You have to create 3 Access Rules based on the instructions provided below. </b>

![Endpoint_Deployment](/images/ztsa-access1.png)
![Endpoint_Deployment](/images/ztsa-access2.png)


> <b>App Description</b>

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
