---
title: [Modify a Snowflake connection]
last_updated: 2/28/2020
summary: Learn how to modify a Snowflake connection and its tables.
sidebar: mydoc_sidebar
permalink: /:collection/:path.html
---

You can modify an Embrace Snowflake connection in the following ways:
{% include content/embrace/modify-options.md %}

{: id="edit-connection"}
## Editing a Snowflake connection

You can edit a Snowflake connection to add tables and columns.

{% include content/embrace/edit-connection-1-3.md %}

   ![Select connection]({{ site.baseurl }}/images/snowflake-select-connection.png "Select Connection")

{% include content/embrace/edit-connection-4.md %}

   ![Edit connection]({{ site.baseurl }}/images/snowflake-editconnection.png "Edit connection")

5. On the **Choose connection type** page, you have the option to change the [Connection name]({{ site.baseurl }}/data-integrate/embrace/embrace-snowflake-reference.html#connecion_name) or [Connection description]({{ site.baseurl }}/data-integrate/embrace/embrace-snowflake-reference.html#connection_description).

   Click **Continue**.  

6. On the Snowflake connection details page, make any necessary changes (to [Account name]({{ site.baseurl }}/data-integrate/embrace/embrace-snowflake-reference.html#account_name), [User]({{ site.baseurl }}/data-integrate/embrace/embrace-snowflake-reference.html#user), [Password]({{ site.baseurl }}/data-integrate/embrace/embrace-snowflake-reference.html#password), [Role]({{ site.baseurl }}/data-integrate/embrace/embrace-snowflake-reference.html#role), [Warehouse]({{ site.baseurl }}/data-integrate/embrace/embrace-snowflake-reference.html#warehouse), [Database]({{ site.baseurl }}/data-integrate/embrace/embrace-snowflake-reference.html#database), or [Schema]({{ site.baseurl }}/data-integrate/embrace/embrace-snowflake-reference.html#schema)), and then click **Continue**.

   Refer to the [Snowflake connection reference]({{ site.baseurl }}/data-integrate/embrace/embrace-snowflake-reference.html#) for more information on each of the specific attributes you must enter for your connection.

{% include content/embrace/edit-connection-7-8.md %}

To remove a table from a connection, delete it from the connection details page. See [Deleting a table]({{ site.baseurl }}/data-integrate/embrace/embrace-snowflake-modify.html#delete-table).

{% include tip.html content="You cannot remove an existing table column from Embrace." %}

{: id="remap-connection"}
## Remapping a Snowflake connection

{% include content/embrace/remap-intro-1-3.md %}

   ![Select a connection type]({{ site.baseurl }}/images/snowflake-select-connection.png "Select a connection type")

{% include content/embrace/remap-4.md %}

    ![Remap a connection]({{ site.baseurl }}/images/snowflake-remapping.png "Remap a connection")

{% include content/embrace/remap-5.md %}

    !["Download the source mapping file"]({{ site.baseurl }}/images/snowflake-downloadyaml.png "Download the source mapping file")

{% include content/embrace/remap-6.md %}

    ![Edit yaml file]({{ site.baseurl }}/images/snowflake-yaml.png "Edit yaml")

{% include content/embrace/remap-7.md %}

{: id="delete-table"}
## Deleting a table from a Snowflake connection

ThoughtSpot checks for dependencies whenever you try to remove a table in a connection. ThoughtSpot shows a list of dependent objects, and you can click them to delete them or remove the dependency. Then you can remove the table.

To delete a table, follow these steps:

1. Click **Data** in the top navigation bar.

2. Click the **Connections** tab at the top of the page.

3. Click the name of the connection that contains the table you want to delete.

   ![]({{ site.baseurl }}/images/snowflake-select-connection.png "Select a connection type")

4. Find the table you want to delete in the list, and check the box next to its name.

5. Click **Delete**, and then click **Delete** again to confirm.

    ![Delete a connection table]({{ site.baseurl }}/images/snowflake-deletetable.png "Delete a connection table")

    If you attempt to delete a table with dependent objects, the operation is blocked. A *Cannot delete* window appears, with a list of links to dependent objects. See [Deleting a table with dependent objects]({{ site.baseurl }}/data-integrate/embrace/embrace-snowflake-modify.html#deleting-a-table-with-dependent-objects).

{: id="delete-table-dependencies"}
## Deleting a table with dependent objects

In the *Cannot delete* window, click the link for each object to modify or delete it.

After handling and removing all dependencies, you can delete the table.

![]({{ site.baseurl }}/images/delete-warning.png "Dependent objects warning")

You can also click the name of a table and then click the linked objects to see a list of dependent objects with links. The list shows the names of the dependent objects (worksheets, pinboards or answers), and the columns they use from that table. You can use this information to determine the impact of changing the structure of the data source or to see how widely used it is. Click a dependent object to modify or delete it.

{: id="delete-connection"}
## Deleting a Snowflake connection

A connection can be used in multiple data sources or visualizations. Because of this, you must delete all of the sources and tasks that use that connection, before you can delete the connection.

To delete a connection, follow these steps:

1. Click **Data** in the top navigation bar.

2. Click the **Connections** tab at the top of the page.

3. Check the box next to the connection you want to delete.

4. Click **Delete**, and then click **Delete** again to confirm.

   ![Delete connection]({{ site.baseurl }}/images/snowflake-delete-connection.png "delete a connection")
   <!--![]({{ site.baseurl }}/images/delete-a-connection.png "delete a connection type")-->

   If you attempt to delete a connection with dependent objects, the operation is blocked, and a *Cannot delete* warning appears, with a list of linked dependent objects.

   ![]({{ site.baseurl }}/images/connection-delete-warning.png "warning connection type")

5. If the *Cannot delete* warning appears, click the link for each object to delete it, and then click **Ok**. Otherwise, go to the next step.

6. After handling and removing all dependencies, you can delete the connection by clicking **Delete**, and then clicking **Delete** again to confirm.

{% include tip.html content="You candelete multiple Embrace." %}
