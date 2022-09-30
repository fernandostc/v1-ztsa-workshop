---
title: "Deploy the Network Security Endpoint"
chapter: false
weight: 33
pre: "<b>4.3 </b>"
---
 

Deploying Network Security as a managed service requires only a few steps and has no overhead management during or after deployment. With managed service, the traffic in your environment is routed through Network Security endpoints to be inspected. The only items you manage are the Network Security endpoints in your cloud environment; the virtual appliances, as well as any additional infrastructure requirements, are managed by Network Security.

![C1NS1](/images/C1NS_Endpoint.png)

---

#### 1. In the Cloud One Network Security console.
- Click on the **Network** tab
- Select **Managed Service**

![C1NS1](/images/deploy_protec_1.png) 

---

#### 2. Select the VPC that you will deploy the Network Security managed service.

- The ID of the **VPC** can be found in the **Outputs tab** of the base environment CloudFormation template. 
- Once you have located the VPC. Click on **Deploy Protection**
![C1NS1](/images/deploy_protec_2.png) 

---

#### 3. Choose the Availability Zones in your VPC and provide a specific subnet for the inspection endpoint. 
- Check the box for **us-east-1a**
- Optional - Define a name for the subnet
- Select **CIDR**
- Paste ```10.10.0.16/28```
- Click **Create Endpoint** 

{{% notice note %}}
<p style='text-align: left;'>
It takes up to 10 minutes to deploy the Endpoint.
</p>
{{% /notice %}}

![C1NS1](/images/deploy_protec_3.png) 

---

#### 4. Once the creation has started click on View Next Steps.
- Click on **Complete Wizard**.
![C1NS1](/images/deploy_protec_4.png) 
![C1NS1](/images/deploy_protec_5.png)
---

#### 5. Confirm endpoint creation.
- In Cloud One - **Network Security > Network > Managed Service**.
- Expand the VPC to see the status of the enpoint.
![C1NS1](/images/deploy_protec_6.png)
![C1NS1](/images/deploy_protec_7.png)  

---

#### 6. Route network traffic through endpoints.
After your Network Security endpoints have successfully deployed, modify the traffic routes in your cloud environment so that traffic is directed to the Network Security endpoints for inspection.

- Navigate to the **AWS Console > VPC**.
- Under Virtual Private Cloud, click **Route Tables**.
- Click **Create route table**.

![C1NS1](/images/deploy_protec_8.png) 

---

#### 7. Creation of Edge Route Table.
- Name: (optional) ```Edge association route table```
- Select your **VPC ID**.
- Click on **Create Route Table**.

![C1NS1](/images/deploy_protec_9.png)

---

#### 7.1 Edit the Route Table routes.
- Add the following route:
```
Destination   | Target
10.10.10.0/24 | <VPC Endpoint>

```
:information_source: You can find the vpc endpoint on the Cloud One console like you can see in this image here:

![C1NS1](/images/vpce_information.png)


- Click **Save Changes**.

![C1NS1](/images/deploy_protec_10.png)

---


#### 7.2  Create the edge association. 
Create an edge association for this route table. 
- Select the **edge association route table**. 
- Click on the **Edge Associations tab**. 
- Click **Edit edge associations**. 
- Select the Internet Gateway and any Virtual Private Gateways that you want to protect, and then click Save changes.

![C1NS1](/images/deploy_protec_12.png)
![C1NS1](/images/deploy_protec_13.png) 

---

#### 8. Create the Network Security endpoint subnet route table
This route table is associated with the Network Security endpoints that you deployed for this VPC.
- Name: (optional) ```Network Security endpoint subnet route table```
- Select your **VPC ID**.
- Click on **Create Route Table**.

![C1NS1](/images/deploy_protec_14.png) 
 

---

#### 8.1 Edit the Route Table routes.
- Add the following route:
```
Destination   | Target
0.0.0.0/0     | <IGW>


```
- Click **Save Changes**.
![C1NS1](/images/deploy_protec_15.png)

---

#### 8.2  Create subnet association.
- Select the **Network Security endpoint subnet route table**. 
- Click the **Subnet Associations tab**. 
- Click **Edit subnet associations**. 
- Select the subnet that contains the **Network Security endpoint**. 
- Create a subnet association for this route table for the subnet that contains a Network Security endpoint.

![C1NS1](/images/deploy_protec_16.png)
![C1NS1](/images/deploy_protec_17.png)

---
#### 9. Modify the public subnet route table.
- Select the Route Table named: ```Protected Public Routes - C1NS-labenvironment```
- Select the **Routes tab**.
- Click on **Edit routes**.

![C1NS1](/images/deploy_protec_18.png)

- **Modify** the route
- Click on **Save Changes**.
```
Destination   | Target
0.0.0.0/0     | <VPC Endpoint>

```
![C1NS1](/images/deploy_protec_19.png)


---
> **Et voila, we just generated configured the routing for the managed service enpoint in our AWS environment** 🤩 :cloud: 🤖 :rocket:
