---
title: "Prerequisites"
chapter: true
weight: 20
pre: "<b>2. </b>"
---
## Prerequisites to start running the labs

As part of this workshop, you will need the following items to be able to build this environment:

#### AWS Account

An <b>AWS Account</b> with <b>AdministratorAccess</b> permission, [Sign up here](https://portal.aws.amazon.com/billing/signup#/start) if it's not already the case! You can learn about the <b>AdministratorAccess</b> permissions [here](https://docs.aws.amazon.com/IAM/latest/UserGuide/getting-started_create-admin-group.html).

<b>[Subscribe](https://aws.amazon.com/marketplace/pp/prodview-skoruk3n7ag5w?sr=0-5&ref_=beagle&applicationId=AWS-Marketplace-Console)</b> to the Trend Micro Zero Trust Secure Access service, available on AWS Marketplace.

---
#### Trend Micro Vision One Account

We have 3 ways to help customers with Free trial:

* Contact your Sales Representative, or 

* [Register](https://resources.trendmicro.com/vision-one-trial.html) on Vision One portal for 30 days free trial, or

* If you are a Trend Micro SE, request Vision One credits using [Jarvis](https://jarvis.trendmicro.com).

---
#### Microsoft Azure AD
Integrate a supported IAM system with Zero Trust Secure Access and grant the required permissions.

Zero Trust Secure Access supports the following IAM systems:

* [Azure AD](https://docs.trendmicro.com/en-us/enterprise/trend-micro-vision-one/zero-trust-secure-ac/gettingstartedchapte/deploymentguides/privateaccesssetupov/iamintegrationovervi/azureadiamsetup.aspx)
* Okta
* Active Directory (on-premises)

You must grant certain permissions within your IAM system to enable Zero Trust Secure Access to monitor user sign-in attempts, access user data, and perform actions on user accounts. To enable user authentication for Private Access and Internet Access, you must configure SAML-based single sign-on (SSO) for your IAM system.

Go to [this url](https://docs.trendmicro.com/en-us/enterprise/trend-micro-vision-one/zero-trust-secure-ac/access-configuration/ztsa-identity-and-ac/iam-system-settings.aspx) to find the required permissions to enable this feature.

If you are planing to use Azure AD with this demo, the instructions on how to integrate Vision One and Azure AD are described [here](https://docs.trendmicro.com/en-us/enterprise/trend-micro-vision-one/zero-trust-secure-ac/gettingstartedchapte/deploymentguides/privateaccesssetupov/iamintegrationovervi/azureadiamsetup.aspx).