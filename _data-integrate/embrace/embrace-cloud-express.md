---
title: [Cloud Express for Embrace]
last_updated: 10/21/2019
toc: true
summary: "With Cloud Express, you can easily try ThoughtSpot Embrace through a simple cloud-based deployment."
sidebar: mydoc_sidebar
permalink: /:collection/:path.html
---
With Cloud Express, you can easily connect your production data in an existing cloud data warehouse to ThoughtSpot using ThoughtSpot Embrace.  

Cloud Express benefits:
- Easy to sign up
- Up and running in 5 minutes
- Zero ThoughtSpot software cost
- No more than $100 to $150 per month infrastructure cost
- No or minimal data modeling
- Successful search-driven insights in 45 minutes from launch

## Features

<table width="100%" border="0">
  <tbody>
	<tr>
      <td>&#9989;</td>
      <td>5 Users</td>
    </tr>  
    <tr>
      <td>&#9989;</td>
      <td>20 million rows</td>
    </tr>
    <tr>
      <td>&#9989;</td>
      <td>Snowflake, AWS Redshift data warehouses</td>
    </tr>
    <tr>
      <td>&#9989;</td>
      <td>Self-service upgrade (Download and access for new release)</td>
    </tr>
    <tr>
      <td>&#9989;</td>
      <td>Measure usage using MixPanel: number of users created, number of rows, queries, objects created, and more</td>
    </tr>
    <tr>
      <td>&#9989;</td>
      <td>SAML*</td>
    </tr>
    <tr>
      <td>&#9989;</td>
      <td>Restore from snapshot*</td>
    </tr>
    <tr>
      <td>&#10060;</td>
      <td>Upload user data</td>
    </tr>
    <tr>
      <td>&#10060;</td>
      <td>Backup</td>
    </tr>
    <tr>
      <td>&#10060;</td>
      <td>Restore from backup</td>
    </tr>
    <tr>
      <td colspan="2"><i>*Available through the ThoughtSpot Management Console ( <b>Admin > Settings</b> )</i></td>
    </tr>
  </tbody>
</table>



## Sign up for Cloud Express

To sign up for Cloud Express, do the following:

1. Go to the ThoughtSpot marketing site [URL TBD].

2. Sign up by providing the following information:
   - Name
   - Email address
   - Company name
   - Phone number
3. After you sign up, you receive an email that contains a license key and instructions.

## Deploy Cloud Express

To deploy Cloud Express, do the following:

1. Open the email you received and download the license key to your computer.
2. Click the link in the email to go to the [AWS marketplace](https://aws.amazon.com/marketplace){:target="_blank"}.
3. Search for ThoughtSpot in AWS marketplace
4. In the search results, click the free trial for Cloud Express.
5. Sign in to AWS using your corporate account.
6. Click the **Continue to Subscribe** button.
7. Accept the terms and conditions, by clicking **Accept Terms**, and then click **Continue to Configuration**.
8. On the _Configure this software_ page, select software version 6.0, your region, and click **Continue to Launch**.
9. On the _Launch this software_ page, if you have not signed up yet, click **Usage Instructions** and follow the instructions in step 2 of [Sign up for Cloud Express]({{ site.baseurl }}/data-integrate/embrace/embrace-cloud-express.html#sign-up-for-cloud-express). Once you're signed up, go to the next step.
10. On the _Launch this software_ page, work with your IT group to select the VPC, Subnet and Keypair settings, and then click **Launch**. Once your ThoughtSpot instance launches, the _Launch this software_ page appears.
11. Click the **EC2 Console** link to view the status of your instance.
12. Save the **Instance ID**, and, under the _Description_ tab at the bottom of the page, the **IPv4 Public IP**. You use the Instance ID to sign in to your instance. The IPv4 Public IP is the URL of your instance.
13. Once your instance is up and running, go to the URL you copied in the previous step and sign in to your ThoughtSpot instance, using the following credentials:
  - Username: **tsadmin**
  - Password: **\<Instance-ID>-TS** _(example: i-035ab9c2900ed9fbf-TS)_
      After you sign in, the _Upload the license key file_ page appears.
14. Upload the license key file you received from ThoughtSpot.
15. After the license key file is uploaded, you are interactively guided through onboarding into ThoughtSpot.
16. If you are going to connect to a Snowflake data warehouse, be sure to enable AWS Private Link for Snowflake. For details, see Snowflake's documentation [Enabling AWS PrivateLink](https://docs.snowflake.net/manuals/user-guide/admin-security-privatelink.html#enabling-aws-privatelink){:target="_blank"} for details.

## Connect to your data warehouse

Before you begin, read the available best practices for your data warehouse:
- [Snowflake best practices]({{ site.baseurl }}/data-integrate/embrace/embrace-snowflake-add.html)

To connect to your data warehouse, do the following:

1. Sign in to your ThoughtSpot instance.
2. Connect to your data warehouse. For details, see:
- [Add a Snowflake connection]({{ site.baseurl }}/data-integrate/embrace/embrace-snowflake-add.html)
- [Add a Redshift connection]({{ site.baseurl }}/data-integrate/embrace/embrace-redshift-add.html)
- [Add a BigQuery connection]({{ site.baseurl }}/data-integrate/embrace/embrace-gbq-add.html)
- [Add a Synapse connection]({{ site.baseurl }}/data-integrate/embrace/embrace-synapse-add.html)  

   When you create a connection to your data warehouse, you specify the tables and columns you want to link to.

3. Once you create your connection, you can search the connected tables and columns of your data warehouse right away, as you would any tables and columns in ThoughtSpot's internal database.  