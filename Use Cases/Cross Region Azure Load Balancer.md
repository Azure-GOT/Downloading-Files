# Cross Region Azure Load Balancer

<b>Use-Case Scenario:</b> If the region fails, then the taffic should be routed to the closest regional load balancer which must be healthy. We can use Cross-Region Load Balancer.

<img src="Images/cross-region-load-balancer.png">

<b>Creating Load Balancer in one region</b> 

Follow this link for reference: <a href="https://docs.microsoft.com/en-in/azure/load-balancer/quickstart-load-balancer-standard-public-portal?tabs=option-1-create-load-balancer-standard">Link</a>

<b>Step 1:</b> Create a <b>Virtual Network</b>
<ul>
  <li>Open the Azure Portal</li>
  <li>Select the <b>＋Create a resource</b> button, search for <b>Virtual Network</b>, and create with the following settings:</li>
  <ul>
    <li><b>Subscription</b> : Select your Azure Subscription</li>
    <li><b>Resource Group</b> : Choose or create a resource group</li>
    <li><b>Name</b> : Enter a unique name</li>
    <li><b>Region</b> : East US</li>
  </ul>
  <li>In the Next tab: IP Addresses, enter the following details</li>
  <ul>
    <li><b>IPv4 address space</b> : Enter 10.1.0.0/16</li>
    <li>Click on <b>Add Subnet</b>, enter <b>Name</b> : myBackendSubnet and <b>Subnet address range</b> : 10.1.0.0/24</li>
    <li>Click on <b>Add</b></li>
  </ul>
  <li>Go to the <b>Security</b> tab and enable the BastionHost with the following details</li>
  <ul>
    <li><b>Bastion name</b> : myBastionHost</li>
    <li><b>AzureBastionSubnet address space</b> : 10.1.1.0/27</li>
    <li><b>Public IP Address</b>: Select <b>Create new</b>, enter <b>name</b>: myBastionIP and select <b>Ok</b></li>
  </ul>
  <li>Click on the <b>Review and Create</b> button. After validation passed <b>Create</b> the resource </li>
  <li>Wait for the deployment to complete</li>
 </ul>
 
 <img src="Images/Creation of Virtual Network.png">
 
 <b>Step 2:</b> Create a NAT Gateway
 
 NAT Gateway is for outbound internet access for resources in the virtual network
 
 <ul>
  <li>Select the <b>＋Create a resource</b> button, search for <b>NAT Gateway</b>, and create with the following settings:</li>
  <ul>
    <li><b>Subscription</b> : Select your Azure Subscription</li>
    <li><b>Resource Group</b> : Choose or create a resource group</li>
    <li><b>NAT Gateway Name</b> : Enter a unique name</li>
    <li><b>Region</b> : East US</li>
    <li><b>Availability zone</b> : None</li>
    <li><b>Idle timeout (minutes)</b> : 15</li>
  </ul>
  <li>Go to the next tab <b>Outbound IP</b> and select <b>Create a new public IP address</b></li>
  <ul>
    <li>Enter <b>Name</b> : myNATGatewayIP and select <b>Ok</b></li>
  </ul>
  <li>Go to the next tab <b>Subnet</b></li>
  <ul>
    <li>In the <b>Virtual network</b>, select the virtual network that you created earlier</li>
    <li>Under the <b>Subnet name</b> select <b>myBackendSubnet</b></li>
  </ul>
  <li>Click on the <b>Review and Create</b> button. After validation passed <b>Create</b> the resource </li>
  <li>Wait for the deployment to complete</li>
 </ul>
 
 <img src="Images/Creation of NAT Gateway.png">
 
 <b>Step 3:</b> Create a Load Balancer
 
 Load balancing will evenly distributes the load (incoming network traffic) across a group of backend resources or servers.
 
 <ul>
  <li>Select the <b>＋Create a resource</b> button, search for <b>Load Balancer</b>, and create with the following settings:</li>
  <ul>
    <li><b>Subscription</b> : Select your Azure Subscription</li>
    <li><b>Resource Group</b> : Choose or create a resource group</li>
    <li><b>Name</b> : Enter a unique name</li>
    <li><b>Region</b> : East US</li>
    <li><b>SKU</b> : Standard</li>
    <li><b>Type</b> : Public</li>
    <li><b>Tier</b> : Regional</li>
  </ul>
  <li>Go to the next tab <b>Frontend IP configuration</b></li>
  <ul>
    <li>Click on <b>+Add a Frontend IP configuration</b></li>
    <li><b>Name</b> : LoadBalancerFrontend </li>
    <li><b>IP version</b> : IPv4</li>
    <li><b>IP type</b> : IP address</li>
    <li>Select <b>Create new</b> in the <b>Public IP address</b> and enter <b>name</b> as myPublicIP</li>
    <li><b>Availability zone</b> : Zone-redundant</li>
    <li>Select <b>Ok</b> and <b>Add</b></li>
  </ul>
  <li>Go to the the next tab <b>Backend pools</b></li>
  <ul>
    <li>Click on <b>+ Add a backend pool</b></li>
    <li><b>Name</b> : myBackendPool</li>
    <li><b>Virtual network</b> : That you created earlier</li>
    <li><b>Backend Pool Configuration</b> : NIC</li>
    <li><b>IP version</b> : IPv4</li>
    <li>Click on <b>Add</b></li>
  </ul>
  <li>Go to next tab <b>Inbound rules</b></li>
  <ul>
    <li>Click on <b>+ Add a load balancing rule</b> and add the following details</li>
    <li><b>Name</b> : myHTTPRule</li>
    <li><b>IP Version</b> : IPv4</li>
    <li><b>Frontend IP address</b> : LoadBalancerFrontend</li>
    <li><b>Protocol</b> : TCP</li>
    <li><b>Port</b> : 80</li>
    <li><b>Bakend port</b> : 80</li>
    <li><b>Backend pool</b> : myBackendPool</li>
    <li><b>Health probe</b> : Click on <b>Create New</b>, enter name as myHealthProbe, <b>protocol</b>:HTTP, and click on Ok</li>
    <li><b>Session persistence</b> : None</li>
    <li><b>Idle timeout (minutes)</b> : 15</li>
    <li><b>TCP reset</b> : Enabled</li>
    <li><b>Floating IP</b> : Disabled</li>
    <li><b>Outbound source network address translation (SNAT)</b> : Leave the Default</li>
    <li>Click on <b>Add</b>
  </ul>
  <li>Click on the <b>Review and Create</b> button. After validation passed <b>Create</b> the resource </li>
  <li>Wait for the deployment to complete</li>
 </ul>
 
 
 <img src="Images/Creation of Load Balancer.png">
 
 <b>Step 4:</b> Create a Virual Machine
 
 <ul>
  <li>Select the <b>＋Create a resource</b> button, search for <b>Virtual Machine</b>, and create with the following settings:</li>
  <ul>
    <li><b>Subscription</b> : Select your Azure Subscription</li>
    <li><b>Resource Group</b> : Choose or create a resource group</li>
    <li><b>Name</b> : myVM1</li>
    <li><b>Region</b> : East US</li>
    <li><b>Availability Options</b> : Availability zones</li>
    <li><b>Availability zone</b> : 1</li>
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
    <li><b>Virtual network</b> : select Virtual network that you created</li>
    <li><b>Subnet</b> : myBackendSubnet</li>
    <li><b>Public IP</b> : None</li>
    <li><b>NIC network security group</b> : Advanced</li>
    <li><b>Configure network security group</b> : Select <b>Create new</b>, enter name as myNSG, click on <b>+Add an inbound rule</b> under Inbound Rules, select <b>HTTP</b>
      as Service, set priority as 100, in the name enter myNSGRule and click on Add</li>
    <li><b>Place this virtual machine behind an existing load-balancing solution?</b> :Select the Box</li>
    <ul>
      <li><b>Load-balancing options</b> : Azure load balancing</li>
      <li><b>Select a load balancer</b> : myLoadBalancer</li>
      <li><b>Select a backend pool</b> : myBackendPool</li>
    </ul>
    </ul>
  <li>Click on the <b>Review and Create</b> button. After validation passed <b>Create</b> the resource </li>
  <li>Wait for the deployment to complete</li>
 </ul>
    
 <b>Follow the same procedure for the rest of the two VMs changing thier names, select 2 and 3 as Availability zone for the respective VMs, and choose the existing NSGs as
  Network Security Group</b>
 
 <img src="Images/Creation of VM-1.png">
 <img src="Images/Creation of Vm-2.png">
  
