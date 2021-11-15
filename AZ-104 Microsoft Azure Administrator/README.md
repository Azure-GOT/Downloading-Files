**Q1.** Your company has serval departments. Each department has a number of virtual machines (VMs).
The company has an Azure subscription that contains a resource group named RG1.
All VMs are located in RG1.
You want to associate each VM with its respective department.

What should you do?
1. Create Azure Management Groups for each department
2. Create a resource group for each department
3. Assign tags to the virtual machines
4. Modify the settings of the virtual machines

**Ans: 3. Assign tags to the virtual machines**

---

**Q2.** You are planning to deploy an Ubuntu Server virtual machine to your company's Azure subscription.
You are required to implement a custom deployment that includes adding a particular trusted root certification authority (CA).

Which of the following should you use to create the virtual machine?
1. The New-AzureRmVm cmdlet
2. The New-AzVM cmdlet
3. The Create-AzVM cmdlet
4. The az vm create command

**Ans: 4. The az vm create command**

---

**Q3.** Your company has a Microsoft Azure subscription.
The company has datacenters in Los Angeles and New York.
You are configuring the two datacenters as geo-clustered sites for site resiliency.
You need to recommend an Azure storage redundancy option.
You have the following data storage requirements:
- Data must be stored on multiple nodes.
- Data must be stored on nodes in separate geographic locations.
- Data can be read from the secondary location as well as from the primary location. 

Which of the following Azure stored redundancy options should you recommend?
1. Geo-redundant storage
2. Read-only geo-redundant storage
3. Zone-redundant storage
4. Locally redundant storage

**Ans: 2. Read-only geo-redundant storage**

**Explanation:** RA-GRS allows to have higher read availability for the storage account by providing read only access to the data replicated to the secondary location

---

**Q4.** Your company has three virtual machines (VMs) that are included in an availability set.
You try to resize one of the VMs, which returns an allocation failure message.
It is imperative that the VM is resized.

Which of the following actions should you take?
1. You should only stop one of the VMs.
2. You should stop two of the VMs
3. You should stop all three VMs
4. You should remove the necessary VM from the availability set

**Ans: 3. You should stop all three VMs**

**Explanation:** The reason all VMs in the availability set must be stopped before performing the resize operation to a size that requires different hardware is that all running VMs in the availability set must be using the same physical hardware cluster. Therefore, if a change of physical hardware cluster is required to change the VM size then all VMs must be first stopped and then restarted one-by-one to a different physical hardware clusters

---

**Q5.** You have an Azure virtual machine (VM) that has a single data disk. You have been tasked with attaching this data disk to another Azure VM.
You need to make sure that your strategy allows for the virtual machines to be offline for the least amount of time possible.

Which of the following is the action you should take FIRST?
1. Stop the VM that includes the data disk.
2. Stop the VM that the data disk must be attached to
3. Detach the data disk
4. Delete the VM that includes the data disk

**Ans: 3. Detach the data disk**

**Explanation:** You can hot remove a data disk, but make sure nothing is actively using the disk before detaching it from the VM.

---

**Q6.** You need to deploy a number of Azure virtual machines (VMs) using Azure Resource Manager (ARM) templates. You have been informed that the VMs will be included in a single availability set.
You are required to make sure that the ARM template you configure allows for as many VMs as possible to remain accessible in the event of fabric failure or maintenance.

Which of the following is the value that you should configure for the platformFaultDomainCount property?
1. 10
2. 30
3. Min Value
4. Max Value

**Ans: 4. Max Value**

**Explanation:** The number of fault domains for managed availability sets varies by region - either two or three per region.

---

**Q7.** You need to deploy a number of Azure virtual machines (VMs) using Azure Resource Manager (ARM) templates. You have been informed that the VMs will be included in a single availability set.
You are required to make sure that the ARM template you configure allows for as many VMs as possible to remain accessible in the event of fabric failure or maintenance.

