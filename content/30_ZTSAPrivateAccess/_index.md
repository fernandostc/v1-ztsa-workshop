---
title: "ZTSA Private Access"
chapter: false
weight: 30
pre: "<b>3. </b>"
---
## Lab Preparation Guide

### Lab Architecture
To simulate a real customer environment, we will use a pre-built CloudFormation template that will create the following resources all in the same Availibility Zone (AZ):

The CFT will create 2 VPCs (VPC1 and VPC2). The VPC1 is hosting Windows and Linux Instances. They are not exposed to the internet by default. To access these applications, the ZTSA Infrastructure is required. 

The VPC2 Windows Client Instance does not have access to the applications on VPC1 by default, but they will become available after you enable the ZTSA Module. 

    Cloud Formation Template description

        * 2x VPCs
            - VPC1
            - VPC2

        * 4x EC2 Instances Running on VPC1 (Not exposed to the internet)
            * VPC1_WindowsServer
                * Exposed Services (RDP, SMB Share)
            * VPC1_LinuxServer1
                * Exposed Services (HTTP) 
            * VPC1_LinuxServer2
                * Exposed Services (HTTP) 
            * VPC1_ZTNA-Connector
                * Exposed Services (ZTSA Services)
                
        * 1x EC2 Instance Running on VPC2 (Exposed to the internet)
            * VPC2_WindowsClient
                * Exposed Services (RDP) - with the XDR Endpoint Sensor and ZTSA Private Access Module enabled

<b>Notes:</b>
> <b>1 -</b> The applications hosted on VPC1 are not exposed to the internet (representing an on premises environment) and can only be accessed using the ZTSA Infrastructure.

> <b>2</b> The VPC2_WindowsClient is representing a remote client, which is connecting to the applications hosted on the VPC1 using the Zero Trust Infrastructure.

![Endpoint_Deployment](/images/ztsa-diagram.png) 


---

### Creating the base AWS environment using AWS CloudFormation Template
Using your AWS Account, deploy the Cloud Formation Template “[demo-aws-ztsa.yaml](https://console.aws.amazon.com/cloudformation/home#/stacks/new?stackName=ZTSAWorkshop&templateURL=https://visionone.s3.us-west-1.amazonaws.com/demo-aws-ztsa.yaml)” and follow the next instructions. 

<a href="https://console.aws.amazon.com/cloudformation/home#/stacks/new?stackName=ZTSAWorkshop&templateURL=https://visionone.s3.us-west-1.amazonaws.com/demo-aws-ztsa.yaml" target="_blank"><img src="https://cdn.rawgit.com/buildkite/cloudformation-launch-stack-button-svg/master/launch-stack.svg" /></a>
