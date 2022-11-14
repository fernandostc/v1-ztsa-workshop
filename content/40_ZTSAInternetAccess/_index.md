---
title: "ZTSA Internet Access"
chapter: false
weight: 40
pre: "<b>4. </b>"
---
## LAB PREPARATION 

### Lab Architecture (AWS Infrastructure)

The infrastructure used to demonstrate ZTSA Internet Access can be created by using Cloud Formation Templates.

After you finish the Cloud Formation Template deployment, you will find the following components available for you to use:

    * 1x VPC
        * VPC2_WindowsClient
            * Exposed Services (RDP) - with ZTSA Internet Access Module installed

<b>Notes:</b>

<b>1 The internet access from the VPC2_WindowsClient will be monitored/protected by ZTSA Internet Access Control.</b>

<b>2 When a malicious file download event is detected on the VPC2_WindowsClient Instance is detected. In case a Ransomware event is detection is detected on this computer, a Risk Control Rule will act isolating the computer from the network.</b>

---
### Deploying the Cloud Formation Template
Using your AWS Account, deploy the following Cloud Formation Template and follow the instructions provided in the following video. 

<b>If you already deployed the Private Access Control (CFT), you can use the same infrastructure instead of creating a new one.</b>

<a href="https://console.aws.amazon.com/cloudformation/home#/stacks/new?stackName=ZTSAWorkshop&templateURL=https://v1demoplatform.s3.us-west-1.amazonaws.com/v1-ztsa-demo/demo-aws-ztsa.yaml" target="_blank"><img src="https://cdn.rawgit.com/buildkite/cloudformation-launch-stack-button-svg/master/launch-stack.svg" /></a>

- How to deploy the Cloud Formation Template?

{{< youtube id="mnXvJoUrUqw" >}}

---
### Enabling the ZTSA Internet Access service on Vision One
The Zero Trust Internet Access Module is one of the most important components of Trend Micro Zero Trust Platform. It allows companies to control the Internet Access, stopping the access to malicious URLs, malicious or non-authorized content, and more. It also allows companies to take decisions based on the Risk Index that each user/device could impose to the company.

Before start testing this module, you must enable the Internet Access Service. You can do this using the Vision One Management Console > Zero Trust Secure Access > Secure Access Configuration > Internet Access Configuration.

After you enable the Internet Access Service, make sure you created a HTTPS Inspection Rule (this step is required in order to give full visibility to the ZTSA Internet Access module). Be sure you also included all URL Categories to the SSL Inspection Rule.

{{< youtube id="HJ_bit0gqQ8" >}}

