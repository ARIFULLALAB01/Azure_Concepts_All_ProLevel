# Azure Storage contineous:

* Disk Performance Parameters
  * Speed
    * IOPS (IOPS): number of input/output operations done per second
  * Throughput : Amount of data transferred per second
  * Size
  * Hardware type:
     * HDD
     * SSD
## Block Storage (Disk Storage)
 * In Azure When we create a virtual machine, vm size determines
    * number of data disks
    * max iops
    * local/temp storage size
 * Any vm size with s in it supports premium disks
 * Azure allows us to create disks in two ways
    * unmanaged disks:
       * This is page blob in storage account
    * managed disks
       * This is managed disks by azure.
 * Azure recommends using managed disks
 * Managed Disk Catgories
   * **Standard:**
    * Hardware types:
        * HDD
        * SSD
    * skus
       * Standard HDD
       * Standard SSD
   * **Premium**
    * Hardware Type:
       * SSD
    * skus
       * Premium SSD
       * Premium SSD v2