<b>Step 5:</b> Install IIS 

<ul>
  <li>Go to the first VM( myVM-01) that you created</li>
  <li>In the <b>Overview</b> page select Connect and then Bastion</li>
  <li>Select <b>Use Bastion</b></li>
  <li>Enter the username and password and click on <b>Create</b></li>
  <li>From the Start Menu, search for Windows PowerShell and add the following commands</li>
        
        # Install IIS server role
        Install-WindowsFeature -name Web-Server -IncludeManagementTools

        # Remove default htm file
        Remove-Item  C:\inetpub\wwwroot\iisstart.htm

        # Add a new htm file that displays server name
        Add-Content -Path "C:\inetpub\wwwroot\iisstart.htm" -Value $("Hello World from " + $env:computername)
  
  <img src="Images/">
  
  <li>Close the Bastion and follow this on rest of the VMs</li>
 </ul>
 
 <b>Create the second load balancer in the different region, and also add R2 as suffix to all the resources associated with it.</b>
 
 <b>Step 6:</b> Create a Cross Region Load Balancer
 
 <b>Follow the same procedure for creating the Load Balancer except for the following details</b>
 <ul>
  <li>Choose <b>Region</b> only from the following options</li>
  <ul>
    <li>East US 2</li>
    <li>West US</li>
    <li>West Europe</li>
    <li>Southeast Asia</li>
    <li>Central US</li>
    <li>North Europe</li>
    <li>East Asia</li>
  </ul>
  <li><b>Tier</b> : Global</li>
  <li>In the <b>Backend pool</b> select the two Load Balancers that you created</li>
 </ul>
 
 From the overview page copy the public IP address and paste it in the web browser, you will be redirct to one of the VM. Now shut down the virtual machines and see the load balancer will redirect to another VM.
