# Enable alerts in the virtual network

## Lab scenario

We can use **alerts** from the monitoring section, when you want to get a notification when someone modify any resource in the azure. 

## Objective

In this we will learn about how to add condition based alert and action group required for the virtual network

## Instruction

- You should have virtual network created in the azure
- Go to virtual network, under **Monitoring** section click on **Alerts**

<img src="Images/Virtual Network - Add alert/VNet alert page.png">

- From the **Alerts** page click on **+ New alert rule**. New window will appear for creating alert rule. 

<img src="Images/Virtual Network - Add alert/Create alert rule 1.png">

<img src="Images/Virtual Network - Add alert/Create alert rule 2.png">

- From the **Create rule** window click on **Add condition**, the alert will be based on this condition
- You can select the **signal name** as per your requirement. Here we have selected *Create or Update virtual network*

<img src="Images/Virtual Network - Add alert/Select a signal.png">

- You will see the signal logic once you select the specific signal name. After that click on **Done**.
  
<img src="Images/Virtual Network - Add alert/Configure signal logic.png">

- Now you have added condition for the alert, but the necessary **action group** is also required. 
- The action group will contain the information about the users who will receive the notification of alert and also required action for the alert
- From the **alert rule page** click on *Add action groups*. And then click on **+ Create action group**

<img src="Images/Virtual Network - Add alert/Add action group.png">

- Provide the details on the **basics** tab:

| Setting | Value |
| -- | -- |
| Resource group | **VNet-demo** |
| Action group name | **VNet- alerts** |

<img src="Images/Virtual Network - Add alert/Create action group basic.png">

-In the **notifications** tab, select *Email/SMS message/Push/Voice* in the Notification type.

<img src="Images/Virtual Network - Add alert/Create action group notification.png">

- After selecting notification type, new pane will appear
- Enter the *Email* and *Phone number* of the user who will recieve the notification
> Note: You can specify one email address per notification. To add another email address, add another notification.

<img src="Images/Virtual Network - Add alert/Email or SMS.png">

- Click **Ok** after adding Email and Phone number.

<img src="Images/Virtual Network - Add alert/Create action group notification 2.png">

- If you want to add some action when the alert is fired you can add in the *Actions* tab.

<img src="Images/Virtual Network - Add alert/Create action group actions.png">

- Once you finish with all the setting, give the name for the **Alert** in Alert rule name and click on **Create alert rule**

<img src="Images/Virtual Network - Add alert/Create alert rule final.png">

- You have prvided the email address in the notification tab, so the email will be sent to that email address after the alert is fired.

<img src="Images/Virtual Network - Add alert/Email alert activated 1.png">

<img src="Images/Virtual Network - Add alert/Email alert activated 2.png">

- Go back to the **Alerts** page under **Monitoring** section in virtual network
- You should see all the alerts on that page with the *Severity* associated with that.
> Note: It will take few minutes for alerts to appear on the screen

<img src="Images/Virtual Network - Add alert/Alert page with alerts.png">

- Click on *Total alerts* on that page, the list of alerts will be present on the page.

<img src="Images/Virtual Network - Add alert/All alerts.png">

- If you want to see detailed information about specific alert, click on that specific alert. New window will appear.

<img src="Images/Virtual Network - Add alert/Change alert state.png">

- Now that you have received all the information regarding alert, you can solve that alert and change it's state to any of the given options. Click on *Save* after changing the state of the alert

<img src="Images/Virtual Network - Add alert/Select a alert state.png">

- After that you can see the changed state of the specific alert in the alerts page

<img src="Images/Virtual Network - Add alert/Closed and acknowledge alerts.png">


