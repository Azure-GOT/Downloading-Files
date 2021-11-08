# Secure your virtual hub using Azure Firewall Manager

For reference: https://docs.microsoft.com/en-in/azure/firewall-manager/secure-cloud-network?WT.mc_id=APC-FirewallManager


With the help of Azure Firewall Manager, we can create secured virtual hubs which will secured the cloud network traffic.

<img src="Images/secure-cloud-network.png">

<h3>Create two virtual networks that contains servers in them and those will be protected by firewall</h3>

<b>Steps:</b>

<ul>
  <li>Open the Azure Portal</li>
  <li>Select the <b>＋Create a resource</b> button, search for <b>Virtual Network</b>, and create with the following settings:</li>
  <ul>
    <li><b>Subscription</b> : Select your Azure Subscription</li>
    <li><b>Resource Group</b> : fw-manager-rg</li>
    <li><b>Name</b> : Spoke-01</li>
    <li><b>Region</b> : East US</li>
  </ul>
  <li>In the Next tab: IP Addresses, enter the following details</li>
  <ul>
    <li><b>IPv4 address space</b> : Enter 10.0.0.0/16</li>
    <li>Click on <b>Add Subnet</b>, enter <b>Name</b> : Workload-01-SN and <b>Subnet address range</b> : 10.0.1.0/24</li>
    <li>Click on <b>Save</b></li>
  </ul>
  <li>Click on the <b>Review and Create</b> button. After validation passed <b>Create</b> the resource </li>
  <li>Wait for the deployment to complete</li>
  
  <img src="Images/Firewall 1.png">
 </ul>
 
Repeat the same process with the following changes:
<ul>
  <li><b>Name:</b> Spoke-02</li>
  <li><b>Address space:</b> 10.1.0.0/16</li>
  <li><b>Subnet name:</b> Workload-02-SN</li>
  <li><b>Subnet address range:</b> 10.1.1.0/24</li>
  
  <img src="Images/Firewall 2.png">
</ul>

<h3>Create the secured virtual hub</h3>
 
<ul>
  <li>From the Azure Portal, in the top search bar search for <b>Firewall Manager</b></li>
  <li>From the Firewall Manager page, go to <b>Virtual Hub</b> and click on Create new secured virtual hub. Provide the following details</li>
  
  <img src="Images/Firewall 3.png">
  <ul>
    <li><b>Resource group</b>: fw-manager-rg</li>
    <li><b>Region</b>: East US</li>
    <li><b>Secured virtual hub name</b>: Hub-01</li>
    <li><b>Hub address space</b>: 10.2.0.0/16</li>
    <li><b>Virtual WAN name</b>: Vwan-01</li>
  </ul>
  <li>Leave the rest as default and click on <b>Create</b></li>
  <li>It will takes about 30 minutes to deploy</li>
  
  <img src="Images/Firewall 4.png">
</ul>

Once the deployment done, get the firewall public IP address.
<ul>
  <li>Go to Firewall Manager, click on <b>Virtual hubs</b></li>
  <li>Select the <b>Hub-01</b> and from under Public IP configuration note down the public IP address</li>
</ul>

<h3>Connect the hub with the virtual networks</h3>

<ul>
  <li>Go to the resource group <b>fw-manager-rg</b> and select <b>Vwan-01</b> virtual WAN</li>
  <li>From the <b>Connectivity</b> section, click on Virtual network connections</li>
  <li>Click on <b>Add connection</b> and enter the following details</li>
  <ul>
    <li><b>Connection name</b>: hub-spoke-01</li>
    <li><b>Hubs</b>: Hub-01</li>
    <li><b>Subscription</b> : Select your Azure Subscription</li>
    <li><b>Resource group</b> : fw-manager-rg</li>
    <li><b>Virtual network</b> : Spoke-01</li>
  </ul>
  <li>And click on <b>Create</b></li>
  
  <img src="Images/Firewall 5.png">
</ul>

Repeat the same procedure for the second virtual network <b>Spoke-02</b> with the connection name <b>hub-spoke-02</b>

<img src="Images/Firewall 6.png">

<h3>Deploy the servers in the virtual network</h3>

<ul>
 <li>Select the <b>＋Create a resource</b> button, search for <b>Virtual Machine</b>, and create with the following settings:</li>
 <ul>
   <li><b>Subscription</b> : Select your Azure Subscription</li>
   <li><b>Resource Group</b> : fw-manager-rg</li>
   <li><b>Name</b> : Srv-workload-01</li>
   <li><b>Region</b> : East US</li>
   <li><b>Availability Options</b> : No infrastructure redundancy required</li>
   <li><b>Image</b> : Windows Server 2019 Datacenter - Gen1</li>
   <li><b>Azure Spot instance</b> : Unchecked</li>
   <li><b>Size</b> : Leave default</li>
   <li><b>Username</b> : Enter the username as per your wish</li>
   <li><b>Password</b> : Enter the password</li>
   <li><b>Confirm Password</b> : Enter the same password</li>
   <li><b>Public inbound ports</b> : None</li>
 </ul>
 <li>Go to the Networking tab</li>
 <ul>
   <li><b>Virtual network</b> : Select Virtual network Spoke-01</li>
   <li><b>Subnet</b> : Workload-01-SN</li>
   <li><b>Public IP</b> : None</li>
 </ul>
  <li>Leave the rest details as default</li>
 <li>Click on the <b>Review and Create</b> button. After validation passed <b>Create</b> the resource </li>
 <li>Wait for the deployment to complete</li>

 <img src="Images/Firewall 7.png">

 <img src="Images/Firewall 8.png">
