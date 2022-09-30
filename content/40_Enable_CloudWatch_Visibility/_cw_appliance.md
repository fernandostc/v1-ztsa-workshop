---
title: "CloudWatch Visibility - Appliance"
chapter: true
weight: 42
pre: "<b>5.2 </b>"
---

# Enable CloudWatch Visibility for Networks Security Appliance.

{{% notice warning %}}
<p style='text-align: left;'>
<b>Don't not continue with these steps if you have already deployed the Network Security Managed Endpoint Cloudwatch panel. The NS appliance cloudwatch panel is an alternative deployment method.</b>
</p>
{{% /notice %}}

---

#### 1. Navigate to **CloudWatch**.
- In left-hand menu, under Alarms click on **All alarms**.
- Use the search filter: ```Modernization-Workshop-Network-Security-Appliance```.
- Select the **Name** of the alarm.

![CloudWatch2](/images/cw-appliance2.png)

---

#### 2. Copy the Alarm's **ARN** value and the **InstanceId** value.

![CloudWatch2](/images/cw-appliance3.png)

---

#### 3. Launch the CloudFormation Template.

> Let's create the Panel with CloudFormation :laptop: :cloud: :bar_chart:

[![Launch Stack](https://cdn.rawgit.com/buildkite/cloudformation-launch-stack-button-svg/master/launch-stack.svg)](https://console.aws.amazon.com/cloudformation/home#/stacks/new?stackName=Demo-Cloud-One-Network-Security-Panel&templateURL=https://aws-workshop-c1as-cft-templates.s3.amazonaws.com/Network_Security_Appliance_CloudWatch.yml)


---

#### 4. Create Stack.
- click on **Next**.

![CloudWatch2](/images/cw-appliance1.png)


---

#### 5. Specify stack details.
- **Stack name**: ```Demo-Cloud-One-Network-Security-Panel```.
- **AlarmARN**: paste the alarm ARN value here.
- **AlarmInstanceID**: paste the InstanceId value here.
- **C1NSRegion**: aws region Network Security appliance is in.
- **DashboardName**: CloudWatch Panel dashboard name.
- Click on **Next**

![CloudWatch2](/images/cw-appliance4.png)

---

#### 6. (Optional) Configure stack options.
- Add **Tags** if desired.
- Click on **Next**.

![CloudWatch2](/images/cw-appliance5.png)

---

#### 7. Review deployment.
- Click on **Create stack**

![CloudWatch2](/images/cw-appliance6.png)
![CloudWatch2](/images/cw-appliance7.png)

---

#### 8. Wait for the stack to complete.

![CloudWatch2](/images/cw-appliance8.png)
![CloudWatch2](/images/cw-appliance9.png)

---

#### 9. After the CloudWatch Panel Stack has reached Create_Complete, you can view the CloudWatch Panel.

- Navigate to **CloudWatch**.
- Select **Dashboards** from left-hand menu.
- Open Dashboard: **Cloud_One_Network_Security_Panel**.

![CloudWatch2](/images/cw-appliance10.png)

With that you can will be able to use the Dashboard to monitor the Appliance performance and also the Detection and Block statistics.

![CloudWatch2](/images/cw-appliance11.png) 



--------

### Congrats on your custom CloudWatch view from Cloud One - Network Security :star-struck: :robot: :white_check_mark: :cloud:

