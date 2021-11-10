# Create service endpoint in virtual network

## Lab scenario

Suppose we want to limit the Azure service to the allowed virtual networks and subnets only so we can use the service endpoint for this kind of security.
The traffic using service endpoints flows over Microsoft backbone providing additional layer of security.

## Objective

In this we will learn how to add service endpoint in virtual network and add that subnet to storage account.

## Instruction

- Navigate to the **virtual network**
- Under **Settings** section, click on **Service endpoints**. The page will be blank if there are no service endpoints are created.

<img src="Images/Virtual Network/Virtual Network service endpoint.png">

- Click on **+ Add** for creating new service endpoint for the virtual network.
- The new **Add service endpoint** pane will appear. Provide the details and click on **Add**

> Note: There are around 10 different services that you can choose according to your need. Here we have demonstrate storage service.
  
<img src="Images/Virtual Network/Add service endpoint pane.png">
  
- After clicking on Add the service endpoint should appear on the page with the associated subnet. 

<img src="Images/Virtual Network/Virtual network service endpoint page.png">

### Add this service endpoint to the Azure service

Here we will restrict the storage account access only to the subnet that has service endpoint associated.

> Note: We need storage account here, so if you don't have one first create it.

- Go to your created storage account
- Under **Security + networking** section, click on **Networking**

<img src="Images/Virtual Network/Storage account networking tab.png">

- From that click on **Selected networks**.
- After that click on **+ Add existing virtual network**(if you already have created virtual network)
- The new **Add networks** pane will appear

<img src="Images/Virtual Network/Storage account add network empty.png">

- Provide the details of virtual network and subnet as shown below

> Note: You can enable the service endpoint for specific subnet from here as well. Just select the subnet and click on enable

<img src="Images/Virtual Network/Storage account add network.png">

- The subnet from the virtual network should now able to access the storage account
  
<img src="Images/Virtual Network/Storage account final.png">
