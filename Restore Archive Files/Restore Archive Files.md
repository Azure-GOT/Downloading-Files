# Restore Archive Files

While a blob is in the Archive access tier, it's considered to be offline and can't be read or modified. In order to read or 
modify data in an archived blob, you must first rehydrate the blob to an online tier, either the Hot or Cool tier. There are 
two options for rehydrating a blob that is stored in the Archive tier:
- Copy an archived blob to an online tier
- Change a blob's access tier to an online tier

1. Copy an archived blob to an online tier

> Note: Replace placeholders in angle brackets with your own values
Azure CLI:

    az storage blob copy start \
    --source-container <source-container> \
    --source-blob <source-blob> \
    --destination-container <dest-container> \
    --destination-blob <dest-blob> \
    --account-name <storage-account> \
    --tier hot \
    --rehydrate-priority standard \
    --auth-mode login

Powershell:

    # Initialize these variables with your values.
    $rgName = "<resource-group>"
    $accountName = "<storage-account>"
    $srcContainerName = "<source-container>"
    $destContainerName = "<dest-container>"
    $srcBlobName = "<source-blob>"
    $destBlobName = "<dest-blob>"

    # Get the storage account context
    $ctx = (Get-AzStorageAccount `
            -ResourceGroupName $rgName `
            -Name $accountName).Context

    # Copy the source blob to a new destination blob in Hot tier with Standard priority.
    Start-AzStorageBlobCopy -SrcContainer $srcContainerName `
        -SrcBlob $srcBlobName `
        -DestContainer $destContainerName `
        -DestBlob $destBlobName `
        -StandardBlobTier Hot `
        -RehydratePriority Standard `
        -Context $ctx

2. Change a blob's access tier to an online tier

Azure CLI:

    az storage blob set-tier \
        --account-name <storage-account> \
        --container-name <container> \
        --name <archived-blob> \
        --tier Hot \
        --rehydrate-priority Standard \
        --auth-mode login

Powershell: 

    # Initialize these variables with your values.
    $rgName = "<resource-group>"
    $accountName = "<storage-account>"
    $containerName = "<container>"
    $blobName = "<archived-blob>"

    # Get the storage account context
    $ctx = (Get-AzStorageAccount `
            -ResourceGroupName $rgName `
            -Name $accountName).Context

    # Change the blob's access tier to Hot with Standard priority.
    $blob = Get-AzStorageBlob -Container $containerName -Blob $blobName -Context $ctx
    $blob.BlobClient.SetAccessTier("Hot", $null, "Standard")

From the portal:

- Select the blob that you want to restore
- In the top menu click on **Change Tier**
- Select the **Access tier** as *Hot* or *Cool*
- Select the rehydrate property as *Standard* or *High(will cost more)*
> Note: Rehydrating a blob from Archive to Hot or Cool may take several hours to complete.
- Click on **Save**


Once the rehydration process is complete you can download the file.

For reference: https://docs.microsoft.com/en-in/azure/storage/blobs/archive-rehydrate-to-online-tier?tabs=azure-portal
