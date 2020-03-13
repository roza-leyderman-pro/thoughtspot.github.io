---
title: [Add a Redshift connection]
last_updated: 02/28/2020
toc: false
sidebar: mydoc_sidebar
permalink: /:collection/:path.html
---
Once ThoughtSpot Embrace is enabled, you can add a connection to a Redshift database. This allows you to perform a live query of the external database to create answers and pinboards, without having to bring the data into ThoughtSpot.

To add a new connection to Redshift:

1. Click **Data** in the top navigation bar.

2. Click the **Connections** tab at the top of the page, and click **+ Add connection** at the upper-right-hand side of the page.

    ![Click "+ Add connection"]({{ site.baseurl }}/images/redshift-addconnection.png "Click "+ add connection"")
     <!-- ![]({{ site.baseurl }}/images/new-connection.png "New db connect") -->
3. Create a name for your connection ([Connection name]({{ site.baseurl }}/data-integrate/embrace/embrace-redshift-reference.html#connecion_name)), an optional [Connection description]({{ site.baseurl }}/data-integrate/embrace/embrace-redshift-reference.html#connection_description), and then select the Redshift connection type, and click **Continue**.

    ![Choose connection type]({{ site.baseurl }}/images/redshift-choosetype.png "Choose connection type")
     <!-- ![]({{ site.baseurl }}/images/select-new-connection.png "Select a new connection type") -->
4. Enter the connection details for your external data source: [Host]({{ site.baseurl }}/data-integrate/embrace/embrace-redshift-reference.html#host), [Port]({{ site.baseurl }}/data-integrate/embrace/embrace-redshift-reference.html#port), [User]({{ site.baseurl }}/data-integrate/embrace/embrace-redshift-reference.html#user), [Password]({{ site.baseurl }}/data-integrate/embrace/embrace-redshift-reference.html#password), and [Database]({{ site.baseurl }}/data-integrate/embrace/embrace-redshift-reference.html#database).

    Click **Continue**.

    ![Enter connection details]({{ site.baseurl }}/images/redshift-connectiondetails.png "Enter connection details")
     <!-- ![]({{ site.baseurl }}/images/new-connection-creds.png "Select a connection type") -->

     Refer to the [Redshift connection reference]({{ site.baseurl }}/data-integrate/embrace/embrace-redshift-reference.html#) for more information on each of the specific attributes you must enter for your connection.

5. Select tables (on the left) and the columns from each table (on the right), and then click **Create connection**.

     ![Select tables and columns]({{ site.baseurl }}/images/snowflake-selecttables.png "Select tables and columns")

   After you add the connection, you can immediately search your Redshift database by clicking **Search now**.

   ![The "connection created" screen]({{ site.baseurl }}/images/redshift-connectioncreated.png "The "connection created" screen")

   Your new connection appears on the **Data** > **Connections** page. You can click the name of your connection to view the tables and columns in your connection.   

The connection you just created is a link to the external data source. If there are any joins in the selected tables of the external data source, those are imported into ThoughtSpot.

You can now perform a live query on the selected tables and columns of your connection. Because the selected tables and columns in your connection are linked, it may take a while to initially render the search results. This is because ThoughtSpot does not cache linked data. With linked data, ThoughtSpot queries the external database directly, which is slower than querying data that is stored in ThoughtSpot's database.

## Related information
- [Modify a Redshift connection]({{ site.baseurl }}/data-integrate/embrace/embrace-redshift-modify.html)
- [Redshift connection reference]({{ site.baseurl }}/data-integrate/embrace/embrace-redshift-reference.html)
- [Load and manage data]({{ site.baseurl }}/admin/loading/loading-intro.html)
- [Data and object security]({{ site.baseurl }}/admin/architecture/security.html)
