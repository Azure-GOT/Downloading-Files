## Step: Add the alerts 

The users should get notification when some conditions met like when there is a resource which is not properly utilized for last some days, the cost can be reduced for such resouces.

- When writing the log queries there is an option for the **+ New alert rule** in the top menu. This will be based on that specific query.
- Click on that, the condition should be already there define the logic in that condition
- Now click on the **Add action group**, in that we can add the email address or SMS for the required user which will be notified 
- The steps are shown below:

- Click on the condition so that you can define the logic behind that condition

<img src="Images/Create alert rule 1.png">

- After Defining the logic click on **Done**

- This condition will trigger the alert when the average CPU utilization is more than 90%
- In the query we have defined the average CPU utilization, when the threshold value will become greater than 90 the alert will fired
<img src="Images/Alert-CPU-90.png">


<img src="Images/Alert-CPU-90-02.png">
<img src="Images/Alert-CPU-90-03.png">

- This condition will trigger the alert when the average CPU utilization is less than 10% in last 2 days
- In the query we have defined the average CPU utilization, when the threshold value will become less than 10 the alert will fired
<img src="Images/Alert-CPU-10.png">
<img src="Images/Alert-CPU-10-02.png">
<img src="Images/Alert-CPU-10-03.png">

- An action group is a collection of notification preferences defined in the Azure. To add the action group click on **Add action group**
<img src="Images/Add action group.png">

- Provide the basic details on the **Basics** tab
<img src="Images/Basic-tab-action-group.jpg">

- On the notification tab, select the notification type as **Email/SMS message/Push/Voice**
<img src="Images/Notification-tab-action-group.png">

- Enter the **Email** and **Phone number** of the user who you want to receive the notification when the alert is fired
> Note: You have to enter the valid Email and Phone number
<img src="Images/Email-SMS-action-group.png">

- When the alert is fired, it should perform some action. We can define those action type on the **Actions** tab
<img src="Images/Actions-tab-action-group.png">

- Click on **Review and create** and wait for the deployment to complete.

---

- Now the **Alert rule** has been added. In some scenario during planned maintenance, you want to suppress the notifications of the alert. Here we can use **Action rule**

- Go to the **Alerts** page on **Monitor** and click on **Action rules**. After that select **+ Create**
<img src="Images/Create action rules.png">

- New window will appear. Select the **Scope** on which you want to apply the action rule. You can select the **Suppression** or **Action group**
<img src="Images/Create action rule 2.png">

- You can select for what time range the alert should suppressed. There are options like *At scheduled time* or *With a recurrence*
<img src="Images/Configure suppresion.png">
<img src="Images/Configure suppresion 2.png">

- After configuring all the details **Create**
<img src="Images/Create action rule final.png">
