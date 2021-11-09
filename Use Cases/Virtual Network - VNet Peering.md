# Create VNet peering between two virtual networks

## Lab scenario

We can use VNet Peering between two virtual networks when we want to route traffic between them privately through IPv4 addresses. The virtual machines in the peered network uses Microsoft backbone infrastructure for communication.

<img src="Images/Virtual Network/Virtual Network Peering diagram.png">

## Objective

Here we will learn how to add peering between two virtual networks

# Instruction

- You should have two virtual netwoks created in azure for VNet peering

> Note: If the virtual networks are in different regions, the VNet peering will work.

- Go to any one of the virtual network, under **Settings** click on **Peering**
- The existing peering should be available there, if there is not any click on **+ Add**
  <img src="Images/Virtual Network/Virtual network VNet peering.png">
  
- The **Add peering** pane will appear. Add the required details such as(leave the rest as default):

  | Setting | Value |
  | -- | -- |
  | Peering Link Name | **VNet-01-demo-to-VNet-01-demo-02** |

  <img src="Images/Virtual Network/Virtual network Add peering 1.png">

- For **Remote Virtual Network** add the following details(leave the rest as default):

  | Setting | Value |
  | -- | -- |
  | Peering Link Name | **VNet-01-demo-02-to-VNet-01-demo** |
  | Subscription | Your Active Azure Subscription |
  | Virtual network | The other virtual network |
  
  <img src="Images/Virtual Network/Virtual network Add peering 2.png">
  
- After that click on **Add**, it should create the peering between them. Peering status will be **Connected** after a few minutes

  <img src="Images/Virtual Network/Virtual network Peering status connected 1.png">

  <img src="Images/Virtual Network/Virtual network Peering status connected 2.png">
