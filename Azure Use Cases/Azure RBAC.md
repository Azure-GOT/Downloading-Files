# Azure Role-Based Access Control(RBAC)

Follow this steps to see what roles are assigned at resource group scope

<ul>
  <li>Select the <b>Resource Group</b> that you want and on the left menu select <b>Access control(IAM)</b></li>
  
  <li>From this you can see <b>Role assignments</b>, this will show who has access to the resouce group.</li>
  <img src="Images/">
  
  <li>From the <b>Roles</b> tab, you can see all built-in and custom roles</li>
  <img src="Images/">
</ul>

Suppose the user need permission to create and manage virtual machines, we can provide the <b>Virtual Machine Contributor</b> role for a resource group to that user.

<ul>
  <li>Follow this procedure to assign the <b>Virtual Machine Contributor</b> role for a resource group</li>
  
  <li>Select the resource group, under that from the left menu select <b>Access control(IAM)</b></li>
  
  <li>From the Role assignment tab, select <b>Add role assignment</b></li>
  <img src="Images/">
  
  <li>Add role assignment pane will open.</li>
  
  <li>In the <b>Role</b> drop-down list select <b>Virtual Machine Contributor</b>. In the <b>Select</b> list select user that you want to give access and click Save.</li>
  <img src="Images/">
  
  <li>The new role will be assign at the resouce group scope</li>
  <img src="Images/">
  
  <li>If you want to remove the access, select the role assignment and click on <b>Remove</b> from the top menu</li>
  <img src="Images/">
</ul>






