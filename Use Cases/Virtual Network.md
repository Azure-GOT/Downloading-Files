# Address space in virtual network

### Lab scenerio

Suppose you want to add the address spaces in the virtual network according to customer request, we can do that from the **Address space** blade under **Settings** section.

## Objective

In this we will learn about 
- Create and configure virtual network
- How to add additional address spaces in the virtual network

## Instructions

1. Create and configure **virtual network**

- Create the virtual network with the following setting ( Leave other as default):

| Setting | Value |
| -- | -- |
| Subscription | Select your active subscription |
| Resource Group | **VNet-demo** |
| Name | **VNet-01-demo** |
| Region | **East US** |
| Subnet name | **VNet-01-demo-subnet** |

<img src="Images/Virtual Network/Creating VNet basic.png"> 

<img src="Images/Virtual Network/Creating VNet ip address.png"> 

<img src="Images/Virtual Network/Creating VNet security.png"> 

<img src="Images/Virtual Network/Creating VNet tags.png"> 

<img src="Images/Virtual Network/Creating VNet final validation.png"> 


2. Add **additional address spaces** in the virtual network

When the deployment completes, go to the **virtual network**, under **settings** section click on **Address space**. You will see the default address space here.

<img src="Images/Virtual Network/VNet address spaces.png"> 

According to the requirement, we can add additional address space, after adding click on save it will be reflected in the virtual network.

>Note: The subnets should belong to these address ranges only

<img src="Images/Virtual Network/VNet additional address spaces.png"> 

<img src="Images/Virtual Network/VNet address spaces done.png"> 
 
