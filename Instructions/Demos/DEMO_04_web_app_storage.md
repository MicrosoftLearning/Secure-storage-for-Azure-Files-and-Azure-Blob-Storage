---
demo:
    title: 'Demonstration 04: Create and configure encryption and secure app access'
    module: 'Guided Project - Azure Files and Azure Blobs'
--- 

## Demonstration - Create and configure encryption and secure app access. 

In this demonstration, explore encryption and app security.

> **Note:** In this demonstration you will create a managed identity, key vault, and key. To save time you may want to pre-create these resources. 

## Create a key vault, key, and a managed identity.

1. Create a new Azure storage account. This will be used to show secure storage features.

1. [Supporting Slide] Before beginning, review how the new developer app must securely access the storage it needs. The app is accessed by a managed identity. The managed identity uses an encryption key that is stored in the Azure Key Vault. The Azure Key Vault is a cloud service used to manage keys, secrets, and certificates. This process replaces the need to store security information in the app code.  Not all students may be familiar with these concepts.

1. Create a **managed identity**. Learn more, [Managed identities](https://learn.microsoft.com/en-us/azure/active-directory/managed-identities-azure-resources/overview).

1. Create a **key vault**. Take the defaults, **except** on the **Access configuration** tab, ensure **Vault access policy** is selected. Learn more, [Azure key vault](https://learn.microsoft.com/azure/active-directory/managed-identities-azure-resources/overview).

1. Wait for the key vault to deploy then **Go to resource**.

1. In the **Objects** blade, point out the **Keys, Secrets, and Certificates**.

1. Select **Keys** and then **Generate/Import**.

1. Give the key a **name** and then **Create** the key. Take the defaults.

## Configure the storage account for the managed identity and the key vault, assign permissions.

1. Return to the storage account.

1. In the **Security + networking** blade, select **Encryption**.

    - Select **Customer-managed keys**. Discuss the difference between a Microsoft-managed key and customer-managed keys. For example, a Microsoft-managed key is used for automatic storage encryption and decryption. A customer-managed key could be used by an app. Learn more, [Customer-managed keys](https://learn.microsoft.com/azure/storage/common/customer-managed-keys-overview).

    - For **key store type** select **key vault**. Keys can be stored in software (key vault) or in hardware (hardware security module). We are using the key vault.

    - Select your **key vault** and **key**.

    - For **identity type** select a **system-assigned managed identity**. This is the default that configures the managed identity so it can access the key vault.

1. [Supporting Slide] At this point you have given the managed identity access to the key vault and associated the identity with the storage account. Now, we need to give the managed identity access to the storage account. Learn more, [Azure role assignments](https://learn.microsoft.com/azure/role-based-access-control/role-assignments).

1. Return to your storage account and select **Access control (IAM)**. Learn more, [Azure built-in roles](https://learn.microsoft.com/azure/role-based-access-control/built-in-roles).

    - Select **Add** and then **Add role assignment**. On the **Assignment type** tab, point out we are assigning a job position role.

    - Move to the **Role** tab and search for **blob**. Select the **Storage blob data reader** role.

    - Move to the **Members** tab and assign access to the **Managed identity.**

    - Select **Select members** and select your **user-assigned managed identity**.

## Configure immutable storage.

1. [Supporting Slide] The developers need to way to store business-critical data that can't be modified for deleted for a user-specified time. Immutable storage lets you protect your data from being overwritten or deleted. Discuss time-based retention policies and legal-hold policies. Learn more, [Immutable storage](https://learn.microsoft.com/azure/storage/blobs/immutable-storage-overview).

1. In your **storage account**, select the **Container** blade.

1. **Create** a container called **hold** and **upload** a file.

1. Access your **hold**container and select the **Access policy** blade.

1. In the **Immutable blob storage** section, select **+ Add policy**.

1. For the **Policy type** select **Time-based retention**.

1. Set the **Retention period** to **5** days.

1. Be sure to **Save** your changes.

1. Try to remove the file from the container.

1. Verify you cannot delete the file due to policy.

## Configure an encryption scope for infrastructure encryption.

1. The developers also need to scope infrastructure encryption at the container level. Discuss encryption scopes and infrastructure encryption. Learn more, [Encryption scopes](https://learn.microsoft.com/azure/storage/blobs/encryption-scope-overview).

1. Continue in the **storage account**.

1. In the **Security + networking** section, select **Encryption**.

1. Move to the **Encryption scope** tab and select **+ Add**.

1. Give your **encryption scope** a **name**.

1. Ensure **Infrastructure encryption** is **Enabled**. Point out the note, "This option cannot be changed after this encryption scope is created."

>**Note**: Students should now be able to compleate LAB_04. 
