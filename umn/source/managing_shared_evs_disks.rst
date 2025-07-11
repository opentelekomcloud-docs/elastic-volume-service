:original_name: evs_01_0010.html

.. _evs_01_0010:

Managing Shared EVS Disks
=========================

What Is Disk Sharing?
---------------------

Disk sharing allows you to create shared EVS disks. Shared EVS disks are block storage devices that support concurrent read/write operations and can be attached to multiple servers. Shared EVS disks provide multiple attachments, high concurrency, high performance, and high reliability. They are usually used for enterprise business-critical applications that require cluster deployment and high availability (HA). Multiple servers can access the same shared EVS disk at the same time.

A shared EVS disk can be attached to a maximum of 16 servers, including ECSs or BMSs. To share files, you need to deploy a shared file system or a cluster management system, such as Windows MSCS, Veritas VCS, or CFS.

.. important::

   A shared file system or cluster management system must be set up before you can properly use a shared disk. If you simply attach a shared disk to multiple servers, data cannot be shared between those servers and may be overwritten.


.. figure:: /_static/images/en-us_image_0000002301564522.png
   :alt: **Figure 1** Application scenario of shared EVS disks

   **Figure 1** Application scenario of shared EVS disks

Advantages
----------

-  Multiple attachments: A shared EVS disk can be attached to a maximum of 16 servers.
-  High-performance: The random read/write IOPS of a shared ultra-high I/O disk can reach up to 160,000.
-  High-reliability: Shared EVS disks support both manual and automatic backup, delivering highly reliable data storage.
-  Wide range of use: Shared EVS disks can be used for Linux RHCS clusters where only shared VBD disks are needed. They can also be used for Windows MSCS and Veritas VCS clusters that require SCSI reservations.

Specifications and Performance
------------------------------

Shared EVS disks have the same specifications and performance as non-shared EVS disks.

How Do I Use Shared VBD and SCSI Disks?
---------------------------------------

You can create shared VBD disks or shared SCSI disks. It is recommended that you attach a shared disk to ECSs in the same ECS group to improve service reliability.

-  Shared VBD disks: The device type of a newly created shared disk is VBD by default. Such disks can be used as virtual block storage devices, but do not support SCSI reservations. If SCSI reservations are required for your applications, create shared SCSI EVS disks.

-  Shared SCSI disks: Such disks support SCSI reservations.

   .. important::

      -  To improve data security, you are advised to use SCSI reservations together with the anti-affinity policy of an ECS group. That said, ensure that shared SCSI disks are only attached to ECSs in the same anti-affinity ECS group.
      -  If an ECS does not belong to any anti-affinity ECS group, you are advised not to attach shared SCSI disks to this ECS. Otherwise, SCSI reservations may not work properly, which may put your data at risk.

   Concepts of the anti-affinity ECS group and SCSI reservations:

   -  The anti-affinity policy of an ECS group allows ECSs to be created on different physical servers to improve service reliability.

      For details about ECS groups, see section "Managing ECS Groups" in the *Elastic Cloud Server User Guide*.

   -  The SCSI reservation mechanism uses a SCSI reservation command to perform SCSI reservation operations. If an ECS sends such a command to an EVS disk, the disk is displayed as locked to other ECSs, preventing the data damage that may be caused by simultaneous reads/writes to the disk from multiple ECSs.

   -  ECS groups and SCSI reservations have the following relationship: A SCSI reservation on a single EVS disk cannot differentiate multiple ECSs on the same physical host. For that reason, if multiple ECSs that use the same shared EVS disk are running on the same physical host, SCSI reservations will not work properly. So you are advised to use SCSI reservations only on ECSs that are in the same ECS group, thus having a working anti-affinity policy.

Constraints on Shared Disks
---------------------------

-  A shared disk can be attached to a maximum of 16 servers.
-  The sharing attribute of a disk cannot be changed after the disk is created.
-  Shared disks can only be used as data disks, not system disks.
-  A shared file system or cluster management system must be set up before you can properly use a shared disk. If you simply attach a shared disk to multiple servers, data cannot be shared between those servers and may be overwritten.
-  When a shared disk is attached to multiple servers, the total performance of the disk on all servers cannot exceed the maximum allowed on a single disk.

Attaching a Shared EVS Disk
---------------------------

A non-shared EVS disk can only be attached to one server, whereas a shared EVS disk can be attached to up to 16 servers.

For details, see :ref:`Attaching a Shared Disk <evs_01_0037>`.

Deleting a Shared EVS Disk
--------------------------

Because a shared EVS disk can be attached to multiple servers, ensure that the shared EVS disk is detached from all the servers before deletion.

For details, see :ref:`Deleting an EVS Disk <evs_01_0005>`.

Data Sharing Principles and Common Usage Mistakes
-------------------------------------------------

A shared EVS disk is essentially the disk that can be attached to multiple servers for use. It is similar to a physical disk in that the disk can be attached to multiple physical servers, and each server can read data from and write data to any space on the disk. If no data read/write rules, such as the read/write sequence and meaning, between these servers are defined, data reads and writes between these servers may conflict, or other unpredictable errors may occur.

Though shared disks are block storage devices that provide shared access for servers, shared disks do not have the cluster management capability. You need to deploy a cluster system to manage shared disks. Common cluster management systems include Windows MSCS, Linux RHCS, Veritas VCS, and Veritas CFS.

If shared EVS disks are not managed by a cluster system, the following issues may occur:

-  Data inconsistency caused by read/write conflicts

   When a shared EVS disk is attached to two servers (server A and server B), server A cannot recognize the disk spaces allocated to server B, vice versa. That said, a disk space allocated to server A may be already used by server B. In this case, repeated disk space allocation occurs, which leads to data errors.

   For example, a shared EVS disk has been formatted into an ext3 file system and attached to server A and server B. Server A has written metadata into the file system in space R and space G. Then server B has written metadata into space E and space G. In this case, the data written into space G by server A will be replaced. When the metadata in space G is read, an error will occur.

-  Data inconsistency caused by data caching

   When a shared EVS disk is attached to two servers (server A and server B), the application on server A has read the data in space R and space G, then cached the data. At that time, other processes and threads on server A would then read this data directly from the cache. At the same time, if the application on server B has modified the data in space R and space G, the application on server A cannot detect this data change and still reads this data from the cache. As a result, the modified data cannot be viewed on server A.

   For example, a shared EVS disk has been formatted into an ext3 file system and attached to server A and server B. Both servers have cached the metadata in the file system. Then server A has created a new file (file F) on the shared disk, but server B cannot detect this modification and still reads data from its cached data. As a result, file F cannot be viewed on server B.

Before you buy a shared EVS disk, determine its device type (VBD or SCSI) based on the applications that will use the shared disk. Shared SCSI EVS disks support SCSI reservations. Before using SCSI reservations, you need to install a driver in the server OS and ensure that the OS image is included in the compatibility list.

For details about how to use shared EVS disks, see :ref:`Managing Shared EVS Disks <evs_01_0010>`.

.. important::

   If you simply attach a shared disk to multiple servers, data or files cannot be shared between the servers, because the shared disk does not have the cluster management capability. To share files between servers, build a shared file system or deploy a cluster management system.

Related Links
-------------

For more disk sharing FAQs, see :ref:`Sharing <evs_01_0084>`.
