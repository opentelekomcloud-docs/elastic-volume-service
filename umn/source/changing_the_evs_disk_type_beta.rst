:original_name: evs_01_0062.html

.. _evs_01_0062:

Changing the EVS Disk Type (Beta)
=================================

Scenarios
---------

If the performance of an existing disk no longer meets your service requirements, you can change the disk type to improve the disk performance.

Constraints
-----------

.. table:: **Table 1** Constraints on the disk type change

   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Phase                             | Description                                                                                                                                                                                                                                                                                                                    |
   +===================================+================================================================================================================================================================================================================================================================================================================================+
   | Before the change                 | -  You can only change the disk type when the disk status is **Available** or **In-use**.                                                                                                                                                                                                                                      |
   |                                   | -  The disk type cannot be changed when any snapshot of the disk is being deleted.                                                                                                                                                                                                                                             |
   |                                   | -  Changing the disk type may affect the disk performance, so change the type during off-peak hours.                                                                                                                                                                                                                           |
   |                                   | -  A disk having more than 128 snapshots cannot have its disk type changed. You can delete some snapshots and then change the disk type.                                                                                                                                                                                       |
   |                                   | -  The disk type of a disk protected by SDRS cannot be changed.                                                                                                                                                                                                                                                                |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | During the change                 | -  Some operations cannot be performed on the disk. Such operations include creating snapshots, creating backups, expanding the disk capacity, rolling back data from a snapshot, restoring data from a backup, attaching or detaching the disk, deleting the disk, transferring the disk, and creating an image from the ECS. |
   |                                   | -  Changing the disk type may take several hours or even longer, and cannot be stopped. The time depends on the throughput, storage space, and original disk type at the time of the change.                                                                                                                                   |
   |                                   | -  In rare cases, the change may fail due to resource problems. In this case, you are advised to perform the change again.                                                                                                                                                                                                     |
   |                                   | -  You can have a maximum of 10 disks with their types being changed at the same time.                                                                                                                                                                                                                                         |
   |                                   | -  The OS cannot be changed if you are changing the disk type of a system disk.                                                                                                                                                                                                                                                |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | After the change                  | In rare cases, the disk type may fail to be changed due to a background resource issue. If this happens, try again later.                                                                                                                                                                                                      |
   +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

The following table shows the supported changes between disk types.

.. table:: **Table 2** Supported changes between disk types

   +---------------------+---------------------------------------------------------------+
   | Source Disk Type    | New Disk Type                                                 |
   +=====================+===============================================================+
   | Extreme SSD         | Ultra-high I/O or General Purpose SSD                         |
   +---------------------+---------------------------------------------------------------+
   | Ultra-high I/O      | Extreme SSD or General Purpose SSD                            |
   +---------------------+---------------------------------------------------------------+
   | General Purpose SSD | Extreme SSD or Ultra-high I/O                                 |
   +---------------------+---------------------------------------------------------------+
   | High I/O            | Extreme SSD, Ultra-high I/O, or General Purpose SSD           |
   +---------------------+---------------------------------------------------------------+
   | Common I/O          | Extreme SSD, Ultra-high I/O, General Purpose SSD, or High I/O |
   +---------------------+---------------------------------------------------------------+

Impact on the System
--------------------

Read and write operations on the disk are not affected.

Prerequisites
-------------

You are advised to create a snapshot for the disk to back up the disk data before changing the disk specifications. For details, see :ref:`Creating an EVS Snapshot <evs_01_2721>`.

Procedure
---------

#. Sign in to the console.

#. Click |image1| in the upper left corner and choose **Storage** > **Elastic Volume Service**.

   The **Elastic Volume Service** page is displayed.

#. In the disk list, locate the target disk, click **More** in the **Operation** column, and choose **Modify Specifications**.

   The **Modify Specifications** page is displayed.

#. Select a disk type from the drop-down list.


   .. figure:: /_static/images/en-us_image_0000002335563257.png
      :alt: **Figure 1** Modify Specifications

      **Figure 1** Modify Specifications

#. Click **Submit**.

   The disk list is displayed, and the disk status is **Changing disk type**, indicating that the disk type is being changed. After the disk type changes to the target type, the operation is successful.

.. |image1| image:: /_static/images/en-us_image_0000001933286285.jpg
