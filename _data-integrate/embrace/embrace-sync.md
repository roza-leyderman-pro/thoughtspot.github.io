---
title: [Sync Tables in Embrace]
last_updated: tbd
toc: true
sidebar: mydoc_sidebar
permalink: /:collection/:path.html
---
When you create a connection to Snowflake, the selected tables and columns in your connection are linked to the Snowflake database. With linked data, ThoughtSpot queries the Snowflake database directly, which is convenient because you don't have to import the data into ThoughtSpot, but search is slower and you don't have access to all of ThoughtSpot's features. With Sync, you get the search performance and all the features available of ThoughtSpot.

## How sync works

Sync copies selected tables or columns into ThoughtSpot. By syncing your tables and columns, your data is indexed, which improves search speed. You can sync manually at any time, and also schedule your sync.

### Syncing manually

You can manually sync one or more tables in a connection.

To sync manually:

1. Click **Data** in the top navigation bar.

2. Click the **Connections** tab at the top of the page.

3. Click the name of your connection.

    ![]({{ site.baseurl }}/images/select-connection.png "Select a connection")

4. Check the box next one or more tables that you want to sync, and click **Sync Now**.

    ![]({{ site.baseurl }}/images/sync.png "Table sync")

The status of the sync appears in the _Last synced_ column and refreshes to indicate when the sync was completed.

### Scheduling sync

To schedule sync:

1. Click **Data** in the top navigation bar.

2. Click the **Connections** tab at the top of the page.

3. Click the name of your connection that contains the table you want to sync.

4. Click the name of the table you want to sync.

4. Click the **Sync** tab.

5. Click **Schedule**.

6. In the *Sync table schedule* window, use the **Select interval** drop-down menu to set the following items:  
    A. How often you want to sync (**Hourly**, **Daily**, **Weekly**, or **Monthly**).  
    B. Select a sync mode:
    - **Append** adds to the current data.
    - **Overwrite** replaces the current data.  
7. (Optional) Enter a filter condition to be added to the search query.

8. (Optional) If you want to shard the data as it is synced, click **Show advanced settings** and enter the **Primary key**, **Sharding key** and **Number of shards**.

9. Click **Schedule**

   The schedule is saved and runs automatically at the selected time.  
   Every time the schedule is run, it is listed in the History list.

#### Updating or removing a schedule

To update a schedule:

1. From the sync tab of the table you want to update, click **Schedule**.

2. In the *Sync table schedule* window, make your changes and click **Update schedule**.

To remove a schedule:

- From the sync tab of the table you want to update, click the More Info icon ![more options menu icon]({{ site.baseurl }}/images/icon-ellipses.png){: .inline} and select **Delete schedule**.


## Related information
- [Modify a connection]({{ site.baseurl }}/data-integrate/embrace/getting-started/modify-a-connection.html)
- [Connectors reference]({{ site.baseurl }}/data-integrate/embrace/reference/embrace-connection-credentials.html)
- [Load and manage data]({{ site.baseurl }}/admin/loading/loading-intro.html)
- [Data and object security]({{ site.baseurl }}/admin/architecture/security.html)