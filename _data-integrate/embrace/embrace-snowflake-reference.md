---
title: [Snowflake connection reference]
summary: Learn about the fields used to create a Snowflake connection with ThoughtSpot Embrace.
last_updated: 02/28/2020
sidebar: mydoc_sidebar
permalink: /:collection/:path.html
---

Here is a list of the fields of a Snowflake connection in ThoughtSpot Embrace. You must have specific information to establish a seamless and secure connection.

 <dl>
   <dlentry id="connection_name">
     <dt>Connection name</dt>
     <dd>Mandatory. Enter a new Snowflake connection name.</dd>
   </dlentry>
   <dlentry id="connection_description">
     <dt>Connection description</dt>
     <dd>Optional. Provide a short description about the connection.</dd>
   </dlentry>
   <dlentry id="account_name">
     <dt>Account name</dt>
     <dd>Mandatory. Enter the account name associated with the Snowflake connection. The account name is the entire URL that precedes <code>snowlfakecomputiong.com</code>.</dd>
   </dlentry>
   <dlentry id="user">
     <dt>User</dt>
     <dd>Mandatory. Enter the Snowflake account username.</dd>
   </dlentry>
   <dlentry id="password">
     <dt>Password</dt>
     <dd>Mandatory. Enter the Snowflake account password.</dd>
   </dlentry>
   <dlentry id="role">
     <dt>Role</dt>
     <dd>Mandatory. Specify the privilege of the user.</dd>
   </dlentry>
   <dlentry id="warehouse">
     <dt>Warehouse</dt>
     <dd>Mandatory. Specify the warehouse associated with the connection.</dd>
   </dlentry>
   <dlentry id="database">
     <dt>Database</dt>
     <dd>Optional. Specify the database associated with the account.</dd>
   </dlentry>
   <dlentry id="schema">
     <dt>Schema</dt>
     <dd>Optional. Specify the schema associated with the database.</dd>
   </dlentry>
</dl>
