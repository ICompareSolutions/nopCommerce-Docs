---
title: SendinBlue integration
uid: en/running-your-store/promotional-tools/sendinblue-integration
author: git.mariannk
---

# SendinBlue integration

This section describes how to integrate SendinBlue in your store.

## What SendinBlue is

SendinBlue is an all-in-one digital marketing toolbox that's capable of taking care of the entirety of your marketing needs. SendinBlue empowers to build and grow relationships using email campaigns, SMS messages and sophisticated automation of marketing workflows. 

The SendinBlue integration for nopCommerce allows a store owner to:
* design clean and professional newsletters
* build and target the audience
* automate the marketing (e.g. abandoned cart recovery)

## Install and enable the plugin

The SendinBlue plugin is an out-of-the-box nopCommerce plugin. You can find it here: **Configuration → Local plugins**. To find the plugin faster use the **Group** field on the search panel to filter the plugins by *Misc* type:
![Find the plugin](_static/sendinblue-integration/plugin-list.jpg)

Install the plugin using the **Install** button if it is uninstalled. Then enable it by clicking the **Edit** button. You will see the *Edit plugin details* window in this case. Mark the plugin as enabled using the **Is enabled** checkbox and click the **Save** button.

## How to configure the plugin

1. Click the **Configure** button. You will see the *Configure - SendinBlue* window:
![Configure - SendinBlue](_static/sendinblue-integration/configure-window.jpg)

1. You need to create a free SendinBlue account using [this link](https://app.sendinblue.com/account/login/?utm_source=nopcommerce_plugin&utm_medium=plugin&utm_campaign=module_link).

1. Enter your **API v3 key** from your SendinBlue account on [SMTP & API](https://account.sendinblue.com/advanced/api/?utm_source=nopcommerce_plugin&utm_medium=plugin&utm_campaign=module_link) page.

1. Click the **Save** button.

1. Once you have done this you should be able to see your account details.
![After th first save](_static/sendinblue-integration/general-panel.jpg)

1. Go to the **Contacts** panel to synchronize your nopCommerce customers with your SendinBlue account.
![Contacts](_static/sendinblue-integration/contacts-panel.jpg)

* To create a new SendinBlue list, click on the **Create a list** button to be redirected to your SendinBlue account.
* From the drop-down list, select the list where your nopCommerce subscribers as well as their contact data will be added. Click on the **Save** button.

### What data is synced?

The following form fields are synced as contact attributes:
* EMAIL
* FIRSTNAME
* LASTNAME
* SMS
* STORE_ID
* USERNAME
* PHONE
* COUNTRY
* GENDER
* DATE_OF_BIRTH
* COMPANY
* ADDRESS_1
* ADDRESS_2
* ZIP_CODE
* CITY
* COUNTY
* STATE
* FAX

> [!NOTE]
>
> For the sync, note that these form fields need to be enabled for customers. Go to **Configuration → Settings → Customer settings → Customer form fields**.

Order data is synced as transactional attributes:
* ORDER_ID: ID of the order
* ORDER_PRICE: amount of the order
* ORDER_DATE: date of the order

> [!NOTE]
>
> Orders are synchronized when the order's payment status is paid.

### How often are contacts synced?

After the initial sync, a task is scheduled to run every 6000 seconds to automatically add your new subscribers to your SendinBlue list.

Click on the **Sync now** button to sync right away.

To change the sync frequency, go to **System → Schedule tasks**.
![Schedule tasks](_static/sendinblue-integration/configure-task.jpg)

## Sending transactional emails

Go to the **Transactional emails** panel to send your transactional emails via SendinBlue SMTP.
![Sending transactional emails](_static/sendinblue-integration/email-panel.jpg)

1. Check the **Use SendinBlue SMTP** checkbox.
1. Paste your SMTP password that can be found [here](https://account.sendinblue.com/advanced/api).
1. From the drop-down list, select the sender you wish to send your emails from.
1. Click on the **Save** button.

You should then be able to see the email notification list. This lists all of the transactional emails (order confirmation, etc.) that you send.
![Notification list](_static/sendinblue-integration/email-list.jpg)

For each template, you can:
* Choose if it is active or inactive.
* Choose between the default nopCommerce template or a SendinBlue template. To do this:
	1. Click on the **Edit** button
	1. From the dropdown, choose your template
	1. Click **Update**
* Edit its content.

> [!NOTE]
>
> If you *have checked* **SendinBlue email template**, then click on **Edit template** to edit the content of your template on your SendinBlue account. 
If you *haven't checked* **SendinBlue email template**, then clicking on **Edit template** will redirect you to the message templage edit page in the nopCommerce admin area. Read more about the message template editing process [here](xref:en/running-your-store/content-management/message-templates). You can also send a test email from that page to check the content. Note that an email credit will be used for each test email.

## Sending SMS

Go to the **SMS** panel to send SMS notifications to your customers in addition to emails.
![Sms panel](_static/sendinblue-integration/sms-panel.jpg)

1. Check the **Use SMS notifications** checkbox.
1. Enter an alphanumerical sender (maximum of 11 characters).
1. Type your telephone number.
1. Click on the **Save** button.

To send an SMS campaign to a SendinBlue list:
![Sms panel](_static/sendinblue-integration/sma-campaigns.jpg)

1. Go to the **SMS campaigns** block.
1. Choose **List** of contacts to send SMS campaign.
1. Input the name of the sender to the **Send SMS campaign from** field. The number of characters is limited to 11 (alphanumeric format).
1. Specify SMS campaign content using the **Text** field. The number of characters is limited to 160 for one message.
1. Click **Save campaign**.

The plugin is now configured. You can access all of your transactional email stats directly from SendinBlue.

## Setting up Marketing Automation workflows

> [!NOTE]
>
> A customer has to be identified by their email address to trigger a workflow i.e. a customer who has logged into their account on the nopCommerce store or input their email address during checkout.

Go to the **Marketing Automation** panel to install the marketing automation tracking script to track the activity of shoppers on your store. You will be able to automate your marketing by sending a series of emails or SMS once a visitor has signed up, a prospect has abandoned their cart, a customer has made a purchase, etc.
![Marketing automation](_static/sendinblue-integration/marketing-automation.jpg)

1. Check the **Use Marketing Automation** checkbox.
1. If the *Marketing Automation platform* is enabled on your SendinBlue account, then the plugin will auto-fill your **Tracker ID**.
1. Paste the tracking script generated by SendinBlue to the **Tracking script** field. {TRACKING_ID} and {CUSTOMER_EMAIL} will be dynamically replaced.
1. Make sure that the SendinBlue widget is activated on the **Configuration → Widgets** page.
1. Click the **Save** button.

Once Marketing Automation is enabled and functioning properly, you will find the following logs in your SendinBlue account under *Automation → Logs → Event logs*:

* Page
* Identify
* Track events

The plugin will automatically track the activity of shoppers for you to set up workflows to recover lost sales and order confirmation workflows. 3 track events are passed:

* cart_updated is passed when an item is added to a cart.
* cart_deleted is passed when a cart is emptied.
* order_completed is passed when the order has been made. This means that the payment status is "Paid".
![Logs](_static/sendinblue-integration/logs.png)

## Learn more

* Learn how to [create an abandoned cart email for nopCommerce customers](https://help.sendinblue.com/hc/en-us/articles/360004172899).
* Learn how to [create an order confirmation email for nopCommerce customers](https://help.sendinblue.com/hc/en-us/articles/360004172939).
