---
title: "Managed Service Endpoint Cleanup"
chapter: false
weight: 141
pre: "<b>8.1 </b>"
---


#### 1. Sign into your AWS Console.
- Navigate to **CloudFormation**.

![cleanup](/images/cleanup-ms1.png)

---

#### 2. Select CloudWatch panel Stack: **Demo-Cloud-One-Network-Security-Panel**.
- Click on **Delete** button.

![cleanup](/images/cw_stack_delete.png)

---

#### 3. In a new tab navigate to **AWS VPC**.
- From left-hand menu select **Route Tables**.
- Select Route Table: **Protected Public Routes- C1NS-labenvironment**.
- Select the **Routes** tab.
- Click **Edit Routes**.
- Remove the route with the **VPC Endpoint**.
- Click **Save Changes**.

![cleanup](/images/cleanup-ms2.png)
![cleanup](/images/cleanup-ms3.png)

---


#### 4. Return to route tables home.
- Select Route Table: **Edge association route table**.
- Select the **Routes** tab.
- Click **Edit Routes**.
- Remove the route with the **VPC Endpoint**.
- Click **Save Changes**.

![cleanup](/images/cleanup-ms4.png)
![cleanup](/images/cleanup-ms5.png)

---

#### 5. Remove edge association.
- Select Route Table: **Edge association route table**.
- Select the **Edge Associations** tab.
- Click on **Edit edge association**.
- Remove the edge association.
- Click **Save changes**.

![cleanup](/images/cleanup-ms6.png)
![cleanup](/images/cleanup-ms7.png)

---

#### 6. Select CloudFormaton Stack: **TM-NS-Endpoint-**.
- Delete the stack.
![cleanup](/images/cleanup-ms8.png)

---

#### 7. Select CloudFormaton Stack: **Network-Security-Workshop**.
- Delete the stack.
![cleanup](/images/cleanup-ms9.png)

---

#### 8. Select CloudFormaton Stack: **C1NS-Cloud-Account-Management**.
- Delete the stack.

{{% notice info %}}
<p style='text-align: left;'>
If the stack fails to delete, navigate to VPC and delete the C1-NS-VPC. Once deleted, retry the stack removal.
</p>
{{% /notice %}}

![cleanup](/images/cleanup-ms10.png)


------

### Thank you for joining our workshop! We hope you enjoyed this and learned new things! :clap: :clap:
