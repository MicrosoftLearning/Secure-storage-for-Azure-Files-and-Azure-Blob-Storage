---
demo:
    title: 'Demonstration: Create and configure storage accounts'
    module: 'Guided Project - Azure Files and Azure Blobs'
---
## Demonstration – Create and configure storage accounts 

In this demonstration, we will explore storage accounts.

1. [Supporting Slide] Before beginning this demonstration you may want to discuss how storage is organized and factors to consider. 

1. Access the **Azure portal**.

1. In the search box, type **Storage Accounts**. As you begin typing, the list filters based on your input.

1. Select **Storage Accounts**.

1. Click **Create**.

1. Explain how the Azure portal provides an easy-to-use wizard interface. Remind the students that items marked with a red asterisk are required.

1. Select the **subscription**.

1. Select the **resource group**.

1. Enter a name for your storage account. Discuss the storage account naming restrictions.

1. [Supporting Slide] Select a region for your storage account. Learn more about [Azure geographies](https://azure.microsoft.com/explore/global-infrastructure/geographies/).

1. [Supporting Slide] Select the **standard** performance. Learn more, [Types of storage accounts](https://learn.microsoft.com/azure/storage/common/storage-account-overview).

1. [Supporting Slide] Select **Redundancy** as **Locally-redundant** storage. Learn more, [Azure storage redundancy](https://docs.microsoft.com/azure/storage/common/storage-redundancy).

1. Move to the **Advanced** tab. In the **Security** section highlight these settings. Note we are only covering a few things to get the student started on their first lab. 

    - **Require secure transfer for REST API operations**. By default, storage account requests are only accepted from secure connection. Learn more, [Secure transfer](https://learn.microsoft.com/azure/storage/common/storage-require-secure-transfer).

    - **Enable storage account key access**. Discuss how this setting can disable access to the storage account. For example, access to the IT department storage account could be disabled. Discuss the importance of protecting the key. Learn more, [Manage storage account access keys](https://learn.microsoft.com/azure/storage/common/storage-account-keys-manage?tabs=azure-portal).

    - **Minimum TLS version**. Explain that Transport Layer Service is for securing communications over the network. TLS is an improved version of SSL. Your developers may ask you what versions are available. Learn more, [Transport Layer Service](https://learn.microsoft.com/azure/storage/common/transport-layer-security-configure-minimum-version).

1. Explain that other tabs will be covered as students go through the labs.

1. Click **Review** and ensure there are no validation errors. Discuss possible validation errors. 

1. Click **Create** and wait while the storage account is deployed. Point out the notification messages.

1. Show how to **Go to the resource**. Discuss other ways of getting to the resource.

>**Note**: Students should now be able to complete LAB_01.
