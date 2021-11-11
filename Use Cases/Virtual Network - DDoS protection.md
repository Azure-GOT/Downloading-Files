# Enable the DDoS protection for the virtual network

## Lab scenario

DDoS(Distributed denial of service) attacks can be targeted at any endpoint that is publicly reachable through the internet. So it can make the application unavailable to users. We can reduced this by enabling the DDoS protection 

## Objective

In this we will learn about how we can enable DDoS protection for the virtual network

## Instruction

- You should have virtual network created in the azure
- Go to virtual network, under **Settings** section click on **DDoS protection**

<img src="Images/Virtual Network - DDoS protection/VNet DDoS protection.png">

- If you see the status of *DDoS Protection Standard* as **Disable**, select **Enable**

<img src="Images/Virtual Network - DDoS protection/VNet DDoS protection enable.png">

- You can select you existing DDoS protection plan if you have one, otherwise click on **Create a DDoS protection plan**
- The new window will open for creating DDoS protection plan.
- Provide the basic details:

| Setting | Value |
| -- | -- |
| Resource group | **VNet-demo** |
| Name | **VNet-DDoS-Protection** |
| Region | **East US** |

<img src="Images/Virtual Network - DDoS protection/Create DDoS protection.png">

- After providing details click on **Review + create** and if validation passed click on **Create**

<img src="Images/Virtual Network - DDoS protection/DDoD protection created.png">

- You can see the newly created DDoS protection plan in the virtual network page.

<img src="Images/Virtual Network - DDoS protection/VNet DDoS protection selected.png">

- Navigate to the **DDoS protection** resource that you created. Under **Settings** section click on **Protected resource**. The virtual network will be there

<img src="Images/Virtual Network - DDoS protection/Enabled DDoS protection for VNet.png">
