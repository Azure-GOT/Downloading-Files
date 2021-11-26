## Step: Resize the Virtual Machine

- Navigate to the Virtual Machine that we found from the log queries
- First **Stop** the Virtual Machine
  <img src="Images/Stop the VM.png">
- Under **Settings** section, go to **Size**
- Select the size of the Virtual Machine, which has less number of vCPUs, RAM so the cost should be less compared to others.
> Note: If the virtual machine is in running state, changing the size will cause it to be restarted.
- Click on **Resize**, once you selected the desired size for virtual machine
  <img src="Images/Resize VM.png">

---

### Reduce the size of Data disk

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


- Go to the Virtual machine and under **Settings** section click on **Disks**. 
- Click on **+ Create and attach a new disk**, provide the required details and click on **Save**. New data disk will be added to the virtual machine
<img src="Images/Data disk- add new one.png">

- Connect to the Virtal machine via **RDP** and search for **Disk Management**
<img src="Images/Data disk-disk management.png">

- We have to create new simple volume to the unallocated disk.Right click on the unallocated disk and select **New Simple Volume**. New window will appear, accept all the default values and keep clicking on **Next** until the **Finish** option.
<img src="Images/Data disk-new simple volume.png">

- You will now see the new volumes in the **Disk Management**
<img src="Images/Data disk-simple volume completed.png">

- Copy all the data from the old disk to the new smaller size disk. After completing go to the Azure Portal and from the Disk blade remove the old disk by clicking on the **Cross** button in front of the disk.
<img src="Images/Data disk-remove old disk.png">

- Click on **Save** once the old disk is removed.
<img src="Images/Data disk-sava changes.png">

- You can check the applied changes from the disk management in the virtual machine as well
<img src="Images/Data disk-Verify changes.png">
