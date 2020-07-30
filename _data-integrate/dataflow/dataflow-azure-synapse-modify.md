---
title: [Modify an Azure Synapse connection]
last_updated: 6/17/2020
summary: Learn how to modify a DataFlow Azure Synapse connection and its tables.
sidebar: mydoc_sidebar
permalink: /:collection/:path.html
---

You can modify a DataFlow Azure Synapse connection in the following ways:
- Edit a connection: to add or remove tables and columns
- Remap a connection: to map a table or column to a different table or column
- Delete a table
- Delete a connection

## Editing an Azure Synapse connection

You can edit an Azure Synapse connection to add tables and columns.

To edit a connection:

## Removing a table from an Azure Synapse connection

To remove a table from a connection, delete it from the connection details page. For more information, see <!--[Deleting a table]({{ site.baseurl }}/data-integrate/embrace/embrace-synapse-modify.html#deleting-a-table-from-a-synapse-connection).-->

## Remapping an Azure Synapse connection

Modify the connection parameters by editing the source mapping <code>yaml</code> file that was created when you added the connection. For example, you can remap the existing table or column to a different table or column in an existing database connection. ThoughtSpot recommends that you check the dependencies before and after you remap a table or column in a connection to ensure they display as intended.

To remap a connection:

1.

## Deleting an Azure Synapse connection

A connection can be used in multiple data sources or visualizations. Because of this, you must delete all of the sources and tasks that use that connection, before you can delete the connection.

To delete a connection:
1.