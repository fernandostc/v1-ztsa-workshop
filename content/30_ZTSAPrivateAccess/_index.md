---
title: "ZTSA Private Access"
chapter: false
weight: 30
pre: "<b>3. </b>"
---
## LAB PREPARATION (AWS Infrastructure)

### Lab Architecture
To simulate a real customer environment, we will use a pre-built CloudFormation template that will create the following resources all in the same Availability Zone (AZ):

The CFT will create 2 VPCs (VPC1 and VPC2). The VPC1 hosts one (1) Windows and two (2) Linux Instances. These EC2 Instances are not exposed to the internet, and the only way to access the applications hosted on each Instance is by using the Trend Micro ZTSA Infrastructure.

Since we want to simulate malicious actions, you can use the "VPC2 Windows Client" Instance to realize all the tests. This EC2 Instance doesn't have access by default to any of the applications hosted on the VPC1. 

After enabling the ZTSA Module on the VPC2 Windows Client instance, you will find that all the applications running on the VPC1 will then become available.

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

![Endpoint_Deployment](/images/ztsa-diagram.png) 


---

### Creating the base AWS environment using AWS CloudFormation Template
Using your AWS Account, deploy the Cloud Formation Template “[demo-aws-ztsa.yaml](https://console.aws.amazon.com/cloudformation/home#/stacks/new?stackName=ZTSAWorkshop&templateURL=https://visionone.s3.us-west-1.amazonaws.com/demo-aws-ztsa.yaml)” and follow the instructions provided in the following video. 

<a href="https://console.aws.amazon.com/cloudformation/home#/stacks/new?stackName=ZTSAWorkshop&templateURL=https://visionone.s3.us-west-1.amazonaws.com/demo-aws-ztsa.yaml" target="_blank"><img src="https://cdn.rawgit.com/buildkite/cloudformation-launch-stack-button-svg/master/launch-stack.svg" /></a>

> How to deploy the Cloud Formation Template?

<div style="text-align: center;">
<div id="ytplayer"></div>

<script>
  // Load the IFrame Player API code asynchronously.
  var tag = document.createElement('script');
  tag.src = "https://www.youtube.com/player_api";
  var firstScriptTag = document.getElementsByTagName('script')[0];
  firstScriptTag.parentNode.insertBefore(tag, firstScriptTag);

  // Replace the 'ytplayer' element with an <iframe> and
  // YouTube player after the API code downloads.
  var player;
  function onYouTubePlayerAPIReady() {
    player = new YT.Player('ytplayer', {
      height: '480',
      width: '854',
      videoId: 'mnXvJoUrUqw'
    });
  }
</script>
</div>
