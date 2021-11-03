# Using network watcher's NSG flow log capability, enable a traffic log for NSG.md

With the help of Network's Watcher NSG flow log capability, we can log the network traffic that flows through NSG. The NSG enables to filter inbound and outbound traffic of Virtual Machine(VM)


<b>Step 1:</b> Create a VM

<ul>
  <li>Go to Azure Portal</li>
  <li>Select the <b>＋Create a resource</b> button, search for <b>Virtual Machine</b>, and create with the following settings:</li>
  <ul>
    <li><b>Subscription</b> : Select your Azure Subscription</li>
    <li><b>Resource Group</b> : Choose or create a resource group</li>
    <li><b>Name</b> : myVM1</li>
    <li><b>Region</b> : East US</li>
    <li><b>Availability Options</b> : No infrastructure redundancy required</li>
    <li><b>Image</b> : Windows Server 2019 Datacenter - Gen1</li>
    <li><b>Azure Spot instance</b> : Unchecked</li>
    <li><b>Size</b> : Leave default</li>
    <li><b>Username</b> : Enter the username as per your wish</li>
    <li><b>Password</b> : Enter the password</li>
    <li><b>Confirm Password</b> : Enter the same password</li>
  </ul>
  <li>Leave the rest of the setting as default</li>
 </ul>
 
 
 <b>Step 2:</b> Register the insights provider
 
 <ul>
  <li>In the Azure portal, to go your active subscription</li>
  <li>Under the Resource Provider, search for microsoft.insights and make sure it is registered, if not click on register.</li>
 </ul>


<img src="Images/microsoft insight.png">


<b>Step 3:</b> Create a storage account

We need the storage account for storing NSG flow log data, follow these steps for creation of storage account

<ul>
  <li>Select the <b>＋Create a resource</b> button, search for <b>Storage account</b>, and create with the following settings:</li>
  <ul>
    <li><b>Subscription</b> : Select your Azure Subscription</li>
    <li><b>Resource Group</b> : Choose or create a resource group</li>
    <li><b>Name</b> : nsgflowlogsstorage03</li>
    <li><b>Region</b> : East US</li>
    <li><b>Performance</b> : Standard</li>
    <li><b>Redundancy</b> : Locally-redundant storage(LRS)</li>
  </ul>
  <li>Rest of the setting leave as default</li>
 </ul>

<img src="Images/storage account.png">

<img src="Images/flow log.png">

<img src="Images/flow log 1.png">

<img src="Images/container.png">

<img src="Images/file.png">

<img src="Images/ex1.png">

<img src="Images/ex2.png">
