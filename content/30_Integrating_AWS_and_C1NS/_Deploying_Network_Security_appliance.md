---
title: "Deploy the Network Security Appliance"
chapter: false
weight: 34
pre: "<b>4.4 </b>"
---

### Deploying Cloud One - Network Security Appliance 

{{% notice warning %}}
<p style='text-align: left;'>
<b>Don't not continue with these steps if you have already deployed the Network Security Managed Endpoint. The NS appliance is an alternative deployment method.</b>
</p>
{{% /notice %}}

Amazon Web Services (AWS) allows you to scale your network deployment as needed without investing in hardware appliances. Deploy Network Security in AWS by placing Network Security instances inline within your AWS Virtual Private Cloud (VPC).

![C1NS1](/images/C1NS_Edge_Deployment.png)

---

#### 1. In the Cloud One Network Security console.
- Select the **Network tab**.
- From the option select, **Appliances**.
- Click the **blue + button**, to start the wizard.

![C1NS1](/images/appliance1.png)
![C1NS1](/images/appliance2.png)


#### 2. Deploy protection.

- **Select** the cloud account created previously.
- Click **Next: Select Asset**.


 
![C1NS1](/images/deploy_appliance1.png)
---

#### 2. Select the VPC that you will deploy the Network Security Appliance.

- Select the VPC with the Internet Gateway Name: ```IGW - C1NS-labenvironment```
- Click on **Next: Select Availability Zones**
![C1NS1](/images/deploy_appliance2.png) 

---

#### 3. Here you can select the Availability Zone(s) that the Cloud One - Network Security Appliance will include in the deployment script. 
- Select **us-east-1a**.
- Click on **Next: Verify Network Asset** 

{{% notice note %}}
<p style='text-align: left;'>
Leave as default with the one AZ selected for this workshop.
</p>
{{% /notice %}}

![C1NS1](/images/deploy_appliance3.png)
---

#### 4. Verify Network Asset
This step verifies that the selected network asset can support deployment for the Network Security virtual appliance.
- Click on **Next: Finalize Parameters** 

![C1NS1](/images/deploy_appliance4.png) 

---

#### 5. Finalize parameters
- Select the SSH Key Pair that we created before for this workshop
- Click on **Next: Use Deployment Script**

![C1NS1](/images/deploy_appliance5.png)

---

#### 6. Click on **Download** to get the CloudFormation template

{{% notice note %}}
<p style='text-align: left;'>
The CloudFormation template will create 2 new subnets for you, the Inspection and the Management subnets.
</p>
{{% /notice %}}

![C1NS1](/images/deploy_appliance6.png)
 

---

#### 7. Edit the CloudFormation template (deploymentScript.yaml) downloaded previously from Cloud One console. 

You can use any text editor or IDE. In our example we are using [Visual Studio Code](https://code.visualstudio.com/download).

---

##### 7.1 In an IDE, open the CloudFormation template that was downloaded called - **deploymentScript.yaml**

![C1NS1](/images/deploy_appliance7.png) 

---

##### 7.2 In the code, search for ```END VTPS CLI```.

![C1NS1](/images/deploy_appliance8.png) 

---

##### 7.3 Add the code snippet provided **ABOVE** the line string  with **END VTPS CLI**. 

These lines are to enable the event forwarding to AWS CloudWatch using the America EST timezone.

```
  edit
- |
  log
- |
  cloudwatch inspection-event enable
- |
  exit
- |
  commit
- |
  exit
- |
  save-config -y
- |
  edit
- |
  gen
- |
  timezone America New_York
- |
  exit
- |
  commit
- |
  exit
- |
  save-config -y
- |
```

---


##### 7.4  After making the changes, the code will be similar to the image below. 
The selection are the lines that I added. 

- Once changed, **save the file**.

{{% notice warning %}}
<p style='text-align: left;'>
<b>Be careful with the indention of the code, otherwise the template format may break.</b>
</p>
{{% /notice %}}

![C1NS1](/images/deploy_appliance9.png) 

---

#### 8. Navigate to the [AWS Console](https://aws.amazon.com/)
- Navigate to **CloudFormation**
- Click on **Create Stack with new resources**

![C1NS1](/images/deploy_appliance10.png) 

---

#### 9.  Create Stack
- Select the **Upload a template file** 
- Click on **Choose file** 
- Choose the CloudFormation template: **deploymentScript.yaml**
- Click on **Next**


![C1NS1](/images/deploy_appliance11.png) 

---

#### 10.  Specify Stack details.
- **Stack Name**: ```Modernization-Workshop-Network-Security-Appliance```.
- Click on **Next**


![C1NS1](/images/deploy_appliance12.png) 

---
#### 11. (Optional) Configure stack options
- Add **Tags** if desired 
- Click on **Next**


![C1NS1](/images/deploy_appliance13.png) 

---
#### 12. Review deployment. 
- Check the box "I acknowledge .."
- Click on **Create stack**

![C1NS1](/images/deploy_appliance14.png)
![C1NS1](/images/deploy_appliance15.png)
![C1NS1](/images/deploy_appliance16.png)

---

#### 13. Wait until the successful creation of the stack before you move to the next chapter.

![C1NS1](/images/deploy_appliance17.png)
![C1NS1](/images/deploy_appliance18.png) 

---
> **Et voila, we just generated completed the deployment of the Cloud One - Network Security Appliance in our AWS environment** 🤩 :cloud: 🤖 :rocket:
