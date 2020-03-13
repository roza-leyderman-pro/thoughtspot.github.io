---
title: [Add a Snowflake connection]
last_updated: 2/28/2020
toc: false
sidebar: mydoc_sidebar
permalink: /:collection/:path.html
---
Once ThoughtSpot Embrace is enabled, you can add a connection to a Snowflake database. This allows you to perform a live query of the external database to create answers and pinboards, without having to bring the data into ThoughtSpot.

To add a new connection to Snowflake:

1. Click **Data** in the top navigation bar.

2. Click the **Connections** tab at the top of the page, and click **+ Add connection** at the upper-right-hand side of the page.

     ![]({{ site.baseurl }}/images/new-connection.png "New db connect")

3. Create a name for your connection ([Connection name]({{ site.baseurl }}/data-integrate/embrace/embrace-snowflake-reference.html#connecion_name)), an optional [Connection description]({{ site.baseurl }}/data-integrate/embrace/embrace-snowflake-reference.html#connection_description), then select the Snowflake connection type, and click **Continue**.

     ![Add a Snowflake connection]({{ site.baseurl }}/images/snowflake-connectiontype.png "Add a Snowflake connection")

4. Enter the connection details for your Snowflake data source: [Account name]({{ site.baseurl }}/data-integrate/embrace/embrace-snowflake-reference.html#account_name), [User]({{ site.baseurl }}/data-integrate/embrace/embrace-snowflake-reference.html#user), [Password]({{ site.baseurl }}/data-integrate/embrace/embrace-snowflake-reference.html#password), [Role]({{ site.baseurl }}/data-integrate/embrace/embrace-snowflake-reference.html#role), [Warehouse]({{ site.baseurl }}/data-integrate/embrace/embrace-snowflake-reference.html#warehouse), [Database]({{ site.baseurl }}/data-integrate/embrace/embrace-snowflake-reference.html#database), and [Schema]({{ site.baseurl }}/data-integrate/embrace/embrace-snowflake-reference.html#schema).

   Click **Continue**.

    ![Enter connection details]({{ site.baseurl }}/images/snowflake-connectiondetails.png "Enter connection details")

    Refer to the [Snowflake connection reference]({{ site.baseurl }}/data-integrate/embrace/embrace-snowflake-reference.html#) for more information on each of the specific attributes you must enter for your connection.

5. Select tables (on the left) and the columns from each table (on the right), and then click **Create connection**.

    ![Select tables and columns for your connection]({{ site.baseurl }}/images/snowflake-selecttables.png "Select tables and columns for your connection")

   After you add the connection, you can immediately search your Snowflake database by clicking **Search now**.

   ![The "Connection created" screen]({{ site.baseurl }}/images/snowflake-connectioncreated.png "The "Connection created" screen")


   Your new connection appears on the **Data** > **Connections** page. You can click the name of your connection to view the tables and columns in your connection.   

The connection you just created is a link to the external data source. If there are any joins in the selected tables of the external data source, they are imported into ThoughtSpot.

You can now perform a live query on the selected tables and columns of your connection. Because the selected tables and columns in your connection are linked, it may take a while to initially render the search results. This is because ThoughtSpot does not cache linked data. With linked data, ThoughtSpot queries the external database directly, which is slower than querying data that is stored in ThoughtSpot's database.

## Related information
- [Modify a Snowflake connection]({{ site.baseurl }}/data-integrate/embrace/embrace-snowflake-modify.html)
- [Snowflake connection reference]({{ site.baseurl }}/data-integrate/embrace/embrace-snowflake-reference.html)
- [Load and manage data]({{ site.baseurl }}/admin/loading/loading-intro.html)
- [Data and object security]({{ site.baseurl }}/admin/architecture/security.html)
