---
title: "Validate Network Inspection"
chapter: false
weight: 52
pre: "<b>6.1 </b>"
---

### Let us validate inspection of traffic with the Network Security managed endpoint.

---

#### 1. Distributing the Policy.
- In the Network Security Console select the **Network** tab.
- Click on **Managed Service**

![ns_policy1](/images/deploy_protec_1.png)

---

#### 2. On the Managed Service page, click in **Distribute Policy** and wait until it distribution has finished.

![ns_policy1](/images/endpoint-distribute.png)

---

##### 2.1 Once it finish it will look like the image below.


![ns_policy1](/images/distro_policy_finish_endpoint.png)

--------

#### 3. Validate deployment.
After you complete the deployment of the Network Security endpoints and modify your route tables, verify that deployment was successful from the **Managed Service page**.
- Click on Network Security endpoint A link to view the protection details for that endpoint, including the rates and times of traffic inspected. 

If data appears in the Traffic Inspected graph, then the managed service was successfully deployed. If not traffic inspection data appears, double check the routing in your cloud environment.

![ns_policy1](/images/endpoint_stats1.png)
![ns_policy1](/images/endpoint_stats2.png)

---

#### 4. Navigate to the AWS Console
- Navigate to **EC2**
- Select EC2 instance **DVWA** 
- Copy the **Public IPv4 Address/DNS**

![ns_policy1](/images/dvwa_ip.png)


---

#### 5. Access the web application using the Public IP/DNS. 
- Remember that it will be over HTTP. 
- User: **admin**
- Password: **password**
- **Login**

![ns_policy1](/images/dvwa_login.png)

---

#### 6. DVWA SQL Injection
- Select: **SQL Injection**
- User ID:

        admin ' OR 1=1--'

![ns_policy1](/images/sql_1.png)
![ns_policy1](/images/sql_2.png)

---

#### 6.1 Remember we configured the SQL Injection filters to **Permit**, if you want to you can change it to Block. Let's check our CloudWatch dashboard for the SQL event.

{{% notice note %}}
<p style='text-align: left;'>
If you decide to change this intrusion prevention filter from permit to <b>BLOCK</b> you will need to redistribute the policy before it will take effect.
</p>
{{% /notice %}}

- In AWS Console navigate to **CloudWatch**
- From the left-hand menu select **Dashboards**
- Select: **Cloud_One_Network_Security_Panel**
- Check under **Cloud One Network Security - PERMIT Action**

![ns_policy1](/images/cw_permit_sql.png)


---

#### 7. DVWA Command Injection 
- Select: **Command Injection**
- User ID: <code>127.0.0.1; cat /etc/passwd</code>

![ns_policy1](/images/rce_1.png)

#### 8.1 We configured the Command Injection filter to **Block**, so instead of the attack being permitted a timeout occurs. 

![ns_policy1](/images/timeout.png)

#### 8.2 Let's check our CloudWatch dashboard for the RCE event.
- In AWS Console navigate to **CloudWatch**
- From the left-hand menu select **Dashboards**
- Select: **Cloud_One_Network_Security_Panel**
- Check under **Cloud One Network Security - BLOCK Action**

![ns_policy1](/images/cw_block_rce.png)

---

#### 9. SSH to bastion machine 
- In the AWS Console navigate to **EC2**
- Select EC2 instance: **BastionLinux**
- Click **Connect**
- Select tab: **SSH client**
- Use the SSH Client to connect to the BastionLinux machine. 

![ns_policy1](/images/ec2_bastion.png)
![ns_policy1](/images/ssh_client.png)
![ns_policy1](/images/ssh_shell.png)

---

#### 9.1 Wget Retrieval Attempt - Download Files 
- In the **SSH shell/terminal**
- Run Command: <code>wget http://files.trendmicro.com/products/eicar-file/eicar.com</code>

#### 9.2 Remember we configured the intrusion prevention filter to **Block**, so instead of the file being permitted the Network Security Appliance drops the file attempt and another timeout will occur. 

![ns_policy1](/images/timeout_mfu.png)


#### 9.3 Let's check our CloudWatch dashboard for Wget Retrieval Attempt - Download File
- In AWS Console navigate to **CloudWatch**
- From the left-hand menu select **Dashboards**
- Select: **Cloud_One_Network_Security_Panel**
- Check under **Cloud One Network Security - BLOCK Action**

![ns_policy1](/images/cw_block_mfu.png)


-----