</ul>

<ul>
  <li>Create the second server with the following changes:</li>
  <ul>
    <li><b>Name:</b> Srv-Workload-02</li>
    <li><b>Virtual network:</b> Spoke-02</li>
    <li><b>Subnet:</b> Workload-02-SN</li>
  </ul>

  <img src="Images/Firewall 9.png">

  <img src="Images/Firewall 10.png">
</ul>
<b>Note down the private IP address of both the virtual machines from the networking tab</b>

<h3>Secure the hub with the help of Firewall policy</h3>

Firewall policy defines the collection of rules.

<ul>
  <li>Navigate to the Firewall Manager and select <b>Azure Firewall policies</b></li>
  <img src="Images/Firewall 11.png">
  
  <li>The new pane will appear to create the firewall policy and so provide the following details:</li>
  <ul>
    <li><b>Subscription</b>: Select your Azure Subscription</li>
    <li><b>Resource group</b>: fw-manager-rg</li>
    <li><b>Name</b>: Policy-01</li>
    <li><b>Region</b>: East US</li>
    <li><b>Policy Tier</b>: Standard</li>
  </ul>
  <li>Leave the rest as default and go to <b>Rules</b> tab, under that click on <b>+ Add a rule collection</b>. When the pane appears provide the following details</li>
  <ul>
    <li><b>Name:</b> App-RC-01</li>
    <li><b>Rule collection type:</b> Application</li>
    <li><b>Priority:</b> 100</li>
    <li><b>Rule collection action:</b> Allow</li>
    <li><b>Rule name:</b> Allow-msft</li>
    <li><b>Source type:</b> IP address</li>
    <li><b>Source:</b> *</li>
    <li><b>Protocol:</b> http,https</li>
    <li><b>Destination type:</b> FQDN</li>
    <li><b>Destination:</b> *.microsoft.com</li>
    <li>Click on <b>Add</b></li>
  </ul>
  <li>Add the DNAT rule to connect the remote desktop to the virtual machine</li>
  <ul>
    <li>Click on <b>+ Add a rule collection</b></li>
    <li><b>Name:</b> dnat-rdp</li>
    <li><b>Rule collection type:</b> DNAT</li>
    <li><b>Priority:</b> 100</li>
    <li><b>Rule collection action:</b> Allow</li>
    <li><b>Rule name:</b> Allow-rdp</li>
    <li><b>Source type:</b> IP address</li>
    <li><b>Source:</b> *</li>
    <li><b>Protocol:</b> TCP</li>
    <li><b>Destination Ports:</b> 3389</li>
    <li><b>Destination type:</b> IP address</li>
    <li><b>Destination:</b> firewall public IP address</li>
    <li><b>Translated address:</b> private IP address for VM Srv-Workload-01</li>
    <li><b>Translated port:</b> 3389</li>
    <li>Click on <b>Add</b></li>
  </ul>
  <li>Add a network rule to connect a remote desktop from one server to another</li>
  <ul>
    <li>Click on <b>+ Add a rule collection</b></li>
    <li><b>Name:</b> vnet-rdp</li>
    <li><b>Rule collection type:</b> Network</li>
    <li><b>Priority:</b> 100</li>
    <li><b>Rule collection action:</b> Allow</li>
    <li><b>Rule name:</b> Allow-vnet</li>
    <li><b>Source type:</b> IP address</li>
    <li><b>Source:</b> *</li>
    <li><b>Protocol:</b> TCP</li>
    <li><b>Destination Ports:</b> 3389</li>
    <li><b>Destination type:</b> IP address</li>
    <li><b>Destination:</b> private IP address for VM Srv-Workload-02</li>
    <li>Click on <b>Add</b></li>
  </ul>
  <li>Click on <b>Review + create</b> and after validation passed click on <b>Create</b></li>
  <li>Wait for the deployment to complete</li>
  
  <img src="Images/Firewall 12.png">
</ul>

<b>Now associate the firewall policy with the hub</b>
<ul>
  <li>From Firewall Manager, select Azure Firewall policies</li>
  <li>Select the check box for the <b>Policy-01</b></li>
  <li>Click on <b>Manage associations</b> and then select <b>Associate hubs</b></li>
  <li>Select Hub-01 and click on Add</li>

  <img src="Images/Firewall 13.png">
</ul>

After the we wants to make sure that the network traffic gets routed through firewall, so for that follow these steps:
<ul>
  <li>Go to Firewall Manager, and select Virtual hubs. Select <b>Hub-01</b></li>
  <li>Under Settings, select Security configuration</li>
  <li>In the Internet traffic, select Azure Firewall</li>
  <li>In the Private traffic, select Send via Azure Firewall</li>
  <li>Click on Save. Wait for few minutes and verify the connection got <b>Secured by Azure Firewall</b>

  <img src="Images/Firewall 14.png">


  <img src="Images/Firewall 15.png">
</ul>

<h3>Test the Firewall</h3>

For the <b>Application rule</b>, Connect the remote desktop to firewall public IP address using virtual machine Srv-Workload-01 credentials.

Open the Internet Explorer and browse to https://www.microsoft.com , you should be able to see the Microsoft home page.

<img src="Images/Firewall 16.png">

Now browse to https://www.google.com , it will be blocked by firewall

<img src="Images/Firewall 17.png">

For the <b>Network Rule</b> to check, open a remote desktop to the VM Srv-Workload-02 private IP address from the VM Srv-Workload-01.

The remote desktop should work.
