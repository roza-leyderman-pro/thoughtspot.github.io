---
title: [Sync data through an Amazon Aurora connection]
last_updated: 7/03/2020
toc: true
sidebar: mydoc_sidebar
permalink: /:collection/:path.html
---
After using ThoughtSpot DataFlow to establish a connection to an Amazon Aurora database, you can create automatic data updates, to seamlessly refresh your data.

{% include content/dataflow/sync-for-databases.md %}

4. Specify the sync properties for Amazon Aurora:

   <details>
        <summary>See the <strong>Connection-specific sync properties</strong> screen</summary>
     <p>
     <img src="../../images/dataflow-set-sync-properties-draft.png" alt="Enter sync details" /></p>
   </details>

   <!--![Enter connection details]({{ site.baseurl }}/images/dataflow-cassandra-create.png "Enter connection details")-->

   * [Column delimiter]({{ site.baseurl }}/data-integrate/dataflow/dataflow-amazon-aurora-reference.html#dataflow-amazon-aurora-sync-column-delimiter)<br/>Specify the column delimiter character.
   * [Enclosing character]({{ site.baseurl }}/data-integrate/dataflow/dataflow-amazon-aurora-reference.html#dataflow-amazon-aurora-sync-enclosing-character)<br/>Specify if the text columns in the source data needs to be enclosed in quotes.
   * [Escape character]({{ site.baseurl }}/data-integrate/dataflow/dataflow-amazon-aurora-reference.html#dataflow-amazon-aurora-sync-escape-character)<br/>Specify the escape character if using a text qualifier in the source data.
   * [Fetch size]({{ site.baseurl }}/data-integrate/dataflow/dataflow-amazon-aurora-reference.html#dataflow-amazon-aurora-sync-fetch-size)<br/>Specify the number of rows to be fetched at a time and processed in memory. If the value specified is zero then, all rows are extracted at once.
   * [TS load options]({{ site.baseurl }}/data-integrate/dataflow/dataflow-amazon-aurora-reference.html#dataflow-amazon-aurora-sync-ts-load-options)<br/>Specify the parameters passed with the <code>tsload</code> command, in addition to the commands already included by the application.

   See [Sync properties]({{ site.baseurl }}/data-integrate/dataflow/dataflow-amazon-aurora-reference.html#sync-properties) for details, defaults, and examples.

5. Save your work by clicking **Save**.<br/>Alternatively, click **Save and sync now** to save your work and sync data at the same time.