Which of the following is the value that you should configure for the platformUpdateDomainCount property?
1. 10
2. 20
3. 30
4. 40

**Ans: 2. 20**

**Explanation:** Each availability set can be configured with up to three fault domains and twenty update domains.

---

**Q8.** You have downloaded an Azure Resource Manager (ARM) template to deploy numerous virtual machines (VMs). The ARM template is based on a current VM, but must be adapted to reference an administrative password.
You need to make sure that the password cannot be stored in plain text.
You are preparing to create the necessary components to achieve your goal.

Which of the following should you create to achieve your goal?
1. An Azure Key Vault
2. Az Azure storage account
3. Azure Active Directory(AD) Identity protection
4. An Access policy
5. Az Azure policy
6. A backup policy

**Ans: 1. An Azure Key Vault, 4. An Access policy

**Explanation:** Key Vault will store your KV pairs and you need to configure the access policy to determine the level of access that a service principal (ARM template will use) can perform against the key vault.

---

**Q9.** Your company has an azure subscription that includes a storage account, a resource group, a blob container and a file share.
A colleague named Jon Ross makes use of a solitary Azure Resource Manager (ARM) template to deploy a virtual machine and an additional Azure Storage account.
You want to review the ARM template that was used by Jon Ross.

**Solution 1:** You access the Virtual Machine blade.

**Ans: No**

**Solution 2:** You access the Resource Group blade.

**Ans: Yes**

**Solution 3:** You access the Container blade.

**Ans: No**

---

**Q10.** Your company has an Azure Active Directory (Azure AD) tenant named weyland.com that is configured for hybrid coexistence with the on-premises Active
Directory domain.
You have a server named DirSync1 that is configured as a DirSync server.
You create a new user account in the on-premise Active Directory. You now need to replicate the user information to Azure AD immediately.

**Solution 1:** You run the Start-ADSyncSyncCycle -PolicyType Initial PowerShell cmdlet

**Ans: No**

**Explanation:** Running a full sync cycle can be very time consuming, so if you need to replicate the user information to Azure AD immediately then run Start-ADSyncSyncCycle -PolicyType Delta

**Solution 2:** You use Active Directory Sites and Services to force replication of the Global Catalog on a domain controller

**Ans: No**

**Solution 3:** You restart the NetLogon service on a domain controller

**Ans: No**

---

**Q11.** Your company makes use of Multi-Factor Authentication for when users are not in the office. The Per Authentication option has been configured as the usage model.
After the acquisition of a smaller business and the addition of the new staff to Azure Active Directory (Azure AD) obtains a different company and adding the new employees to Azure Active Directory (Azure AD), you are informed that these employees should also make use of Multi-Factor Authentication.
To achieve this, the Per Enabled User setting must be set for the usage model.

**Solution 1:** You reconfigure the existing usage model via the Azure portal.

**Ans: No**

**Solution 2:** You reconfigure the existing usage model via the Azure CLI.

**Ans: No**

**Solution 3:** You create a new Multi-Factor Authentication provider with a backup from the existing Multi-Factor Authentication provider data

**Ans: Yes**

**Explanation:** It is not possible to change the usage model of an existing provider, we have to create a new one and reactivate the existing server with activation credentials from the new provider.

---


**Q12.** Consider the scenario: Your company has an Azure Active Directory (Azure AD) subscription.
You want to implement an Azure AD conditional access policy.
The policy must be configured to require members of the Global Administrators group to use Multi-Factor Authentication and an Azure AD-joined device when they connect to Azure AD from untrusted locations.

**Solution 1:** You access the multi-factor authentication page to alter the user settings

**Ans: No**

**Solution 2:** You access the Azure portal to alter the session control of the Azure AD conditional access policy

**Ans: No**

**Solution 3:** You access the Azure portal to alter the grant control of the Azure AD conditional access policy

**Ans: Yes**

---

