---
title: "Enable CloudWatch Visibility"
chapter: true
weight: 40
pre: "<b>5. </b>"
---

# Enable CloudWatch Visibility

Amazon CloudWatch dashboards are customizable home pages in the CloudWatch console that you can use to monitor your resources in a single view, even those resources that are spread across different Regions. You can use CloudWatch dashboards to create customized views of the metrics and alarms for your AWS resources.

### Create an Amazon CloudWatch Panel

The form of consumption of logs by Trend Micro Cloud One - Network Security takes place through third party integrations, you can use any Syslog Server/SIEM but in this workshop we will use Amazon CloudWatch.

To do it you can read the logs in the CloudWatch service or we can create a custom Panel in Amazon CloudWatch. For this approach we can deploy CloudFormation template to simplify our life.

----
