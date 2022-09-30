---
title: "CloudWatch Visibility - Endpoint"
chapter: true
weight: 41
pre: "<b>5.1 </b>"
---

# Enable CloudWatch Visibility for Networks Security Managed Endpoint.



#### 1. Obtain the following Parameter values.
- In CloudFormation, select the stack: ```C1NS-Cloud-Account-Management```. 
- Select the **Parameters** tab.
- Copy down the **ExternalID** value.
- Obtain your **AWS Account ID** by clicking your name/user in the top right. Copy this value down.

![CloudWatch2](/images/cw4.png)

---

#### 2. Launch the CloudFormation Template.

> Let's create the Panel with CloudFormation :laptop: :cloud: :bar_chart:

[![Launch Stack](https://cdn.rawgit.com/buildkite/cloudformation-launch-stack-button-svg/master/launch-stack.svg)](https://console.aws.amazon.com/cloudformation/home#/stacks/new?stackName=NS-Cloudwatch-Panel&templateURL=https://aws-workshop-c1as-cft-templates.s3.amazonaws.com/Network_Security_MS_CloudWatch.yml)


---

#### 3. Create Stack.
- click on **Next**.

![CloudWatch2](/images/Create_Stack.png)

---

#### 4. Specify stack details.
- Leave the **C1NSRegion** and **DashboardName** parameters as default.
- For **LogStream** use the following format below, replacing the values appropriately.

- ```NSaaS-<External ID here>-<AWS Account ID Here>-<VPC-ID here>```

- Example: ```NSaaS-340002837676-013257365352-vpc-00ff298e7578fb3a9```

- Click on **Next**.
- Again, Click on **Next**.
- Review the stack details and click on **Create Stack**.

![CloudWatch2](/images/cw2.png)
![CloudWatch10](/images/panel_tags.png)
![CloudWatch12](/images/panel_review2.png)

---

#### 5. After the Stack has reached Create_Complete, you can view the CloudWatch Panel.

- Select the **Resources** tab.
- Click on the link named **Cloud_One_Network_Security_Panel**.

![CloudWatch2](/images/cw3.png)

![CloudWatch14](/images/cw-nsaas-dash.png) 

With that you can will be able to use the Dashboard to monitor the Appliance performance and also the Detection and Block statistics


--------

### Congrats on your custom CloudWatch view from Cloud One - Network Security :star-struck: :robot: :white_check_mark: :cloud:

