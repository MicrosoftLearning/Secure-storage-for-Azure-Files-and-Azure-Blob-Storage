---
lab:
    title: 'Exercise: Provide storage for the IT department testing and training'
    module: 'Guided Project - Azure Files and Azure Blobs'
---

The company is geographically dispersed with offices in different locations.  These offices need a way to share files and disseminate information. For example, the Finance department needs to confirm cost information for auditing and compliance. This file shares should be easy to access and load without delay. Some content should only be accessed from selected corporate virtual networks.


## Architecture diagram

![Diagram with a storage account, file share, and directory](../Media/task_04.png)

## Skilling tasks
- Create a storage account. 
- Configure a file share and directory. 
- Configure snapshots and practice restoring files. 
- Restrict access to a specific virtual network and subnet. 

## Exercise instructions

>**Note**: To complete this lab you will need an [Azure subscription](https://azure.microsoft.com/free/).

1. Create a storage account for the finance department's shared files.  [Learn more about storage accounts for Azure Files deployments](https://learn.microsoft.com/azure/storage/files/storage-files-planning#management-concepts)

    - Search the portal for **Storage accounts**. 
    - Click **+ Create**. 
    - Provide a name for the storage account. 
    - Set the **Performance** to **Standard**.  
    - Set the **Redundancy** to **Geo-redundant storage**.
    - Click **Review** and then **Create** the storage account.
    - Wait for the resource to deploy. 

1. Create a general purpose file share for the corporate office. [Learn more about Azure File tiers](https://learn.microsoft.com/azure/storage/files/storage-files-planning#storage-tiers)

    - Select the storage account, and then under **Data storage**, select the **File shares** blade. 
    - Click **+ File share** and provide a **Name**.
    - For the **Tier** choose **Hot**. 
    - Click **Create**. 


1. Add a directory to the file share for the finance department. For future testing, upload a file. 

    - Select your file share and click **+ Add directory**. 
    - Name the new directory **finance**.
    - Browse to the new **finance directory** and add a file to it. 

1. Similar to blob storage, you need to protect against accidental deletion of files. You decide to use snapshots. [Learn more about file snapshots](https://learn.microsoft.com/azure/storage/files/storage-snapshots-files)
    
    - Select your file share and then select the **Snapshots** blade. 
    - Click **+ Add snapshot** and add an optional comment. 
    - Select your uploaded file and in the **Properties** pane click **Delete**.
    - Select the **Snapshot** blade and then click your snapshot. 
    - Navigate to the file you want to restore,
    - Select the file and click **Restore**.
    - Confirm the file has been restored. 

1. The corporate file server is in a separate virtual network. This storage should only be accessed from virtual machines in that network. [Learn more about using private storage endpoints.](https://learn.microsoft.com/azure/storage/common/storage-private-endpoints)

    - Search for and select **Virtual networks**.
        - Click **Create**. Give the virtual network a **name** and select your resource group. 
        - Take the defaults for other parameters, click **Create and review** and wait for the resource to deploy. 
    - Navigate to your virtual network, and then the **Subnets** blade.
        - Select the **default** subnet and then **Service endpoints** and **Services**.
        - Select the **Microsoft.Storage** option.     
        - Don't forget to **Save** your changes. 
    - Return to your files storage account. 
    - Select the **Networking** blade and the **Firewalls and virtual networks** tab. 
        - Change the **Public network access** to **Enabled from selected virtual networks and IP addresses**.
        - In the **Virtual networks** section, click **Add existing virtual network**.
        - **Add** your virtual network and the default subnet. 
        - Be sure to **Save** your changes. 
    - Select the **Storage browser** and navigate to your file share. 
    - Verify the message *not authorized to perform this operation*. 


>**Note**: For additional practice complete the [Configure Azure storage security](https://learn.microsoft.com/training/modules/configure-storage-security/) module. The module has an interactive lab simulation where you can get more practice creating secure storage. 