**Q13.** Your company has an Azure Active Directory (Azure AD) tenant that is configured for hybrid coexistence with the on-premises Active Directory domain.
The on-premise virtual environment consists of virtual machines (VMs) running on Windows Server 2012 R2 Hyper-V host servers.
You have created some PowerShell scripts to automate the configuration of newly created VMs. You plan to create several new VMs.
You need a solution that ensures the scripts are run on the new VMs.

Which of the following is the best solution?
1. Configure a SetupComplete.cmd batch file in the %windir%\setup\scripts directory
2. Configure a Group Policy Object (GPO) to run the scripts as logon scripts
3. Configure a Group Policy Object (GPO) to run the scripts as startup scripts
4. Place the scripts in a new virtual hard disk (VHD)

**Ans: 1. Configure a SetupComplete.cmd batch file in the %windir%\setup\scripts directory**

**Explanation:** After Windows is installed but before the logon screen appears, Windows Setup searches for the SetupComplete.cmd file in the %windir%\setup\scripts directory

---

**Q14.** Your company has an Azure Active Directory (Azure AD) tenant that is configured for hybrid coexistence with the on-premises Active Directory domain.
You plan to deploy several new virtual machines (VMs) in Azure. The VMs will have the same operating system and custom software requirements.
You configure a reference VM in the on-premise virtual environment. You then generalize the VM to create an image.
You need to upload the image to Azure to ensure that it is available for selection when you create the new Azure VMs.

Which PowerShell cmdlets should you use?
1. Add-AzVM
2. Add-AzVhd
3. Add-AzImage
4. Add-AzImageDataDisk

**Ans: 2. Add-AzVhd**

**Explanation:** The Add-AzVhd cmdlet uploads on-premises virtual hard disks, in .vhd file format, to a blob storage account as fixed virtual hard disks. 
Example: *Add-AzVhd -ResourceGroupName $resourceGroup -Destination $urlOfUploadedImageVhd -LocalFilePath $localPath*

---

**Q15.** Your company has an Azure subscription that includes a number of Azure virtual machines (VMs), which are all part of the same virtual network.
Your company also has an on-premises Hyper-V server that hosts a VM, named VM1, which must be replicated to Azure.

Which of the following objects that must be created to achieve this goal?
1. Hyper-V site
2. Storage account
3. Azure Recovery Service Vault
4. Azure Traffic Manager instance
5. Replication policy
6. Endpoint

**Ans: 1. Hyper-V site, 3. Azure Recovery Service Vault, 5. Replication policy**

---

**Q16.** Your company's Azure subscription includes two Azure networks named VirtualNetworkA and VirtualNetworkB.
VirtualNetworkA includes a VPN gateway that is configured to make use of static routing. Also, a site-to-site VPN connection exists between your company's on- premises network and VirtualNetworkA.
You have configured a point-to-site VPN connection to VirtualNetworkA from a workstation running Windows 10. After configuring virtual network peering between
VirtualNetworkA and VirtualNetworkB, you confirm that you are able to access VirtualNetworkB from the company's on-premises network. However, you find that you cannot establish a connection to VirtualNetworkB from the Windows 10 workstation.
You have to make sure that a connection to VirtualNetworkB can be established from the Windows 10 workstation.

**Solution 1:** You choose the Allow gateway transit setting on VirtualNetworkA.

**Ans: No**

**Solution 1:** You choose the Allow gateway transit setting on VirtualNetworkB.

**Ans: No**

**Solution 3:** You download and re-install the VPN client configuration package on the Windows 10 workstation

**Ans: Yes**

**Explanation:** If you make a change to the topology of your network and have Windows VPN clients, the VPN client package for Windows clients must be downloaded and installed again in order for the changes to be applied to the client.

---

**Q17.** Your company has virtual machines (VMs) hosted in Microsoft Azure. The VMs are located in a single Azure virtual network named VNet1.
The company has users that work remotely. The remote workers require access to the VMs on VNet1.
You need to provide access for the remote workers.

