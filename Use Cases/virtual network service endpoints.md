# Restrict network access to PaaS resources with virtual network service endpoints

For reference: https://docs.microsoft.com/en-in/azure/virtual-network/tutorial-restrict-network-access-to-resources

<h3>Create a Virtual Network</h3>

<ul>
  <li>Open the Azure Portal</li>
  <li>Select the <b>＋Create a resource</b> button, search for <b>Virtual Network</b>, and create with the following settings:</li>
  <ul>
    <li><b>Subscription</b> : Select your Azure Subscription</li>
    <li><b>Resource Group</b> : demo</li>
    <li><b>Name</b> : myVirtualNetwork</li>
    <li><b>Region</b> : East US</li>
  </ul>
  <li>In the Next tab: IP Addresses, enter the following details</li>
  <ul>
    <li><b>IPv4 address space</b> : Leave as default.</li>
    <li><b>Subnet name</b> : Select default and change the subnet name to "Public"</li>
    <li><b>Subnet Address Range</b> : Leave as default</li>
  </ul>
  <li>Leave the rest as default</li>
  <li>Click on the <b>Review and Create</b> button. After validation passed <b>Create</b> the resource </li>
  <li>Wait for the deployment to complete</li>
 </ul>
 
<img src="Images/Restrict network access 1.png">


<h3>Enable the service endpoint</h3>

<ul>
  <li>Go to the virtual network that you created, under the <b>Subnets</b> blade and click on <b>+ Subnet</b></li>

  <img src="Images/Restrict network access 2.png">

  <li>On the <b>Add subnet</b> page enter the following details</li>
  <ul>
    <li><b>Name</b>: Private</li>
    <li><b>Service endpoints</b>: Select Microsoft.Storage</li>
    <li>Leave the rest as default</li>
  </ul>
  
  <img src="Images/Restrict network access 3.png">
  
  <img src="Images/Restrict network access 4.png">

</ul>  

<h3>Restrict network access for a subnet</h3>

<ul>
  <li>Open the Azure Portal</li>
  <li>Select the <b>＋Create a resource</b> button, search for <b>Network Security Group</b>, and create with the following settings:</li>
  <ul>
    <li><b>Subscription</b> : Select your Azure Subscription</li>
    <li><b>Resource Group</b> : demo</li>
    <li><b>Name</b> : myNsgPrivate</li>
    <li><b>Region</b> : East US</li>
  </ul>
  <li>Click on the <b>Review and Create</b> button. After validation passed <b>Create</b> the resource </li>
  <li>Wait for the deployment to complete</li>
 </ul>
<img src="Images/Restrict network access 5.png">

<ul>
  <li>Go to the resource that you created. Select Outbound security rules under Settings and click on <b>+ Add</b></li> 

  <img src="Images/Restrict network access 6.png">

  <li>Enter the following details in the <b>Add Outbound security rule</b> pane</li>
  <ul>
    <li><b>Source</b>: VirtualNetwork</li>
    <li><b>Source port ranges</b>: *</li>
    <li><b>Destination</b>: Service Tag</li>
    <li><b>Destination service tag</b>: Storage</li>
    <li><b>Service</b>: Leave as default</li>
    <li><b>Destination port ranges</b>: 445</li>
    <li><b>Protocol</b>: Any</li>
    <li><b>Action</b>: Allow</li>
    <li><b>Priority</b>: 100</li>
    <li><b>Name</b>: Allow-Storage-All</li>
  </ul>
  <img src="Images/Restrict network access 7.png">

  <img src="Images/Restrict network access 8.png">
  

  <li>Add another <b>Outbound security Rule</b> with the following details</li>
  <ul>
    <li><b>Source</b>: VirtualNetwork</li>
    <li><b>Source port ranges</b>: *</li>
    <li><b>Destination</b>: Service Tag</li>
    <li><b>Destination service tag</b>: Internet</li>
    <li><b>Service</b>: Leave as default</li>
    <li><b>Destination port ranges</b>: *</li>
    <li><b>Protocol</b>: Any</li>
    <li><b>Action</b>: Deny</li>
    <li><b>Priority</b>: 110</li>
    <li><b>Name</b>: Deny-Internet-All</li>
  </ul>
  
  <img src="Images/Restrict network access 9.png">

  <img src="Images/Restrict network access 10.png">
</ul>

<ul>
  <li>Select Inbound security rules under Settings and click on <b>+ Add</b></li> 
  
  <img src="Images/Restrict network access 11.png">

  <li>Enter the following details in the <b>Add Inbound security rule</b> pane</li>
  <ul>
    <li><b>Source</b>: Any</li>
    <li><b>Source port ranges</b>: *</li>
    <li><b>Destination</b>: VirtualNetwork</li>
    <li><b>Service</b>: RDP</li>
    <li><b>Destination port ranges</b>: 3389</li>
    <li><b>Action</b>: Allow</li>
    <li><b>Priority</b>: 120</li>
    <li><b>Name</b>:Allow-RDP-All</li>
  </ul>
  <img src="Images/Restrict network access 12.png">

  <img src="Images/Restrict network access 13.png">

  <img src="Images/Restrict network access 14.png">

  <img src="Images/Restrict network access 15.png">
</ul>

<ul>
  <li>Under <b>Settings</b>, select <b>Subnets</b> and click on <b>+ Associate</b> with the <b>myVirtualNetwork</b> as virtual network and <b>Private</b> as subnet</li>
  <img src="Images/Restrict network access 16.png">
  
</ul>

<h3>Restrict network access to a resource</h3>

<h4>Create a <b>storage account</b></h4>
<img src="Images/Restrict network access 17.png">

<img src="Images/Restrict network access 18.png">

<img src="Images/Restrict network access 19.png">

<img src="Images/Restrict network access 20.png">

<img src="Images/Restrict network access 21.png">

<img src="Images/Restrict network access 22.png">

<img src="Images/Restrict network access 23.png">

<img src="Images/Restrict network access 24.png">

<img src="Images/Restrict network access 25.png">

<img src="Images/Restrict network access 26.png">

<img src="Images/Restrict network access 27.png">
