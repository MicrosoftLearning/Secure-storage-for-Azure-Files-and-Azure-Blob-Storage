---
demo:
    title: 'Demonstration 03: Create and configure files and storage networking'
    module: 'Guided Project - Azure Files and Azure Blobs'
--- 

## Demonstration - Create and configure files and storage networking.

In this demonstration, explore Azure Files storage and storage networking.

> **Note:** In this demo you will create a new storage account, and a virtual network with subnet. These can be pre-created to save time. 

## Review Azure Files and create a storage account specifically for file shares.

1. [Supporting Slide] Before beginning the demonstration, discuss what Azure File storage is and how it is different from Azure blob storage. Learn more, [Scenarios for Azure Storage](https://learn.microsoft.com/azure/storage/common/storage-introduction).

1. Access the **Azure portal**.

1. Create a **new** Azure storage account. This account will be used to address the shared files requirements.

1. [Supporting Slide] For **Performance** select **Premium**. 

1. For **Premium account type** select **File shares**. Premium file shares are for enterprise or high-performance file share applications. Our scenario requirement is for a corporate file share. 

1. For **Redundancy** select **Zone-redundant** storage. Remind students this is recommended for high availability scenarios and protects against datacenter failures.

1. Move to the **Data protection** tab.

1. Point out that **Enable soft delete for file shares** is **enabled**.

1. **Review** the storage account and then **Create**.

## Configure the file share.

1. Continue in the storage account.

1. In the **Data storage** blade, select **File shares**.

1. Select **File share** and give the file share a name, **finance**.

1. Discuss **Provisioned capacity** and how a premium file share is billed by provisioned file size, regardless of the used capacity. As you have time, discuss other settings. 

1. Discuss **Protocol**, select **SMB**.

1. Select **Create**.

## Configure the file share settings and create a snapshot.

1. Select the **finance** file share.

1. Review the settings at the top of the page. For example, **Upload** and **Change size and performance**.

1. [Supporting Slide] Discuss the purpose of snapshots. Learn more, [File share snapshots](https://learn.microsoft.com/azure/storage/files/storage-snapshots-files).

1. In the **Operations** blade, select **Snapshots**.

1. Select **Add snapshot** and select **OK**. Adding a comment is optional.

1. Students will upload, snapshot, and restore files in the lab.

## Configure network access for storage.

1. [Supporting Slide] Before configuring storage networking, discuss the various options. Review some of the previous networking options that have configured. 

1. Search the portal for **virtual networks.**

1. Use the **Basics** tab to create a virtual network named **corpnet**. Create a **subnet**, **finance**. Point out this network would already be created.

1. Return to the storage account.

1. In the **Security + networking** blade, select **Networking**.

1. Select **Enabled from selected virtual networks and IP addresses**.

1. In the **Add network** page, add the **corpnet** virtual network and **finance** subnet.

1. **Enable the endpoint**. Explain that a new service endpoint may take up to 15 minutes to create.

1. Review the **Firewall** settings.

1. Review the **Network Routing** section, and that Microsoft network routing is being used.



1. As you have time, give a quick demonstration of the **Storage browser**. 

>**Note**: Students should now be able to complete LAB_03. 
