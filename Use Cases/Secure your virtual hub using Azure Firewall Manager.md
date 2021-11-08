# Secure your virtual hub using Azure Firewall Manager

For reference: https://docs.microsoft.com/en-in/azure/firewall-manager/secure-cloud-network?WT.mc_id=APC-FirewallManager

<b>Create two virtual networks that contains servers in them and those will be protected by firewall</b>

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
 </ul>
 
Repeat the same process with the following changes:
<ul>
  <li><b>Name:</b> Spoke-02</li>
  <li><b>Address space:</b> 10.1.0.0/16</li>
  <li><b>Subnet name:</b> Workload-02-SN</li>
  <li><b>Subnet address range:</b> 10.1.1.0/24</li>
</ul>

<b>Create the secured virtual hub</b>
 
 
