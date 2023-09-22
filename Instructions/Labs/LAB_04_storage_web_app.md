---
lab:
    title: 'Exercise 04: Provide storage for a new company app'
    module: 'Guided Project - Azure Files and Azure Blobs'
---
The company is designing and developing a new app. Developers need to ensure the storage is only accessed using keys and managed identities. The developers would like to use role-based access control. To help with testing, protected immutable storage is needed. 

## Architecture diagram

![Diagram with a storage account, managed identities, and a key vault.](../Media/task-5.png)

## Skilling tasks

- Create the storage account and managed identity.
- Secure access to the storage account with a key vault and key.
- Configure the storage account to use the customer managed key in the key vault
- Configure an time-based retention policy and an encryption scope.

## Exercise instructions

## Create the storage account and managed identity

1. Provide a storage account for the web app. 
    - In the portal, search for and select **Storage accounts**. 
    - Select **+ Create**.
    - For **Resource group** select **Create new**. Give your resource group a **name** and select **OK** to save your changes.
    - Provide a **Storage account name**. Ensure the name is unique and meets the naming requirements. 
    - **Review**, and then **Create** the storage account.
    - Wait for the resource to deploy.

1. Provide a managed identity for the web app to use.  Learn more about [managed identities](https://learn.microsoft.com/azure/active-directory/managed-identities-azure-resources/overview).

    - Search for and select **Managed identities**.
    - Select **Create**.
        - Select your **resource group**. 
        - Give your managed identity a name.
    - Select **Review and create**, and then **Create**. 

1. Assign the correct permissions to the managed identity. The identity only needs to read and list containers and blobs. Learn more about [how to assign Azure roles](https://learn.microsoft.com/azure/role-based-access-control/role-assignments-portal).
    
    - Search for and select your **storage account**.
    - Select the **Access Control (IAM)** blade.
    - Select **Add role assignment** (center of the page).
    - On the **Job functions roles** page, search for and select the **Storage Blob Data Reader** role. 
    - On the **Members** page, select **Managed identity**.
    - Select **Select members**, in the **Managed identity** drop-down select **User-assigned managed identity**.
    - Select the managed identity you created in the previous step. 
    - Click **Select** and then **Review + assign** the role. 
    - Select **Review + assign** a second time to add the role assignment.
    - Your storage account can now be accessed by a managed identity with the Storage Data Blob Reader permissions. 

## Secure access to the storage account with a key vault and key

1. To create the key vault and key needed for this part of the lab, your user account must have Key Vault Administrator permissions. Learn more about how to [provide access to Key Vault keys, certificates, and secrets with an Azure role-based access control](https://learn.microsoft.com/azure/key-vault/general/rbac-guide?tabs=azure-cli)
    - In the portal, search for and select **Resource groups**. 
    - Select your **resource group**, and then the **Access Control (IAM)** blade.
    - Select **Add role assignment** (center of the page).
    - On the **Job functions roles** page, search for and select the **Key Vault Administrator** role.
    - On the **Members** page, select **User, group, or service principal**.
    - Select **Select members**.
    - Search for and select your user account. Your user account is shown in the top right of the portal.
    - Click **Select** and then **Review + assign**.
    - Select **Review + assign** a second time to add the role assignment.
    - You are now ready to continue with the lab.

1. Create a key vault to store the access keys. 

    - In the portal, search for and select **Key vaults**.
    - Select **Create**.
    - Select your **resource group**.
    - Provide the **name** for the key vault. The name must be unique. 
    - Select **Review + create**.
    - Wait for the validation checks to complete and then select **Create**.
    - After the deployment, select **Go to resource**.
    - On the **Overview** blade ensure both **Soft-delete** and **Purge protection** are **enabled**. 

1. Create a customer-managed key in the key vault. 

    - In your **key vault**, in the **Objects** section, select the **Keys** blade.
    - Select **Generate/Import** and **Name** the key.
    - Take the defaults for the rest of the parameters, and **Create** the key.

## Configure the storage account to use the customer managed key in the key vault

1. Before you can complete the next steps, you must assign the Key Vault Crypto Service Encryption User role to the managed identity. Learn more about how to [use a system-assigned managed identity to authorize access](https://learn.microsoft.com/azure/storage/common/customer-managed-keys-configure-existing-account?tabs=azure-portal#use-a-system-assigned-managed-identity-to-authorize-access)
    - In the portal, search for and select **Resource groups**. 
    - Select your **resource group**, and then the **Access Control (IAM)** blade.
    - Select **Add role assignment** (center of the page).
    - On the **Job functions roles** page, search for and select the **Key Vault Crypto Service Encryption User** role.
    - On the **Members** page, select **Managed identity**.
    - Select **Select members**, in the **Managed identity** drop-down select **User-assigned managed identity**.
    - Select your managed identity.  
    - Click **Select** and then **Review + assign**.
    - Select **Review + assign** a second time to add the role assignment.
    
1. Configure the storage account to use the customer managed key in your key vault. Learn more about [customer managed keys on an existing storage account](https://learn.microsoft.com/azure/storage/common/customer-managed-keys-configure-existing-account?WT.mc_id=Portal-Microsoft_Azure_Storage&tabs=azure-portal).
    - Return to your the storage account.
    - In the **Security + networking** section, selet the **Encryption** blade.
    - Select **Customer-managed keys**.
    - **Select a key vault and key**. Select your key vault and key.
    - **Select** to confirm your choices. 
    - Ensure the **Identity type** is **User-assigned**.
    - **Select an identity**.
    - Select your managed identity then select **Add**. 
    - **Save** your changes.
    - If you receive an error that your identity does not have the correct permissions, wait a minute and try again. 

## Configure an time-based retention policy and an encryption scope.

1. The developers require a storage container where files can't be modified, even by the administrator. Learn more about [blob immutable storage](https://learn.microsoft.com/azure/storage/blobs/immutable-storage-overview).

    - Navigate to your **storage account**.
    - In the **Data storage** section, select the **Containers** blade. 
    - Create a container called **hold**. Take the defaults. Be sure to **Create** the container. 
    - Upload a file to the container. 
    - In the **Settings** section, select the **Access policy** blade. 
    - In the **Immutable blob storage** section, select **+ Add policy**. 
    - For the **Policy type**, select **time-based retention**. 
    - Set the **Retention period** to **5** days. 
    - Be sure to **Save** your changes. 
    - Try to **delete** the file in the container. 
    - Verify you are notified **failed to delete blobs** due to policy.  

1. The developers require an encryption scope that enables infrastructure encryption. Learn more about [infrastructure encryption](https://learn.microsoft.com/azure/storage/common/infrastructure-encryption-enable?tabs=portal).

    - Navigate back to your storage account. 
    - In the **Security + networking** blade, select **Encryption**.
    - In the **Encryption scopes** tab, select **Add**.
    - Give your encryption scope a **name**. 
    - The **Encryption type** is **Microsoft-managed key**.
    - Set **Infrastructure encryption** to **Enable**.
    - Notice the warning that enabling infrastructure encryption can not be changed after the scope is created.
    - **Create** the encryption scope.
    - Return to your storage account and create a new container.
    - Notice on the **New container** page, there is the **Name** and **Public access level**.
    - Notice in the **Advanced** section you can select the **Encryption scope** you created and apply it to all blobs in the container. 


>**Note**: For additional practice complete the [Secure and isolate access to Azure resources by using network security groups and service endpoints](https://learn.microsoft.com/training/modules/secure-and-isolate-with-nsg-and-service-endpoints/) module. The module has a sandbox where you can get more practice restricting access to storage.