What should you do?
1. Configure a Site-to-Site (S2S) VPN.
2. Configure a VNet-toVNet VPN
3. Configure a Point-to-Site (P2S) VPN
4. Configure DirectAccess on a Windows Server 2012 server VM
5. Configure a Multi-Site VPN

**Ans: 3. Configure a Point-to-Site (P2S) VPN**

**Explanation:** A Point-to-Site (P2S) VPN gateway connection lets you create a secure connection to your virtual network from an individual client computer.

---

**Q18.** Your company has a Microsoft SQL Server Always On availability group configured on their Azure virtual machines (VMs).
You need to configure an Azure internal load balancer as a listener for the availability group.

**Solution 1:** You create an HTTP health probe on port 1433

**Ans: No**

**Solution 2:** You set Session persistence to Client IP

**Ans: No**

**Solution 3:** You enable Floating IP

**Ans: Yes**

---

**Q19.** Your company has two on-premises servers named SRV01 and SRV02. Developers have created an application that runs on SRV01. The application calls a service on SRV02 by IP address.
You plan to migrate the application on Azure virtual machines (VMs). You have configured two VMs on a single subnet in an Azure virtual network.
You need to configure the two VMs with static internal IP addresses.

What should you do?
1. Run the New-AzureRMVMConfig PowerShell cmdlet
2. Run the Set-AzureSubnet PowerShell cmdlet
3. Modify the VM properties in the Azure Management Portal
4. Modify the IP properties in Windows Network and Sharing Center
5. Run the Set-AzureStaticVNetIP PowerShell cmdlet

**Ans: 5. Run the Set-AzureStaticVNetIP PowerShell cmdlet**

---

**Q20.** Your company has an Azure Active Directory (Azure AD) subscription.
You need to deploy five virtual machines (VMs) to your company's virtual network subnet.
The VMs will each have both a public and private IP address. Inbound and outbound security rules for all of these virtual machines must be identical.

Which of the following is the least amount of **network interfaces** needed for this configuration?
1. 5
2. 10
3. 20
4. 40

**Ans 1. 5**

---

**Q21.** Your company has an Azure Active Directory (Azure AD) subscription.
You need to deploy five virtual machines (VMs) to your company's virtual network subnet.
The VMs will each have both a public and private IP address. Inbound and outbound security rules for all of these virtual machines must be identical.

Which of the following is the least amount of **security groups** needed for this configuration?
1. 4
2. 3
3. 2
4. 1

**Ans: 4. 1**

---

**Q22.** Your company's Azure subscription includes Azure virtual machines (VMs) that run Windows Server 2016.
One of the VMs is backed up every day using Azure Backup Instant Restore.
When the VM becomes infected with data encrypting ransomware, you decide to *recover the VM's files.*

Which of the following is TRUE in this scenario?
1. You can only recover the files to the infected VM
2. You can recover the files to any VM within the companyג€™s subscription
3. You can only recover the files to a new VM
4. You will not be able to recover the files

**Ans: You can only recover the files to the infected VM** (Not confirm)

---

**Q23.** Your company's Azure subscription includes Azure virtual machines (VMs) that run Windows Server 2016.
One of the VMs is backed up every day using Azure Backup Instant Restore.
When the VM becomes infected with data encrypting ransomware, you are required to restore the VM.

Which of the following actions should you take?
1. You should restore the VM after deleting the infected VM
2. You should restore the VM to any VM within the companyג€™s subscription
3. You should restore the VM to a new Azure VM
4. You should restore the VM to an on-premise Windows device

**Ans: 3. You should restore the VM to a new Azure VM**

---

**Q24.** You administer a solution in Azure that is currently having performance issues.
You need to find the cause of the performance issues pertaining to metrics on the Azure infrastructure.

Which of the following is the tool you should use?
1. Azure Traffic Analytics
2. Azure Monitor
3. Azure Activity Log
4. Azure Advisor

