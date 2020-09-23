You can use the Data Push API and a custom menu item to initiate an action in another application based on the result of a search in ThoughtSpot.

These custom menu items are visible when you select the more options menu ![]({{ site.baseurl }}/images/icon-more-10px.png){: .inline} on an Answer, or during a search, if you use the search terms that the external application expects to receive.

## About the Data Push API
The Data Push API allows you to open a web page in the context of the ThoughtSpot application. This third party web page then has access to the ThoughtSpot search from which it was invoked. This is useful when you want to initiate an action in another application based on the result of a search in ThoughtSpot.

For example, you may search in ThoughtSpot for customers who are coming due for renewal of their contract in the next month. You could then trigger an action that brings up a web page from an external billing system. The billing system could be set up to read the data (list of names, emails, products, and renewal dates) from ThoughtSpot. The billing system might then add the price, generate an invoice for each customer, and send it by email.

To turn on the Data Push API functionality, [contact ThoughtSpot Support]({{ site.baseurl}}/admin/misc/contact.html).

The data is available to the external application in JSON (JavaScript Object Notation) format. You must parse the JSON to get the data values you need using JavaScript in the receiving application.

## Create a custom menu item from the Administration Portal
To add custom items to the more options menu ![]({{ site.baseurl }}/images/icon-more-10px.png){: .inline} for Answers, navigate to the Administration Portal by clicking on the **Admin** tab from the top navigation bar. Select **Action Customization** from the side navigation bar that appears.

![Admin Portal - Action customization]({{ site.baseurl }}/images/admin-portal-action-customization.png "Admin Portal - Action customization")

Select **Add custom action item**.

![Add a custom menu item]({{ site.baseurl }}/images/admin-portal-action-customization-edit.png "Add a custom menu item")

Specify a label for the item, such as *billing renewal email*, and add the URL of the external application. Choose the size of the window you would like to open up in ThoughtSpot when a user clicks on this action, and click **Confirm**.

You can now see your action on ThoughtSpot searches and Answers, if you use the search terms that the external application expects to receive. Your action has a **custom** tag to differentiate it from ThoughtSpot actions.

When a user clicks on your action, the application you specified appears, and completes the actions specified by the Data Push API.

{% include note.html content="In order for your action to work correctly, you <strong><em>must</em></strong> use the search terms that the external application expects to receive in your Answer or unsaved ThoughtSpot search." %}