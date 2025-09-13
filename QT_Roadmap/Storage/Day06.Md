# ALL Activtes Must practise:
================================

## Activity 1: Upload a file to Container
  * Note: for screenshots refer classroom video
  * Standard Storage
  * Premium Block Blob storage


## Activity 2: Enable anonymous access to the container
  * By default in azure storage account anonymous access is disabled
  * We can enable in from the settings –> Configuration –> Allow Blob anonymous access to enabled and save
  * Select the container and change acess level
  * Access any blob and get the url
  * Exercise:
      - upload resume document (pdf or docx) to azure storage account

## Activity 3: Accessing the private item
  * [Refer Here](https://learn.microsoft.com/en-us/azure/storage/common/storage-sas-overview) for SAS (Shared access signature)
  * SAS is temporary access to an item for a limited time period
  * Acess Keys in Storage Account: [Refer Here](https://learn.microsoft.com/en-us/azure/storage/common/storage-account-keys-manage?tabs=azure-portal)
  * Create a container with private access
   ![AT-1](../Images_Azure/azstorage26.webp)

  * upload some item into private container and try accessing from url
  ![AT-2](../Images_Azure/azstorage25.webp)

  * Every storage account will have two access keys key1 and key2. These keys can be used to access the storage account content programatically
  * Now lets generate SAS for a blob item based on key1

   ![AT-3](../Images_Azure/azstorage29.webp)

   ![At-4](../Images_Azure/azstorage30.webp)

   ![At-5](../Images_Azure/azstorage31.webp)

   ![At-6](../Images_Azure/azstorage32.webp)

 * Now access the object using url with SAS token
 * This stops working in two cases
    * date is expired
    * acess key is rotated

## Activity 4: Rotate access keys
  * Since access keys give programatic access to storage account. It is recommended to rotate access keys
  * [Refer Here](https://learn.microsoft.com/en-us/azure/storage/common/storage-account-keys-manage?tabs=azure-cli#manually-rotate-access-keys) for the section

## Activity 5: exploring containers
 * Create a resource group and a storage account (Standard)
 
 ![AT-7](../Images_Azure/azstorage33.webp)

  * Upload two files (one.txt two.txt) in two private containers
  * make a note of resource group, storage account, container name
  * delete the resource group
  * Can we recover yes
    * We can recover
        * blob
        * container
        * storage account.
  * Lets understand soft delete. The delete object will not be actually delete but marked for delete for 7 days (configured days)
  * [Refer Here](https://learn.microsoft.com/en-us/azure/storage/common/storage-account-recover) for recovering storage account

  ![AT-8](../Images_Azure/azstorage34.webp)

## Activity 5: Enable versioining for a blob
 * [Refer Here](https://learn.microsoft.com/en-us/azure/storage/blobs/versioning-enable?tabs=portal) to enable versioning in  Azure Storage account
 * Once the version is enabled and the object is uploaded navigate to versions section to find all the versions of the blob

   ![At-8](../Images_Azure/azstorage35.webp)


## Activity 6: Enable versioning extended
 * Create a standard storage account (if doest not exists)
 * Create a container called as docs
 * Create a blob called as topics.txt
 * try uploading with some topics
 * Enable versioning
 * now add some more content to topics.txt and upload as a new version.
 * Delete the older version and try restore.
 * [Refer Here](https://learn.microsoft.com/en-us/azure/storage/blobs/soft-delete-blob-manage#restore-soft-deleted-blobs-when-versioning-is-enabled) for the solution


## Activity 7: Lifecycle Managment
 * Azure Storage account supports lifecycle management to change access tiers.
 * [Refer Here](https://learn.microsoft.com/en-us/azure/storage/blobs/lifecycle-management-policy-configure?tabs=azure-portal) for lifecycle management policy
 * Manually change access tier

    ![At-9](../Images_Azure/azstorage36.webp)
   
    ![At-10](../Images_Azure/azstorage37.webp)
   
    ![At-11](../Images_Azure/azstorage38.webp)
   
    ![At-12](../Images_Azure/azstorage39.webp)

## Activity 8: Snapshots
 * Snapshot/Backup of storage account containers or blobs
 * Select the object and generate snapshot

## Activity 9: Replications
 * Redundancy is already done on the basis of LRS/ZRS/RA-GZRS
 * Replication, replicates the storage account contents to other storage belonging to same account or different account.
 * Now lets upload a new file to both containers and then experiment and observe the results.

  ![At-13](../Images_Azure/azstorage40.webp)
  ![At-14](../Images_Azure/azstorage41.webp)

## Activity 10: Static Website Hosting
 * A fully functional website which is developed in CSS, HTML and javascript can be directly hosted in storage account.
 * [Refer Here](https://learn.microsoft.com/en-us/azure/storage/blobs/storage-blob-static-website) for official docs
 * As done in the class, install  Azure storage explorer for copying folders easily
 * Download any website template [Refer Here](https://templatemo.com/)
 * enable static website hosting and copy the contents to $web container.


## Activity 11: Using Azure Storage account for Data Lakes
[Refer Here](https://learn.microsoft.com/en-us/azure/storage/blobs/data-lake-storage-introduction) for using azure storage account as datalake

## Activity 12: Attach a data disk to linux vm (Managed Disk Continuty)

 * Create a free (b1s) vm with any linux os
 * List the block devices lsblk
 
 ![AT-15](../Images_Azure/azstorage43.webp)

 * Create a directory /tools
 * Attach a data disk of size 4GiB

 ![At-16](../Images_Azure/azstorage44.webp)

 * Now list block devices

 ![At-17](../Images_Azure/azstorage45.webp)

 * The disk can be partioned or used directly for partiotion [Refer Here](https://cloudinfrastructureservices.co.uk/how-to-create-partitions-in-ubuntu-linux-using-fdisk/)
 * Lets use the disk directly by creating a xfs filesystem
 ![At-18](../Images_Azure/azstorage46.webp)

## Activity 13: Ensure mounts are available after restart
  * Lets stop the vm and start the vm
  * We observe the /tools is not mounted.
  * To retain mounts in linux across restarts we need to use fstab [Refer Here](https://learn.microsoft.com/en-us/azure/virtual-machines/linux/attach-disk-portal?tabs=ubuntu#mount-the-disk)
  * Add fstab entries as discussed in the class.


## Activity 14: Create a backup of as disk.
 * Backup of disk is referred as snapshot.

   ![At-18](../Images_Azure/azstorage47.webp)

 * types of backup
     * full: Complete readonly copy of disk
     * incremental: backups the changes done post previous snapshot.

     ![At-19](../Images_Azure/azstorage48.webp)

## Activity 15: Create a disk from this snapshot and mount to vm.
 * Create a disk
  ![AT-20](../Images_Azure/azstorage49.webp)

  ![At-21](../Images_Azure/azstorage50.webp)

 * Attach this disk to new vm

   ![At-22](../Images_Azure/azstorage51.webp)

   ![At-23](../Images_Azure/azstorage52.webp)

## Activity 16: Enable automatic backups for disks

* Create a vm with b1s and ubuntu os
* ssh into vm and install any application
* Open Backup center

  ![At-24](../Images_Azure/azstorage53.webp)

  ![At-25](../Images_Azure/azstorage54.webp)

## Activity 17: Use Azure File storage

 * Create two vms in the same region.

   ![AT-26](../Images_Azure/azstorage56.webp)

 * Create a storage account (standard or premium file share)
 
   ![AT-27](../Images_Azure/azstorage57.webp)

 * Mount the file storage to any folder (drive in windows) in vms
 * To mount the details can be found in the connect

  ![At-28](../Images_Azure/azstorage58.webp)

 * When the data is minimal in size and we need to mount the data not to morethan 3 vms we can enable shared disks


## File Shares
  * Azure provides storage accounts with file share capabilities
  * Azure File Share uses SMB protocol which can connect to multiple os as disks

  ![AT-26](../Images_Azure/azstorage55.webp)


## Queue Storage
 * Azure provides queue storage as a service in standard storage accounts.
 * [Refer Here](https://learn.microsoft.com/en-us/azure/storage/queues/storage-quickstart-queues-python?tabs=passwordless%2Croles-azure-portal%2Cenvironment-variable-windows%2Csign-in-azure-cli) for code examples


## For Backups, we can use
  * Backup center
  * Business continuity center
## For Recovery, we can use
  * Recovery services vault
  * Business continuity center
## The data will be stored in vault