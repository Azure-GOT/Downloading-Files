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

**Q.** Your company has an azure subscription that includes a storage account, a resource group, a blob container and a file share.
A colleague named Jon Ross makes use of a solitary Azure Resource Manager (ARM) template to deploy a virtual machine and an additional Azure Storage account.
You want to review the ARM template that was used by Jon Ross.

**Solution 1:** You access the Virtual Machine blade.

**Ans: No**

**Solution 2:** You access the Resource Group blade.

**Ans: Yes**

**Solution 3:** You access the Container blade.

**Ans: No**

---

**Q.** Your company has an Azure Active Directory (Azure AD) tenant named weyland.com that is configured for hybrid coexistence with the on-premises Active
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

**Q.** Your company makes use of Multi-Factor Authentication for when users are not in the office. The Per Authentication option has been configured as the usage model.
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


**Q.** Consider the scenario: Your company has an Azure Active Directory (Azure AD) subscription.
You want to implement an Azure AD conditional access policy.
The policy must be configured to require members of the Global Administrators group to use Multi-Factor Authentication and an Azure AD-joined device when they connect to Azure AD from untrusted locations.

**Solution 1:** You access the multi-factor authentication page to alter the user settings

**Ans: No**

**Solution 2:** You access the Azure portal to alter the session control of the Azure AD conditional access policy

**Ans: No**

**Solution 3:** You access the Azure portal to alter the grant control of the Azure AD conditional access policy

**Ans: Yes**

---

**Q.** 
