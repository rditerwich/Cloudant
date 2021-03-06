---

copyright:
  years: 2017, 2018
lastupdated: "2018-12-10"

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}

<!-- Acrolinx: 2018-08-20 -->

# Creating an {{site.data.keyword.cloudant_short_notm}} instance on {{site.data.keyword.cloud_notm}} by using the {{site.data.keyword.cloud_notm}} CLI

This tutorial shows you how to create an {{site.data.keyword.cloudantfull}} service instance on {{site.data.keyword.cloud}}
by using the {{site.data.keyword.cloud_notm}} CLI.
{:shortdesc}

## Prerequisites 

To follow this tutorial, you must first install the {{site.data.keyword.cloud_notm}} CLI developer tools. For more information about installing the tools, see the [Getting started with the {{site.data.keyword.cloud_notm}} CLI ![External link icon](../images/launch-glyph.svg "External link icon")](https://console.bluemix.net/docs/cli/index.html#overview){:new_window} tutorial.

## Identifying the {{site.data.keyword.cloud_notm}} API endpoint

Specify the target API endpoint for your {{site.data.keyword.cloud_notm}} commands:

```sh
ibmcloud api https://api.ng.bluemix.net
```
{:codeblock}

The result confirms that you correctly identified the endpoint:

```sh
Setting api endpoint to https://api.ng.bluemix.net...
OK

API endpoint: https://api.ng.bluemix.net (API version: 2.54.0)
Not logged in. Use 'ibmcloud login' to log in.
```
{:pre}

## Logging in to your {{site.data.keyword.cloud_notm}} account

The following example describes the login process. If you are using a federated user ID, it is important that you switch to a one-time passcode (`ibmcloud login --sso`), or use an API key (`ibmcloud --apikey key or @key_file`) to authenticate. For more information about how to log in using the CLI, see [General CLI (ibmcloud) commands ![External link icon](../images/launch-glyph.svg "External link icon")](https://console.bluemix.net/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_login){:new_window} under `ibmcloud login`. 

1.  Start the login process for
  your {{site.data.keyword.cloud_notm}} account by using the following command:
  
  ```sh
  ibmcloud login
  ```
  {:codeblock}
  
  {{site.data.keyword.cloud_notm}} responds by reminding you of the current
  API endpoint, and asks for the email address of your account:
  
  ```sh
  API endpoint: https://api.ng.bluemix.net
  
  Email>
  ```
  {:pre}

2.  Enter the email address of your account, and then enter your password:

  ```sh
  API endpoint: https://api.ng.bluemix.net
  
  Email> J.Doe@email.com
  
  Password>
  ```
  {:pre}
  
  {{site.data.keyword.cloud_notm}} validates your details and summarizes the information about your login session:

  ```sh
  API endpoint: https://api.ng.bluemix.net
  
  Email> J.Doe@email.com
  
  Password> 
  Authenticating...
  OK
  
  Targeted account J DOE's Account (707...a32)
  
  Targeted org J.Doe@email.com
  
  Targeted space dev
  
  API endpoint:   https://api.ng.bluemix.net (API version: 2.54.0)
  Region:         us-south
  User:           j.doe@email.com
  Account:        J DOE's Account (707...a32)
  Org:            J.Doe@email.com
  Space:          dev
  ```
  {:pre}

3.  You are now logged in to your {{site.data.keyword.cloud_notm}} account.

## Choosing the {{site.data.keyword.cloudant_short_notm}} plan for your service

See the [Plans ![External link icon](../images/launch-glyph.svg "External link icon")](https://console.bluemix.net/docs/services/Cloudant/offerings/bluemix.html#plans){:new_window} section of the documentation for details on using the {{site.data.keyword.cloudant_short_notm}} Lite or Standard plan.
{:pre}

## Creating the {{site.data.keyword.cloudant_short_notm}} service

{{site.data.keyword.cloudant_short_notm}} uses Resource Groups for provisioning new instances rather than Cloud Foundry orgs and spaces. {{site.data.keyword.cloudant_short_notm}} instances that are provisioned in the past can still be deployed in Cloud Foundry orgs and spaces. For more information, see the [How does IBM Cloudant work with IBM Cloud Resource Groups? ![External link icon](../images/launch-glyph.svg "External link icon")](https://console.bluemix.net/docs/services/Cloudant/guides/resource-groups.html#how-does-ibm-cloudant-work-with-ibm-cloud-resource-groups-){:new_window} guide.

First, set your target Resource Group and region as shown in [General CLI (ibmcloud) commands ![External link icon](../images/launch-glyph.svg "External link icon")](https://console.bluemix.net/docs/cli/reference/ibmcloud/bx_cli.html#ibmcloud_target){:new_window} under `ibmcloud target` by using the following format:

```sh
ibmcloud target [-r REGION_NAME] [-g RESOURCE_GROUP]
```

For a list of regions, run this command:

```sh
ibmcloud regions
```

For a list of resource groups, run this command: 

```sh
ibmcloud resource groups
```

Second, to create a service instance, the basic command format within {{site.data.keyword.cloud_notm}} is as follows:

```sh
ibmcloud resource service-instance-create NAME SERVICE_NAME|SERVICE_ID SERVICE_PLAN_NAME|SERVICE_PLAN_ID LOCATION [-p, --parameters @JSON_FILE | JSON_STRING ]
```
{:pre}

The fields are described in the following table: 


Field | Description
------|------------
`NAME` | Arbitrary name that you give to the instance. 
`SERVICE_NAME` | `cloudantnosqldb`
`PLAN_NAME` | Lite plan or Standard plan.
`LOCATION` | The location where you want to deploy: AP North, Germany, Global, Sydney, United Kingdom, US East, or US South. 
`legacyCredentials` | Defaults to true. This field dictates whether the instance uses both legacy and IAM credentials or IAM credentials only. 

For more information about choosing an authentication method, see the [IAM guide](../guides/iam.html#ibm-cloud-identity-and-access-management-iam-){:new_window}.

In this example, we want to create an instance of an {{site.data.keyword.cloudant_short_notm}} service by using the `Lite` plan (where the instance name is `cs20170517a` in the US-South location and uses IAM credentials only), you create this instance by using a command similar to the following example:

```sh
ibmcloud resource service-instance-create cs20170517a cloudantnosqldb lite us-south -p '{"legacyCredentials": false}'
```
{:codeblock}

After creating the service instance, {{site.data.keyword.cloud_notm}}
responds with a message similar to the following example:

```sh
Creating service instance cs20170517a in resource group default of account John Does's Account as j.doe@email.com...
OK
Service instance cs20170517a was created.
Name          Location   State    Type               Tags   
cs20170517a   us-south   active   service_instance  
```
{:pre}

## Creating credentials for your {{site.data.keyword.cloudant_short_notm}} service

Applications that require access to your {{site.data.keyword.cloudant_short_notm}} service
must have the necessary credentials.

Service credentials are valuable. If anyone or any application has access to the credentials, they can effectively do whatever they want with the service instance. For example, they might create spurious data, or delete valuable information. Protect these credentials carefully.
{: tip}

For more information about the fields included in the service credentials, see the [IAM guide](../guides/iam.html#ibm-cloud-identity-and-access-management-iam-){:new_window}.

The basic command format to create credentials for a service instance
within {{site.data.keyword.cloud_notm}} is as follows:

```sh
ibmcloud resource service-key-create NAME ROLE_NAME --instance-name SERVICE_INSTANCE_NAME
```
{:pre}

The fields are described in the following table:

Field | Description
------|------------
`NAME` | Arbitrary name that you give the service credentials. 
`ROLE_NAME` | This field currently allows the Manager role only.
`SERVICE_INSTANCE_NAME` | The name you give to your {{site.data.keyword.cloudant_short_notm}} instance. 

Ifyou want to create credentials for the `cs20170517a` instance of
an {{site.data.keyword.cloudant_short_notm}} service (where the name for the credentials is `creds_for_cs20170517a`), you create these credentials by using a command similar to the following example:

```sh
ibmcloud resource service-key-create creds_for_cs20170517a Manager --instance-name cs20170517a
```
{:codeblock}
After receiving the request to create credentials for the service instance, {{site.data.keyword.cloud_notm}} responds with a message similar to the following example:

```sh
Creating service key in resource group default of account John Does's Account as john.doe@email.com...
OK
Service key crn:v1:bluemix:public:cloudantnosqldb:us-south:a/b42223455bb7e2abb0841ca25d28ee4c:ee78351d-82bf-4e80-bc22-825c937fafa3:resource-key:621ffde2-ea10-4318-b297-d6d849cec48a was created.
                  
Name:          creds_for_cs20170517a   
ID:            crn:v1:bluemix:public:cloudantnosqldb:us-south:a/b42223455bb7e2abb0841ca25d28ee4c:ee78351d-82bf-4e80-bc22-825c937fafa3:resource-key:621ffde2-ea10-4318-b297-d6d849cec48a   
Created At:    Tue Sep 18 19:58:38 UTC 2018   
State:         active   
Credentials:                                   
               iam_apikey_name:          auto-generated-apikey-621ffde2-ea10-4318-b297-d6d849cec48a      
               iam_role_crn:             crn:v1:bluemix:public:iam::::serviceRole:Manager      
               url:                      https://f6cf0c55-48ea-4908-b441-a962b27d3bb6-bluemix:5811381f6daff7255b288695c3544be63f550e975bcde46799473e69c7d48d61@f6cf0c55-48ea-4908-b441-a962b27d3bb6-bluemix.cloudant.com      
               username:                 f6cf0c55-48ea-4908-b441-a962b27d3bb6-bluemix      
               port:                     443      
               apikey:                   XXXXX-XXXXXX_XXXXXXXXXXXXX-XXXXXXXXXXX      
               host:                     f6cf0c55-48ea-4908-b441-a962b27d3bb6-bluemix.cloudant.com      
               iam_apikey_description:   Auto generated apikey during resource-key operation for Instance - crn:v1:bluemix:public:cloudantnosqldb:us-south:a/b42116849bb7e2abb0841ca25d28ee4c:ee78351d-82bf-4e80-bc22-825c937fafa3::      
               iam_serviceid_crn:        crn:v1:bluemix:public:iam-identity::a/b42116849bb7e2abb0841ca25d28ee4c::serviceid:ServiceId-53f9e2a2-cdfb-4f90-b072-bfffafb68b3e      
               password:                 581138...7d48d61 
```
{:pre}

## Listing the service credentials for your {{site.data.keyword.cloudant_short_notm}} service

The basic command format to retrieve the credentials for a service instance
within {{site.data.keyword.cloud_notm}} is as follows:

```sh
ibmcloud resource service-key KEY_NAME
```
{:pre}

In this example, we want to retrieve credentials for the `cs20170517a` instance of
an {{site.data.keyword.cloudant_short_notm}} service
(where the name for the credentials is `creds_for_cs20170517a`), you retrieve the credentials by using a command similar to the following example:

```sh
ibmcloud resource service-key creds_for_cs20170517b
```
{:codeblock}

After receiving the request to retrieve the credentials for the service instance,
{{site.data.keyword.cloud_notm}} responds with a message similar to the following (abbreviated) example:

```sh
Retrieving service key in resource group default of account John Does's Account as john.doe@email.com...
OK
Service key crn:v1:bluemix:public:cloudantnosqldb:us-south:a/b42223455bb7e2abb0841ca25d28ee4c:ee78351d-82bf-4e80-bc22-825c937fafa3:resource-key:621ffde2-ea10-4318-b297-d6d849cec48a was created.
                  
Name:          creds_for_cs20170517a   
ID:            crn:v1:bluemix:public:cloudantnosqldb:us-south:a/b42223455bb7e2abb0841ca25d28ee4c:ee78351d-82bf-4e80-bc22-825c937fafa3:resource-key:621ffde2-ea10-4318-b297-d6d849cec48a   
Created At:    Tue Sep 18 19:58:38 UTC 2018   
State:         active   
Credentials:                                   
               iam_apikey_name:          auto-generated-apikey-621ffde2-ea10-4318-b297-d6d849cec48a      
               iam_role_crn:             crn:v1:bluemix:public:iam::::serviceRole:Manager      
               url:                      https://f6cf0c55-48ea-4908-b441-a962b27d3bb6-bluemix:5811381f6daff7255b288695c3544be63f550e975bcde46799473e69c7d48d61@f6cf0c55-48ea-4908-b441-a962b27d3bb6-bluemix.cloudant.com      
               username:                 f6cf0c55-48ea-4908-b441-a962b27d3bb6-bluemix      
               port:                     443      
               apikey:                   XXXXX-XXXXXX_XXXXXXXXXXXXX-XXXXXXXXXXX      
               host:                     f6cf0c55-48ea-4908-b441-a962b27d3bb6-bluemix.cloudant.com      
               iam_apikey_description:   Auto generated apikey during resource-key operation for Instance - crn:v1:bluemix:public:cloudantnosqldb:us-south:a/b42116849bb7e2abb0841ca25d28ee4c:ee78351d-82bf-4e80-bc22-825c937fafa3::      
               iam_serviceid_crn:        crn:v1:bluemix:public:iam-identity::a/b42116849bb7e2abb0841ca25d28ee4c::serviceid:ServiceId-53f9e2a2-cdfb-4f90-b072-bfffafb68b3e      
               password:                 581138...7d48d61 
```
{:pre}

## Using your {{site.data.keyword.cloudant_short_notm}} service instance

Now, you are finished with the following tasks:

1.  Created an {{site.data.keyword.cloudant_short_notm}} service
  instance within {{site.data.keyword.cloud_notm}}.
2.  Created credentials for the {{site.data.keyword.cloudant_short_notm}} service instance.
3.  Retrieved the service instance credentials, so that they can be used by your application.

For more information, see the [Creating and populating a simple {{site.data.keyword.cloudant_short_notm}} database on {{site.data.keyword.cloud_notm}}](../tutorials/create_database.html#context){:new_window} tutorial that shows you how to use an {{site.data.keyword.cloudant_short_notm}} service instance from a Python application by using legacy credentials. Remember to substitute the credentials you created in this tutorial.

## (Optional) Tidying up afterward

The following short list of commands might be helpful in tidying up your development environment.

### Deleting service credentials

To delete a set of service credentials,
use a command like this one:

```sh
ibmcloud resource service-key-delete KEY_NAME
```
{:pre}

For example,
to delete the credentials called `creds_for_cs20170517a`, use a command like this one:

```sh
ibmcloud resource service-key-delete creds_for_cs20170517a
```
{:pre}

### Deleting a service instance

To delete a service instance,
use a command like this one:

```sh
ibmcloud resource service-instance-delete SERVICE_INSTANCE_NAME
```
{:pre}

For example,
to delete the `cs20170517a` instance of
an {{site.data.keyword.cloudant_short_notm}} service,
use a command like this one:

```sh
ibmcloud resource service-instance-delete cs20170517a
```
{:pre}

