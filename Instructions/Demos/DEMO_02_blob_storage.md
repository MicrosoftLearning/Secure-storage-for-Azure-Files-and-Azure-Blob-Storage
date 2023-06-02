---
demo:
    title: 'Demonstration: Create and configure blob storage'
    module: 'Guided Project - Azure Files and Azure Blobs'
---


## Demonstration - Create and configure blob storage.

In this demonstration, we will explore blob storage.

## Review blob storage settings

1. [Slide] Before beginning the demonstration, review blob storage uses and organization. Which of our business groups will need blob storage?

1. Access the Azure portal.

1. You can continue using the previous storage account. 

1. Select the **Overview** tab.

1. [Slide] In the **Blob service** section, highlight the **Default access tier** setting. Explain how corporate content might be in the hot access tier. Auditing information could be in the cool tier. Logs or seasonal marketing literature could be in the archive tier. Learn more, [Access tiers for blob storage](https://docs.microsoft.com/azure/storage/blobs/access-tiers-overview).

1. [Slide] In the **Blob service** section, highlight the **soft delete** settings. This would be important to the public website in case something is accidentally deleted or overwritten. Students will practice soft delete in the lab. Learn more, [Blob soft delete](https://learn.microsoft.com/azure/storage/blobs/soft-delete-blob-overview).

1. In the **Blob service** section, point out the **Versioning** setting. This might be important to the Marketing department. Product literature might need to be tracked.

### Create a blob container, upload a file, and configure access.

1. In your storage account, locate the **Data storage** blade.

1. Select **Containers** and then click **+ Container**.

1. Provide a **name** for your new container, **public**. This is storage for the public website.

1. Set the access level to **Container (anonymous access read access for containers and blobs)**. Briefly describe the access levels. This is covered in more detail in the last demonstration. 

1. Click **Create**.

1. Wait for the container to be deployed, then **select** the **public** container.

1. **Upload a blob**. As you have time, discuss the options. 

1. Select the **uploaded file** and **copy the URL**.

1. Open a **new browser tab**, paste in the URL and ensure the uploaded file displays.

1. Return to the **public** container and **Change access level** to **Private (no anonymous access)**.

1. **Refresh the URL tab** and confirm access to the resource is now **denied**.

### Configure lifecycle management.

1. [Slide] The marketing group has product literature that is seasonal. For example, the winter clothing and accessory line. This content can be archived until the next season. Archiving content is easy to accomplish with a lifecycle management rule. Learn more, [Blob lifecycle management policies](https://learn.microsoft.com/azure/storage/blobs/lifecycle-management-overview).

1. Continue working with the storage account.

1. In the **Data management** blade, select **Lifecycle management**.

1. On the **Details** tab, name the rule **movetoarchive**.

1. Discuss the **rule scope** and how you can **limit blobs with filters**. For example, only moving the content in the specific container.

1. Move to the **Base blobs** tab.

1. Discuss how the rule will automatically move blobs based on the last modified or created more than days ago.

1. Open the **Then** drop-down and discuss the options. Try to give examples based on our lab scenario. For example, the IT department might want blobs deleted after 30 days because it is a test account.

### Configure limited access to content.

1. Review usage cases for limited access. For example, the corporate content needs to be shared with third party vendors or partners. Access might be limited to a specific timeframe and action (read, write). There is a slide on SAS. Learn more, [Shared access signatures](https://learn.microsoft.com/azure/storage/common/storage-sas-overview).

1. Continue with the **storage account**.

1. In the **Security + networking** blade, select **Shared access signature**.

1. Review the **Allowed services** and **Allowed resource types**. Explain that a SAS must be scoped to a storage account, container, file, or individual blob file.

1. Review the **Allowed permissions**.

1. Select **Blob and Container** and **Read**.

1. Review the **Start** and **expiry date/time** settings.

1. Click **Generate SAS and connection string**.

1. **Save** your changes. 

1. Copy the **Blob service SAS URL** to a new browser tab.

1. Discuss how the content is displayed even though this is a private container.

### Configure blob object replication. 

1. [Slide] Before continuing the demonstration, review usage cases for blob object replication. For example, the public website content needs to be backed up. Explain that storage accounts may be in different Azure regions, but that is not required. Learn more, [Object replication](https://learn.microsoft.com/azure/storage/blobs/object-replication-overview).

1. Create a **new** storage account.

1. **Create** a **container**, **backup**, in the storage account.

1. Return to the previous storage account and the **public** container. 

1. In the **Data management** blade, select **Object replication**.

1. Click **Create replication** rules.

* Destination storage account: your second storage account

* Source container: **public**

* Destination container: **backup**

1. **Create** the rule. Explain that it may take 5-10 minutes for the source container to replicate. Explain that students will take that time during the lab. 

> **Note:** Students should now be able to complete LAB_02 and LAB_03. 

  