**Ans: 2. Azure Monitor**

Metrics in Azure Monitor are stored in a time-series database which is optimized for analyzing time-stamped data. This makes metrics particularly suited for alerting and fast detection of issues.

---

**Q25.** Your company has an Azure subscription that includes a Recovery Services vault.
You want to use Azure Backup to schedule a backup of your company's virtual machines (VMs) to the Recovery Services vault.

Which of the following VMs can you back up?
1. VMs that run Windows 10
2. VMs that run Windows Server 2012 or higher
3. VMs that have NOT been shut down
4. VMs that run Debian 8.2+
5. VMs that have been shut down

**Ans: ALL**

---

**Q26.** You have an Azure subscription that contains the following users in an Azure Active Directory tenant named contoso.onmicrosoft.com   :
| Name | Role | Scope |
| -- | -- | -- |
| User 1 | Global Administrator | Azure Active Directory |
| User 2 | Global Administrator | Azure Active Directory |
| User 3 | User Administrator | Azure Active Directory |
| User 4 | Owner | Azure Subscription |

User1 creates a new Azure Active Directory tenant named external.contoso.onmicrosoft.com.
You need to create new user accounts in external.contoso.onmicrosoft.com.

**Solution 1:** You instruct User3 to create the user accounts

**Ans: Yes**

*Only a global administrator can add users to the tenant*

**Solution 2:** You instruct User4 to create the user accounts

**Ans: No**

**Solution 3:** You instruct User3 to create the user accounts

**Ans: No**

---

**Q27.** You have an Azure subscription that contains an Azure Active Directory (Azure AD) tenant named contoso.com and an Azure Kubernetes Service (AKS) cluster named AKS1.
An administrator reports that she is unable to grant access to AKS1 to the users in contoso.com.
You need to ensure that access to AKS1 can be granted to the contoso.com users.

What should you do first?
1. From contoso.com, modify the Organization relationships settings
2. From contoso.com, create an OAuth 2.0 authorization endpoint
3. Recreate AKS1
4. From AKS1, create a namespace

**Ans: 2. From contoso.com, create an OAuth 2.0 authorization endpoint**

---

**Q28.** You have a Microsoft 365 tenant and an Azure Active Directory (Azure AD) tenant named contoso.com.
You plan to grant three users named User1, User2, and User3 access to a temporary Microsoft SharePoint document library named Library1.
You need to create groups for the users. The solution must ensure that the groups are deleted automatically after 180 days.

Which two groups should you create?
1. a Microsoft 365 group that uses the Assigned membership type
2. a Security group that uses the Assigned membership type
3. a Microsoft 365 group that uses the Dynamic User membership type
4. a Security group that uses the Dynamic User membership type
5. a Security group that uses the Dynamic Device membership type

**Ans: 1. a Microsoft 365 group that uses the Assigned membership type, 3. a Microsoft 365 group that uses the Dynamic User membership type**

*You can set expiration policy only for Office 365 groups in Azure Active Directory (Azure AD)*

---

**Q29.** You have an Azure subscription named AZPT1 that contains the resources shown in the following table:
| Name | Type | 
| -- | -- |
| storage1 | Azure storage account |
| VNET1 | Virtual network |
| VM1 | Azure virtual machine |
| VM1Managed | Managed disk for VM1 |
| RVAULT1 | Recovery service vault for the site recovery of VM1 |

You create a new Azure subscription named AZPT2.
You need to identify which resources can be moved to AZPT2.

Which resources should you identify?
1. VM1, storage1, VNET1, and VM1Managed only
2. VM1 and VM1Managed only
3. VM1, storage1, VNET1, VM1Managed, and RVAULT1
4. RVAULT1 only

**Ans: 3. VM1, storage1, VNET1, VM1Managed, and RVAULT1**

---

