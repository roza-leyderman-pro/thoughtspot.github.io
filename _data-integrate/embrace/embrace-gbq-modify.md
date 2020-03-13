---
title: [Modify a BigQuery connection]
last_updated: 1/30/2020
summary: Learn how to modify a BigQuery connection and its tables.
sidebar: mydoc_sidebar
permalink: /:collection/:path.html
---

You can modify an Embrace BigQuery connection in the following ways:
{% include content/embrace/modify-options.md %}

{: id="edit-connection"}
## Editing a BigQuery connection

You can edit a BigQuery connection to add new tables and columns.

To edit a connection, follow these steps:

{% include content/embrace/edit-connection-1-3.md %}

1. Click **Data** in the top navigation bar.

2. Click the **Connections** tab at the top of the page.

3. Click the name of the connection you plan to edit.

   ![Select a connection to edit]({{ site.baseurl }}/images/gbq-chooseconnection.png "Select a connection to edit")

4. Click **Edit connection** at the upper-right-hand side of the page.

   ![Edit connection]({{ site.baseurl }}/images/gbq-editconnection.png "Edit connection")

5. On the Choose connection type page, change the connection name or description (if needed), and then click **Continue**.  

6. On the BigQuery connection details page, make any changes needed, and then click **Continue**.

7. Expand the database table drop-down menu, and select the tables and columns you want to add.

   ![Select tables and columns]({{ site.baseurl }}/images/embrace-edit-tables.png "Select tables and columns")

8. Click **Update**, and then click **Confirm** to save the updated connection detail.

To remove a table from a connection, delete it from the connection details page. For more information, see [Deleting a table]({{ site.baseurl }}/data-integrate/embrace/embrace-gbq-modify.html#deleting-a-table-from-a-bigquery-connection).

{: id="remap-connection"}
## Remapping a BigQuery connection

Modify the connection parameters by editing the source mapping <code>yaml</code> file that was created when you added the connection. For example, you can remap the existing table or column to a different table or column in an existing database connection. ThoughtSpot recommends that you check the dependencies before and after you remap a table or column in a connection to ensure they display as intended.

To remap a connection:

1. Click **Data** in the top navigation bar.

2. Click the **Connections** tab at the top of the page.

3. Click the name of the connection you want to remap.
    ![Select a connection to remap]({{ site.baseurl }}/images/gbq-chooseconnection.png "Select a connection to remap")

4. Click the More Info icon ![more options menu icon]({{ site.baseurl }}/images/icon-ellipses.png){: .inline} and select **Remapping** on the upper-right-hand side of the page.
   ![Remap a connection]({{ site.baseurl }}/images/gbq-remapping.png "Remap a connection")

5. Click **Download** to download the source mapping file.

   !["Download the source mapping file"]({{ site.baseurl }}/images/gbq-downloadyaml.png "Download the source mapping file")

6. Edit the file, as required, and save it.

   ![Edit the yaml file]({{ site.baseurl }}/images/gbq-yaml.png "Edit the yaml file")

7. Finally, click **Browse your files**, and upload your edited mapping file to update the mapping of your connection.

{: id="delete-table"}
## Deleting a table from a BigQuery connection
ThoughtSpot checks for dependencies whenever you try to remove a table in a connection. ThoughtSpot shows a list of dependent objects, and you can click them to delete them or remove the dependency. Then you can remove the table.

To delete a table, follow these steps:

1. Click **Data** in the top navigation bar.

2. Click the **Connections** tab at the top of the page.

3. Click the name of the connection that contains the table you want to delete.

   ![Select a connection]({{ site.baseurl }}/images/gbq-chooseconnection.png "Select a connection")

4. Find the table you want to delete in the list, and check the box next to its name.

5. Click **Delete**, and then click **Delete** again to confirm.

   ![Delete a connection table]({{ site.baseurl }}/images/gbq-deletetable.png "Delete a connection table")

   If you attempt to delete a table with dependent objects, the operation is blocked. A *Cannot delete* window appears, with a list of links to dependent objects. See [Deleting a table with dependent objects]({{ site.baseurl }}/data-integrate/embrace/embrace-gbq-modify.html#deleting-a-table-with-dependent-objects).

{: id="delete-table-deependencies"}
## Deleting a table with dependent objects

In the *Cannot delete* window, click the link for each object to modify or delete it.

  When all dependencies are removed, you can delete the table.

  ![]({{ site.baseurl }}/images/gbq-demoremapping.png "Dependent objects warning")

You can also click the name of a table and then click the linked objects to see a list of dependent objects with links. The list shows the names of the dependent objects (worksheets, pinboards or answers), and the columns they use from that table. You can use this information to determine the impact of changing the structure of the data source or to see how widely used it is. Click a dependent object to modify or delete it.

{: id="delete-connection"}
## Deleting a BigQuery connection
A connection can be used in multiple data sources or visualizations. Because of this, you must delete all of the sources and tasks that use that connection, before you can delete the connection.

To delete a connection, follow these steps:

1. Click **Data** in the top navigation bar.

2. Click the **Connections** tab at the top of the page.

3. Check the box next to the connection you want to delete.

4. Click **Delete**, and then click **Delete** again to confirm.

   ![Delete a connection]({{ site.baseurl }}/images/gbq-deleteconnection.png "Delete a connection")

   If you attempt to delete a connection with dependent objects, the operation is blocked, and a "Cannot delete" warning appears with a list of dependent objects with links.

   ![]({{ site.baseurl }}/images/connection-delete-warning.png "warning connection type")

5. If the "Cannot delete" warning appears, click the link for each object to delete it, and then click **Ok**. Otherwise, go to the next step.

6. When all its dependencies are removed, delete the connection by clicking **Delete**, and then click **Delete** again to confirm.
