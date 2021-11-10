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
| Action group name | **VNet- alerts* |

<img src="Images/Virtual Network - Add alert/Create action group basic.png">

-In the **notifications** tab, select *Email/SMS message/Push/Voice* in the Notification type.

<img src="Images/Virtual Network - Add alert/Create action group notification.png">

- After selecting notification type, new pane will appear
- Enter the *Email* and *Phone number* of the user who will recieve the notification
> Note: You can specify one email address per notification. To add another email address, add another notification.

<img src="Images/Virtual Network - Add alert/Email or SMS.png">

-Click **Ok** after adding Email and Phone number.
<img src="Images/Virtual Network - Add alert/Create action group notification 2.png">

<img src="Images/Virtual Network - Add alert/Create action group actions.png">

<img src="Images/Virtual Network - Add alert/Create alert rule final.png">

<img src="Images/Virtual Network - Add alert/Email alert activated 1.png">

<img src="Images/Virtual Network - Add alert/Email alert activated 2.png">

<img src="Images/Virtual Network - Add alert/Alert page with alerts.png">

<img src="Images/Virtual Network - Add alert/All alerts.png">

<img src="Images/Virtual Network - Add alert/Change alert state.png">

<img src="Images/Virtual Network - Add alert/Select a alert state.png">

<img src="Images/Virtual Network - Add alert/Closed and acknowledge alerts.png">


