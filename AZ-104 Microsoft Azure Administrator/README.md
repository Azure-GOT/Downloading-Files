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
