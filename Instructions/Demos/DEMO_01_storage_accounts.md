---
demo:
    title: 'Demonstrations: Create and Configure Storage Accounts'
    module: 'Guided Project - Azure Files and Azure Blobs'
---
## Demonstration – Create and Configure Storage Accounts

In this demonstration, we will explore storage accounts.

1. Before beginning this demonstration you may want to discuss factors for determining the number of storage accounts needed. There is a slide for this. 

1. Access the Azure portal.

1. In the search box, type **Storage Accounts**. As you begin typing, the list filters based on your input.

1. Select **Storage Accounts**.

1. Click **Create**.

1. Discuss how the Azure portal provides an easy-to-use interface. Remind the students that items marked with a red asterisk are required.

1. Select the available **subscription**.

1. Select the available **resource group**.

1. Enter a name for your storage account. Discuss the storage account naming restrictions.

1. Select a region for your storage account. There is a slide to discuss regions. Learn more about [Azure geographies](https://azure.microsoft.com/explore/global-infrastructure/geographies/).

1. Select the **standard** performance. There is a slide to highlight the differences between Standard and Premium. Learn more, [Types of storage accounts](https://learn.microsoft.com/azure/storage/common/storage-account-overview).

1. Select **Redundancy** as **Locally-redundant** storage. There is a slide to review [Azure storage redundancy](https://docs.microsoft.com/azure/storage/common/storage-redundancy).

1. Move to the **Advanced** tab. In the **Security** section highlight these settings. Note we are only covering a few things to get the student started on their first lab. 

    - **Require secure transfer for REST API operations**. By default, storage account requests are only accepted from secure connection. Learn more, [Secure transfer](https://learn.microsoft.com/azure/storage/common/storage-require-secure-transfer).

    - **Enable storage account key access**. Discuss how this setting can disable access to the storage account. For example, access to the IT department storage account could be disabled. Discuss the importance of protecting the key. Learn more, [Manage storage account access keys](https://learn.microsoft.com/azure/storage/common/storage-account-keys-manage?tabs=azure-portal).

    - **Minimum TLS version**. Explain that Transport Layer Service is for securing communications over the network. TLS is an improved version of SSL. Your developers may ask you what versions are available. Learn more, [Transport Layer Service](https://learn.microsoft.com/azure/storage/common/transport-layer-security-configure-minimum-version).

1. Explain that other tabs will be covered as you go through the labs.

1. Click **Review** and ensure there are no validation errors. Discuss possible validation errors. 

1. Click **Create** and wait while the storage account is deployed. Point out the notification messages.

1. Show how to **Go to the resource**. 

  
