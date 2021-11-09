# Virtual Network - Adding subnets

## Lab scenario

When there is a requirement for different sub-network for the each department in the organization, so we can divide the virtual network into multiple subnets for different department and security.

> Note: The address range of one subnet should not overlap into address range of another subnet.

## Objective

In this we will learn about

- How to add multiple subnets in virtual network

## Instruction

- You should have virtual network created in the azure portal
- Go to virtual network, under **settings** section click on **Subnets**

  <img src="Images/Virtual Network/Virtual network subnet.png">
  
- One default subnet should be present in the subnet page. For adding another subnets click on **+ Subnet**. The **Add subnet** pane will appear
- Enter the follwing details:( Leave the rest as default)

| Setting | Value |
| -- | -- |
| Name | **VNet-01-demo-subnet-02** |
| Subnet address range | **10.0.1.0/24** |

<img src="Images/Virtual Network/Virtual network subnet 2.png">
  
- For adding another subnets again click on **+ Subnet**. The **Add subnet** pane will appear
- Enter the follwing details:( Leave the rest as default)

| Setting | Value |
| -- | -- |
| Name | **VNet-01-demo-subnet-03** |
| Subnet address range | **10.1.0.0/29** |

<img src="Images/Virtual Network/Virtual network subnet 3.png">

- For adding another subnets again click on **+ Subnet**. The **Add subnet** pane will appear
- Enter the follwing details:( Leave the rest as default)

| Setting | Value |
| -- | -- |
| Name | **VNet-01-demo-subnet-04** |
| Subnet address range | **10.10.0.0/27** |

<img src="Images/Virtual Network/Virtual network subnet 4.png">

- The list of available subnets should appear on the **Subnet** page

<img src="Images/Virtual Network/Virtual network subnet 5.png">
