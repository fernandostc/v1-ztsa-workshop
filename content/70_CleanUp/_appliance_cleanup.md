---
title: "Appliance Cleanup"
chapter: false
weight: 142
pre: "<b>8.2 </b>"
---


#### 1. Sign into your AWS Console.
- Navigate to **CloudFormation**

![cleanup](/images/cleanup-appliance1.png)

---

#### 2. Select CloudWatch panel Stack: **Demo-Cloud-One-Network-Security-Panel**
- Click on **Delete** button

![cleanup](/images/cw_stack_delete.png)

---

#### 3. Select Network Security Appliance Stack: **Modernization-Workshop-Network-Security-Appliance**
- Click on **Delete** button
- This stack will take a few minutes to delete

![cleanup](/images/ns_stack_delete.png)


---

#### 4. Select Network Security Account Stack: **C1NS-Cloud-Account-Management**
- Click on **Delete** button

![cleanup](/images/cleanup-appliance2.png)

---

#### 5. In a new tab navigate to **AWS VPC**.
- From left-hand menu select **Route Tables**.
- Select Route Table: **Protected Public Routes- C1NS-labenvironment**.
- From the details section, choose the **subnet associations** tab.
- Click on **Edit subnet associations**.
- **Remove all** subnet associations.
- Click on **Save associations**.

![cleanup](/images/cleanup-appliance3.png)
![cleanup](/images/cleanup-appliance4.png)

---

#### 6. Delete the route table.
- Select Route Table: **Protected Public Routes- C1NS-labenvironment**.
- Actions: **Delete Route Table**.
- Type **delete**.
- Click **Delete**.

![cleanup](/images/route_tables.png)
![cleanup](/images/route_tables_delete.png)

---

#### 7. Navigate to CloudFormation. 
- Select base VPC Stack: example **Network-Security-Workshop**.
- Click on stack actions, choose **Delete stack** button.
- This stack will take a few minutes to delete.

![cleanup](/images/vpc_stack_delete.png)

------

### Thank you for joining our workshop! We hope you enjoyed this and learned new things! :clap: :clap: