# Enable Diagnostic settings for virtual network

## Lab scenario

## Objective

## Instruction

- You should have virtual network created in the azure
- Go to virtual network, under **Monitoring** section click on **Diagnostic settings**

<img src="Images/Virtual Network - Diagnostic setting/1 Diagnostic settings.png">

- If there is Diagnostic settings already exist, it is displayed here.
- For adding another Diagnostic settings or creating new click on **+ Add diagnostic settings**
- The new Diagnostic settings window will open

<img src="Images/Virtual Network - Diagnostic setting/2 Adding diagnostic setting.png">

- Add the required details as shown and click on **Save**

<img src="Images/Virtual Network - Diagnostic setting/3 Adding diagnostic setting.png">

- After adding, the new Diagnostic settings will appear on the page

<img src="Images/Virtual Network - Diagnostic setting/4 Diagnostic setting page.png">

- If you wish to add the Diagnostic settings from activity log click on **Activity log** and from that click on **Diagnostic settings**

<img src="Images/Virtual Network - Diagnostic setting/5 Diagnostic setting from activity log.png">

- Provide the required details as shown and click on **Save**

<img src="Images/Virtual Network - Diagnostic setting/6 Diagnostic setting from activity log page.png">

- New Diagnostic settings will appear on the page

<img src="Images/Virtual Network - Diagnostic setting/7 Diagnostic setting activity log done.png">

- All the activity log will be stored in the storage account because we selected storage account as destination
- Go to that specific storage account, and click on **Container** under **Date storage** section

<img src="Images/Virtual Network - Diagnostic setting/8 Container.png">

- Click on the *insights-activity-log* container and nagivate to the last folder where you will find the *PT1H.json* file

<img src="Images/Virtual Network - Diagnostic setting/9 File in container.png">

- You can download the file by clicking on it and then click on *Download*.

<img src="Images/Virtual Network - Diagnostic setting/10 File download.png">