**Q30.** You recently created a new Azure subscription that contains a user named Admin1.
Admin1 attempts to deploy an Azure Marketplace resource by using an Azure Resource Manager template. Admin1 deploys the template by using Azure
PowerShell and receives the following error message: `User failed validation to purchase resources. Error message: "Legal terms have not been accepted for this item on this subscription. To accept legal terms, please go to the Azure portal (http:// go.microsoft.com /fwlink/?LinkId=534873) and configure programmatic deployment for the Marketplace item or create it there for the first time."
You need to ensure that Admin1 can deploy the Marketplace resource successfully.

What should you do?
1. From Azure PowerShell, run the Set-AzApiManagementSubscription cmdlet
2. From the Azure portal, register the Microsoft.Marketplace resource provider
3. From Azure PowerShell, run the Set-AzMarketplaceTerms cmdlet
4. From the Azure portal, assign the Billing administrator role to Admin1

**Ans: 3. From Azure PowerShell, run the Set-AzMarketplaceTerms cmdlet**

---

**Q31.** You have an Azure Active Directory (Azure AD) tenant that contains 5,000 user accounts.
You create a new user account named AdminUser1.
You need to assign the User administrator administrative role to AdminUser1.

What should you do from the user account properties?
1. From the Licenses blade, assign a new license
2. From the Directory role blade, modify the directory role
3. From the Groups blade, invite the user account to a new group

**Ans: 2. From the Directory role blade, modify the directory role**

*select Active directory --> Users--> select the username --> Assigned roles --> click on +add Assignments --> select User administrator role*

---

**Q32.** You have an Azure Active Directory (Azure AD) tenant named contoso.onmicrosoft.com that contains 100 user accounts.
You purchase 10 Azure AD Premium P2 licenses for the tenant.
You need to ensure that 10 users can use all the Azure AD Premium features.

What should you do?
1. From the Licenses blade of Azure AD, assign a license
2. From the Groups blade of each user, invite the users to a group
3. From the Azure AD domain, add an enterprise application
4. From the Directory role blade of each user, modify the directory role

**Ans: 1. From the Licenses blade of Azure AD, assign a license**

*Active Directory-> Manage Section > Choose Licenses -> All Products -> Select Azure Active Directory Premium P2 -> Then assign a user to it*

---

**Q33.** You have an Azure subscription named Subscription1 and an on-premises deployment of Microsoft System Center Service Manager.
Subscription1 contains a virtual machine named VM1.
You need to ensure that an alert is set in Service Manager when the amount of available memory on VM1 is below 10 percent.

What should you do first?
1. Create an automation runbook
2. Deploy a function app
3. Deploy the IT Service Management Connector (ITSM)
4. Create a notification

**Ans: 3. Deploy the IT Service Management Connector (ITSM)**

**Explanation:** The IT Service Management Connector (ITSMC) allows you to connect Azure and a supported IT Service Management (ITSM) product/service, such as the
Microsoft System Center Service Manager.
With ITSMC, you can create work items in ITSM tool, based on your Azure alerts (metric alerts, Activity Log alerts and Log Analytics alerts).

---

**Q34.** You sign up for Azure Active Directory (Azure AD) Premium.
You need to add a user named admin1@contoso.com as an administrator on all the computers that will be joined to the Azure AD domain.

What should you configure in Azure AD?
1. Device settings from the Devices blade
2. Providers from the MFA Server blade
3. User settings from the Users blade
4. General settings from the Groups blade

**Ans: 1. Device settings from the Devices blade**

---

**Q35.** You have an Azure subscription that contains a resource group named RG26.
RG26 is set to the West Europe location and is used to create temporary resources for a project. RG26 contains the resources shown in the following table:

| Name | Type | Location |
| -- | -- | -- |
| VM1 | Virtual Machine | North Europe |
| RGV1 | Recovery Service Vault | North Europe |
| SQLD01 | SQL server in Azure VM | North Europe |
| sa001 | Storage account | West Europe |

SQLDB01 is backed up to RGV1.
When the project is complete, you attempt to delete RG26 from the Azure portal. The deletion fails.
You need to delete RG26.

What should you do first?
1. Delete VM1
2. Stop VM1
3. Stop the backup of SQLDB01
4. Delete sa001

**Ans: 3. Stop the backup of SQLDB01**

---

**Q36.** You have an Azure subscription named Subscription1 that contains a virtual network named VNet1. VNet1 is in a resource group named RG1.
Subscription1 has a user named User1. User1 has the following roles:
- Reader
- Security Admin
- Security Reader
You need to ensure that User1 can assign the Reader role for VNet1 to other users.

What should you do?
1. Remove User1 from the Security Reader and Reader roles for Subscription1
2. Assign User1 the User Access Administrator role for VNet1
3. Assign User1 the Network Contributor role for VNet1
4. Assign User1 the Network Contributor role for RG1

**Ans: 2. Assign User1 the User Access Administrator role for VNet1**

*Has full access to all resources including the right to delegate access to others*

---

**Q37.** You have an Azure Active Directory (Azure AD) tenant named contosocloud.onmicrosoft.com.
Your company has a public DNS zone for contoso.com.
You add contoso.com as a custom domain name to Azure AD.
You need to ensure that Azure can verify the domain name.

Which type of DNS record should you create?
1. MX
2. NSEC
3. PTR
4. RRSIG

**Ans: MX**

*When you add a custom domain in azure you are not allowed to use that unless you prove its your domain. So once you add the custom domain name azure asks you to verify and you have to provide some inputs to verify that its your's. These inputs can be provided in TXT or MX, so its MX in this case*

---

**Q38.** You have an Azure Directory (Azure AD) tenant named Adatum and an Azure Subscription named Subscription1. Adatum contains a group named Developers.
Subscription1 contains a resource group named Dev.
You need to provide the Developers group with the ability to create Azure logic apps in the Dev resource group.

**Solution 1:** On Subscription1, you assign the DevTest Labs User role to the Developers group

**Ans: No**

*DevTest Labs User role only lets you connect, start, restart, and shutdown virtual machines in your Azure DevTest Labs*

**Solution 2:** On Subscription1, you assign the Logic App Operator role to the Developers group

**Ans: No**

**Solution 3:** On Dev, you assign the Contributor role to the Developers group

**Ans: Yes**

*The Contributor role can manage all resources (and add resources) in a Resource Group.*

---

**Q39.** You have an Azure subscription named Subscription1 that contains an Azure Log Analytics workspace named Workspace1.
You need to view the error events from a table named Event.

Which query should you run in Workspace1?
1. Get-Event Event | where {$_.EventType == "error"}
2. search in (Event) "error"
3. select * from Event where EventType == "error"
4. search in (Event) * | where EventType -eq "error"

**Ans: 2. search in (Event) "error"**

*To search a term in a specific table, add the table-name just after the search operator*

---

**Q40.** You have an Azure subscription named Subscription1. Subscription1 contains the resource groups in the following table:

| Name | Azure region | Policy |
| -- | -- | -- |
| RG1 | West Europe | Policy1 |
| RG2 | North Europe | Policy2 |
| RG3 | France Central | Policy3 |

RG1 has a web app named WebApp1. WebApp1 is located in West Europe.
You move WebApp1 to RG2.

What is the effect of the move?
1. The App Service plan for WebApp1 remains in West Europe. Policy2 applies to WebApp1
2. The App Service plan for WebApp1 moves to North Europe. Policy2 applies to WebApp1
3. The App Service plan for WebApp1 remains in West Europe. Policy1 applies to WebApp1
4. The App Service plan for WebApp1 moves to North Europe. Policy1 applies to WebApp1

**Ans: 1. The App Service plan for WebApp1 remains in West Europe. Policy2 applies to WebApp1**

---

**Q41.** You have an Azure subscription.
Users access the resources in the subscription from either home or from customer sites. From home, users must establish a point-to-site VPN to access the Azure resources. The users on the customer sites access the Azure resources by using site-to-site VPNs.
You have a line-of-business-app named App1 that runs on several Azure virtual machine. The virtual machines run Windows Server 2016.
You need to ensure that the connections to App1 are spread across all the virtual machines.

What are two possible Azure services that you can use?
1. an internal load balancer
2. a public load balancer
3. an Azure Content Delivery Network (CDN)
4. Traffic Manager
5. an Azure Application Gateway

**Ans: 1. an internal load balancer, 5. an Azure Application Gateway

---

**Q42.** You have an Azure subscription.
You have 100 Azure virtual machines.
You need to quickly identify underutilized virtual machines that can have their service tier changed to a less expensive offering.

Which blade should you use?
1. Monitor
2. Advisor
3. Metrics
4. Customer insights

**Ans: 2. Advisor**

*Advisor helps you optimize and reduce your overall Azure spend by identifying idle and underutilized resources. You can get cost recommendations from the Cost tab on the Advisor dashboard*

---

**Q43.** You have an Azure Active Directory (Azure AD) tenant named contoso.onmicrosoft.com.
The User administrator role is assigned to a user named Admin1.
An external partner has a Microsoft account that uses the user1@outlook.com sign in.
Admin1 attempts to invite the external partner to sign in to the Azure AD tenant and receives the following error message: 'Unable to invite user user1@outlook.com' " Generic authorization exception.`
You need to ensure that Admin1 can invite the external partner to sign in to the Azure AD tenant.

