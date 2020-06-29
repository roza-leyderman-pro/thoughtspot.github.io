---
title: [Azure Synapse connections in DataFlow]
last_updated: 6/17/2020
toc: true
sidebar: mydoc_sidebar
permalink: /:collection/:path.html
---
DataFlow enables you to connect to Azure Synapse database, to use your data in ThoughtSpot.

- [Add a connection]({{ site.baseurl }}/data-integrate/dataflow/dataflow-azure-synapse-add.html)
- [Sync data]({{ site.baseurl }}/data-integrate/dataflow/dataflow-azure-synapse-sync.html)
- [Best practices]({{ site.baseurl }}/data-integrate/dataflow/dataflow-azure-synapse-best.html)
- [Reference]({{ site.baseurl }}/data-integrate/dataflow/dataflow-azure-synapse-reference.html)

<!--
1. Click **Data** in the top navigation bar.

2. Click the **Connections** tab at the top of the page, and click **+ Add connection** at the upper-right-hand side of the page.

    ![Click "+ Add connection"]({{ site.baseurl }}/images/redshift-addconnection.png "Click "+ add connection"")
   []({{ site.baseurl }}/images/new-connection.png "New db connect")

3. Create a name for your connection, a description (optional), then select the Synapse connection type, and click **Continue**.

   ![Add a Synapse connection]({{ site.baseurl }}/images/synapse-connectiontype.png "Add a Synapse connection")

4. Enter the connection details for your Synapse data source.

   ![Enter connection details]({{ site.baseurl }}/images/synapse-connectiondetails.png "Enter connection details")

   Refer to the [Synapse connection reference]({{ site.baseurl }}/data-integrate/embrace/embrace-synapse-reference.html#) for more information on each of the specific attributes you must enter for your connection.

5. (Optional) Provide additional key-value pairs that you need to set up your connection to Synapse, by doing the following:
- Click the **Advanced Config** menu to reveal the **Key** and **Value** fields.
- Enter your key and value information.
- To add more keys and values, click the plus sign (+), and enter them.

    {% include note.html content="Any key-value pairs that you enter must be defined in your Synapse data source. Key-value pairs are case-sensitive." %}

6. Click **Continue**.      

7. Select tables (on the left) and the columns from each table (on the right), and then click **Create connection**.

    ![Select tables and columns for your connection]({{ site.baseurl }}/images/snowflake-selecttables.png "Select tables and columns for your connection")
    ![Select tables and columns for your connection]({{ site.baseurl }}/images/synapse-selecttables.png "Select tables and columns for your connection")

   Once the connection is added, you can search your Synapse database right away by clicking **Search now**.

   ![The "Connection created" screen]({{ site.baseurl }}/images/synapse-connectioncreated.png "The "Connection created" screen")

   Your new connection appears on the **Data** > **Connections** page. You can click the name of your connection to view the tables and columns in your connection.   

The connection you just created is a link to the external data source. If there are any joins in the selected tables of the external data source, those are imported into ThoughtSpot.

You can now perform a live query on the selected tables and columns of your connection. Because the selected tables and columns in your connection are linked, it may take a while to initially render the search results. This is because ThoughtSpot does not cache linked data. With linked data, ThoughtSpot queries the external database directly, which is slower than querying data that is stored in ThoughtSpot's database.

## Related information
- [Modify a Synapse connection]({{ site.baseurl }}/data-integrate/embrace/embrace-synapse-modify.html)
- [Synapse connection reference]({{ site.baseurl }}/data-integrate/embrace/embrace-synapse-reference.html)
- [Load and manage data]({{ site.baseurl }}/admin/loading/loading-intro.html)
- [Data and object security]({{ site.baseurl }}/admin/architecture/security.html)

-->