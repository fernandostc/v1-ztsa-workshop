---
title: "ZTSA - Client Based Access - part 2"
chapter: false
weight: 32
pre: "<b>3.2 </b>"
---
 
### ZTSA – Private Access Control - Configuring the Secure Access Rules / Private Access Control
The Secure Access Rules are the key to allow your remote workforce to access the private applications. In our case, the VPC2 Windows Client will only be able to connect to the applications running on the VPC1 after we create the Secure Access Rule that allows access from specific devices/users to the private applications created/added to the Vision One in the previous step of this lab.


---
#### ZTSA – Private Access Control Rules
The following instructions will guide you and enable the VPC2_WindowsClient Instance to Access the applications hosted on the VPC1.

{{< youtube id="0VstN03vW1U" >}}

> <b>Add the following Secure Access Rules to your Vision One account</b>

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
