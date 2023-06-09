---
lab:
    title: 'Exercise: Provide storage for the IT department testing and training        '
    module: 'Guided Project - Azure Files and Azure Blobs'
---

The IT department needs to prototype different storage scenarios and to train new personnel. The content isn't important enough to back up and doesn't need to be restored if the data is overwritten or removed. A simple configuration that can be easily changed is desired.

## Architecture diagram
![Diagram with one storage account](../Media/task_01.png)

## Skilling tasks
- Create a storage account. 
- Configure basic settings for security and networking. 

## Exercise instructions

>**Note**: To complete this lab you will need an [Azure subscription](https://azure.microsoft.com/free/).

1. Create and deploy a resource group to hold all your guided project resources. [Learn more about resource groups](https://learn.microsoft.com/azure/azure-resource-manager/management/manage-resource-groups-portal)
    - In the Azure portal, search for and select **Resource groups**.
    - Select **+ Create**.
    - Give your resource group a **name**. Use this resource group for all project resources.
    - Select a **region**. Use this region throughout the project. 
    - Select **Review and create** to validate the resource group.
    - Select **Create** to deploy the resource group.

1. Create and deploy a storage account to support testing and training. [Learn more about the types of storage accounts](https://learn.microsoft.com/azure/storage/common/storage-account-overview#types-of-storage-accounts)
    - In the Azure portal, search for and select  **Storage accounts**. 
    - Select **+ Create**.
    - On the **Basics** tab, select your **Resource group**.
    - Provide a **Storage account name**.
    - Set the **Performance** to **Standard**. 
    - Select **Review**, and then **Create**. 
    - Wait for the storage account to deploy and then **Go to resource**.  

1. The data in this storage account doesn't require high availability or durability. A lowest cost storage solution is desired. [Learn more about storage account redundancy](https://learn.microsoft.com//azure/storage/common/storage-redundancy)
    - In your storage account, select the **Redundancy** blade.
    - Select **Locally-redundant storage (LRS)** in the **Redundancy** drop-down. 
    - Be sure to **Save** your changes. 
    - Refresh the page and notice the content only exists in the primary data center. 

1. The storage account should only accept requests from secure connections. [Learn more about requiring secure transfer from secure connections](https://learn.microsoft.com/azure/storage/common/storage-require-secure-transfer)
    - In the **Settings** section, select the **Configuration** blade.
    - Ensure **Secure transfer required** is **Enabled**.
    - Be sure to **Save** your changes. 

1. The storage account should use at least TLS version 1.2. [Learn more about transport layer security (TLS)](https://learn.microsoft.com//azure/storage/common/transport-layer-security-configure-minimum-version?tabs=portal)
    - In the **Settings** section, click the **Configuration** blade.
    - Ensure the **Minimal TLS version** is set to **Version 1.2**. 


1. Until the storage is needed again, disable requests to the storage account for both shared keys and shared access signatures. [Learn more about disabling shared keys](https://learn.microsoft.com/azure/storage/common/shared-key-authorization-prevent?tabs=portal#disable-shared-key-authorization)
    - In the **Settings** section, click the **Configuration** blade.
    - Ensure **Allow storage account key access** is **Disabled**. 
    - Be sure to **Save** your changes. 

1. Ensure the storage account allows public access from all networks.  
    - In the **Security + networking** section, click the **Networking** blade.
    - Ensure **Public network access** is set to **Enabled from all networks**.
    - Be sure to **Save** your changes. 

>**Note**: For additional practice complete the [Create an Azure Storage Account](https://learn.microsoft.com/training/modules/create-azure-storage-account/) module. The module has a sandbox where you can practice creating a storage account.