What should you do?
1. From the Users blade, modify the External collaboration settings
2. From the Custom domain names blade, add a custom domain
3. From the Organizational relationships blade, add an identity provider
4. From the Roles and administrators blade, assign the Security administrator role to Admin1

**Ans: 1. From the Users blade, modify the External collaboration settings**

---

**Q44.** You have an Azure subscription linked to an Azure Active Directory tenant. The tenant includes a user account named User1.
You need to ensure that User1 can assign a policy to the tenant root management group.

What should you do?
1. Assign the Owner role for the Azure Subscription to User1, and then modify the default conditional access policies
2. Assign the Owner role for the Azure subscription to User1, and then instruct User1 to configure access management for Azure resources
3. Assign the Global administrator role to User1, and then instruct User1 to configure access management for Azure resources
4. Create a new management group and delegate User1 as the owner of the new management group

**Ans: **

---

**Q45.** You have an Azure subscription that contains a user named User1.
You need to ensure that User1 can deploy virtual machines and manage virtual networks. The solution must use the principle of least privilege.

Which role-based access control (RBAC) role should you assign to User1?
1. Owner
2. Virtual Machine Contributor
3. Contributor
4. Virtual Machine Administrator Login

**Ans: 3. Contributor**

---

**Q46.** You have an Azure subscription named Subscription1 that contains an Azure virtual machine named VM1. VM1 is in a resource group named RG1.
VM1 runs services that will be used to deploy resources to RG1.
You need to ensure that a service running on VM1 can manage the resources in RG1 by using the identity of VM1.

What should you do first?
1. From the Azure portal, modify the Managed Identity settings of VM1
2. From the Azure portal, modify the Access control (IAM) settings of RG1
3. From the Azure portal, modify the Access control (IAM) settings of VM1
4. From the Azure portal, modify the Policies settings of RG1

**Ans: 1. From the Azure portal, modify the Managed Identity settings of VM1**

---

**Q47.** You have an Azure DNS zone named adatum.com.
You need to delegate a subdomain named research.adatum.com to a different DNS server in Azure.

What should you do?
1. Create an NS record named research in the adatum.com zone.
2. Create a PTR record named research in the adatum.com zone.
3. Modify the SOA record of adatum.com.
4. Create an A record named *.research in the adatum.com zone.

**Ans: 1. Create an NS record named research in the adatum.com zone.**

---
