## Step: Resize the Virtual Machine

- Navigate to the Virtual Machine that we found from the log queries
- First **Stop** the Virtual Machine
  <img src="Images/Stop the VM.png">
- Under **Settings** section, go to **Size**
- Select the size of the Virtual Machine, which has less number of vCPUs, RAM so the cost should be less compared to others.
> Note: If the virtual machine is in running state, changing the size will cause it to be restarted.
- Click on **Resize**, once you selected the desired size for virtual machine
  <img src="Images/Resize VM.png">


**Reduce the size of Data disk**

1. Created a new, smaller disk
2. Attached it to the VM, including creating a partition in the OS, and so forth
3. Copy everything from the original data disk to the new one
4. Detached the old disk from the VM
5. Assigned the drive letter of the old disk (and its only partition) to the new one, and named the new like the 
old (partition label)
6. Deleted the old disk
> Note: This is not capable for OS disks.
and also when we are detaching a disk from a VM having replication (disaster recovery) enabled, we can't do it via the portal,
even having the VM deallocated. But the disk can be detach using Azure CLI while the VM was 
deallocated:
az vm disk detach -g resource_group_name --vm-name vm_name --name disk_name
