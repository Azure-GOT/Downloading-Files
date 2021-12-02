# Cases that need to be considered for reducing the azure resource cost 

- **Backup** 
  - **Back up the data incrementally :** The data we are backing up is bound to grow over time. This backup costs fortune for cloud storage and data transfer. This can be done by 
 storing incremental backups. First you need to perform a full backup, once the full backup is made, every consecutive backup contains only the changes made to the original 
 backup. Since the backup isn’t done very often and only the new changes are backed up, organizations don’t have to pay for large cloud data transfers. These changes or 
 increments can then be reflected on the previous full backup if the need for the backup arises. 
  - **Exclude Swap Files or Partitions :** Sometimes, the RAM of a VM may not be enough to store the applications and OS data. In this case, the OS occupies some part of the hard 
  disc to store additional data. This data is referred to as a swap file or swap partition in Windows and Linux, respectively.<br>
  The swap files are generally 1.5 times the size of the RAM. And, the data in these files change regularly. This means that every time a backup takes place, 
  these files are backed up as well. However, this data is of no relevance to the backup. Therefore, these files should be excluded from the backup. These files can get 
  really large as they keep changing after every backup job requiring even more space in the cloud. The point is to backup what you need, and leave out non-essentials like 
  the swap memory of a VM.


- **VM Resizing**
  - If you are provisioning machines that offer more than what you need, then you’re paying for compute you don’t use. By reviewing the performance over time, we can determine 
  that the virtual machine is not in that much of use and we can resize the VM to lower size.


- **Disk**
  - Make sure to select the right disk for the machine, default is Premium SSD – the most expensive option. For non-production environments and for production servers that 
    don't need high performance SSD, change to a disk with a lower cost. You can also delete the disks that are unused means when we delete the virtual machine the disks associated to that VM are not deleted automatically, which leaves behind as orphaned disks. For deleting such disks perform the following steps:(for managed disks)
    1. From Azure portal search for disks
    2. When the search is complete you’ll see a list of all your disks. Look for any disks that do not have an owner listed.
    3. Select one of the disks without an owner. Check the "Disk state” in the overview tab to make sure that the disk is unattached. If it is, go ahead and click “Delete.”

- **Licences**
  - If we have our own Windows Server or SQL Server license we can use those Licences and we can save upto 40% of the cost. When you provide your own license, Azure doesn't have 
  to assign you one and you save costs. With this benefit, for each license it will cover the cost of the OS, while we just pay for base compute costs.
  
- **Auto Shutdown**
  - When we enable the Auto-Shutdown feature, we can tell it to shutdown the VM at a certain time every day and send a notification when that happened. This deallocates the VM 
  resources and makes the VM only incur minimal costs.
  
- **Azure Reserved Instance**
  - Reserved instances are for purchasing one-year or three-year term Azure Reseved instances with a single, upfront payment and it could save you up to 72% of the VM 
    cost – along with Azure Hybrid Benefit it can save even up to 80%. The prices for Reserved VM Instances are significantly lower than non-reserved instances and so anytime 
    there is a need to have long running VMs then you should opt to use Azure Reserved Instances to gain cost savings.
    
- **Different rigions**
  - Deploying the virtual machines into a different region can save money, various Azure regions are cheaper than others for VM deployments. If you are not required for data 
    compliance etc to have your VMs in a specific region(s) then looking at another region is a viable option in relation to cost saving.<br>
    Look at the following example:
    | Region | Virtual Machine | Per hour cost | Monthly cost (730 hours) |
    | -- | -- | -- | -- |
    | UK South | DS3v2 | £0.3135 | £228.85 |
    | East US | DS3v2 | €0.2617 | £191.04 |

- **Orphaned Resources**
  - Orphaned resources occur when a VM is terminated, but resources attached to that machine continue running or existing – which incurs wasted costs. 
    Make sure you look out for Orphaned Volumes (Azure Virtual Disks), Unassociated IPs (Static Public IPs) and either terminate or reassign them. When VMs are deleted, the disks are not deleted automatically, which leaves behind as orphaned disks. These orphaned disks take up space and incur charges that most Azure users don’t even know they’re paying.

