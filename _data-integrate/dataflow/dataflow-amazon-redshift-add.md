---
title: [Add an Amazon Redshift database connection]
last_updated: 7/3/2020
toc: true
sidebar: mydoc_sidebar
permalink: /:collection/:path.html
---
You can add a connection to an Amazon Redshift database using ThoughtSpot DataFlow.

Follow these steps:

{% include content/dataflow/add-database-connection.md %}

4. After you select the Amazon Redshift **Connection type**, the rest of the connection properties appear.

   <details>
     <summary>See the <strong>Create connection</strong> screen for Amazon Redshift</summary>
     <p>
      <img src="../../images/dataflow-amazon-redshift-create.png" alt="Create Amazon Redshift connection" /></p>
   </details>

   * [Connection name]({{ site.baseurl }}/data-integrate/dataflow/dataflow-amazon-redshift-reference.html#dataflow-amazon-redshift-conn-connection-name)<br/>Name your connection.
   * [Connection type]({{ site.baseurl }}/data-integrate/dataflow/dataflow-amazon-redshift-reference.html#dataflow-amazon-redshift-conn-connection-type)<br/>Choose the Amazon Redshsift connection type.
   * [Host]({{ site.baseurl }}/data-integrate/dataflow/dataflow-amazon-redshift-reference.html#dataflow-amazon-redshift-conn-host)<br/>Specify the hostname or the IP address of the Redshift system<br/>Mandatory field.
   * [Port]({{ site.baseurl }}/data-integrate/dataflow/dataflow-amazon-redshift-reference.html#dataflow-amazon-redshift-conn-port)<br/>Specify the port associated to the Redshift system<br/>Mandatory field.
   * [User]({{ site.baseurl }}/data-integrate/dataflow/dataflow-amazon-redshift-reference.html#dataflow-amazon-redshift-conn-user)<br/>Specify the user to connect to Amazon Redshift. This user must have data access privileges.
   * [Password]({{ site.baseurl }}/data-integrate/dataflow/dataflow-amazon-redshift-reference.html#dataflow-amazon-redshift-conn-password)<br/>Specify the password for the User.
   * [Database]({{ site.baseurl }}/data-integrate/dataflow/dataflow-amazon-redshift-reference.html#dataflow-amazon-redshift-conn-database)<br/>Collection of information that is organized so that it can be easily accessed, managed and updated.

   See [Connection properties]({{ site.baseurl }}/data-integrate/dataflow/dataflow-amazon-redshift-reference.html#connection-properties) for details, defaults, and examples.

5. Click **Create connection**.   