---
title: "Cloud One - Network Security Adding Cloud Account"
chapter: false
weight: 32
pre: "<b>4.2 </b>"
---

### Integrating AWS with Cloud One- Network Security.

{{% notice info %}}
<p style='text-align: left;'>
A Cloud One Account is required to proceed. If you have not registered for a Cloud One account please go <a href="https://www.trendmicro.com/en_us/business/campaigns/cloud-one-trial.html?utm_campaign=RGEV2022_Cloud-One_SMKT&utm_medium=Webinar&utm_source=Immersion-Day_Network_PR&utm_content=Cloud-One-Trial" target="_top">here.</a>
</p>
{{% /notice %}}

----

#### 1. Log in [Cloud One](https://cloudone.trendmicro.com/)
- Select the **Network Security** tile. 

![C1NS2](/images/c1-home.png) 

---

#### 2. Click on **Add Cloud Account**.

![C1NS3](/images/C1NS_Wizard.png)

---

#### 3. Create an IAM role and policy for Network Security in your AWS account using the generated CloudFormation template.

- Click on **Launch Stack**.

![C1NS4](/images/Add_IAM_Policy.png) 

---

#### 4. Clicking Launch Stack will navigate you to AWS CloudFormation.
- Optional: Rename the stack.
- Do NOT edit any of the stack parameters.
- Check the box to acknowledge resources.
- Click on **Create Stack**

![C1NS1](/images/create_net_sec_1.png)
![C1NS1](/images/create_net_sec_2.png)

---

#### 5. Once the Stack has completed successfully.
- Select the tab **Outputs** 
- Copy the **ARN value** for the IAM role created.

![C1NS1](/images/create_net_sec_3.png) 

---

#### 6. Navigate back to Cloud One - Network Security.
- Paste in the ARN value copied from the CloudFormation Outputs.
- Click on **+ Add Cloud Account**

![C1NS1](/images/create_net_sec_4.png)

---

#### 7. Confirm the account has been created successfully.
- Once confrimed, click on **Exit Wizard**.

![C1NS1](/images/create_net_sec_6.png) 



---
#### Congrats!! You have successfully integrated your AWS Account with Cloud One - Network Security :cloud: :laptop: :rocket:
