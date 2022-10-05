---
title: "ZTSA Internet Access"
chapter: false
weight: 40
pre: "<b>4. </b>"
---
## Lab Preparation Guide

### Lab Architecture
To simulate a real customer environment, we will use a pre-built CloudFormation template that will create the following resources all in the same Availibility Zone (AZ):

* <b>1x VPCs</b>
    - VPC1

* <b>1x EC2 Instance Running on VPC2 (Exposed to the internet)</b>
    * VPC2_WindowsClient
        * Exposed Services (RDP) - with ZTSA Internet Access Module

Notes:
* 1 The internet access from the VPC2_WindowsClient will be monitored by ZTSA Internet Access Control.
* 2 When a malicious file download event is detected on the VPC2_WindowsClient Instance is detected. In case a Ransomware event is detection is detected on this computer, a Risk Control Rule will act isolating the computer from the network 

NETWORK DIAGRAM TO BE UPDATED
![Endpoint_Deployment](/images/ztsa-diagram.png) 
NETWORK DIAGRAM TO BE UPDATED

---

### Creating the base AWS environment using AWS CloudFormation Template

******** If you already deployed and still have access to the demo environment -Zero Trust Private Access-, you can skip this step and use the same demo environment. ********

Using your AWS Account, deploy the Cloud Formation Template “demo-aws-ztsa.yaml” and follow the next instructions. 

<a href="https://console.aws.amazon.com/cloudformation/home#/stacks/new?stackName=ZTSAWorkshop&templateURL=https://visionone.s3.us-west-1.amazonaws.com/demo-aws-ztsa.yaml" target="_blank"><img src="https://cdn.rawgit.com/buildkite/cloudformation-launch-stack-button-svg/master/launch-stack.svg" /></a>


---

### Enabling the ZTSA Internet Access service on Vision One
The Zero Trust Internet Access Module is one additional feature available on Vision One. It allows companies to control the Internet Access, mitigating the issues and security risks accessed by the users. It also allows companies to take decisions based on the Risk Index that each user/device could impose to the company.

First, you must enable the Internet Access Service. You can do this using the Vision One Management Console. You can do this by accessing the Zero Trust Secure Access > Internet Access Configuration, and then enabling the Internet Access Control module.
![Endpoint_Deployment](/images/ztsa-internetaccess.png) 

After you enable the Internet Access Service, make sure you created a HTTPS Inspection Rule (this step is required in order to give full visibility to the ZTSA Internet Access module).
Be sure you included all URL Categories to the SSL Inspection Rule.

![Endpoint_Deployment](/images/ztsa-ssl1.png) 
![Endpoint_Deployment](/images/ztsa-ssl2.png) 
