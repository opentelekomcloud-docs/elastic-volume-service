:original_name: en-us_topic_0032860759.html

.. _en-us_topic_0032860759:

Shared EVS Disks and Usage Instructions
=======================================

What Are Shared EVS Disks?
--------------------------

Shared EVS disks are block storage devices that support concurrent read/write operations and can be attached to multiple servers. Shared EVS disks feature multiple attachments, high-concurrency, high-performance, and high-reliability. They are usually used for enterprise business-critical applications that require cluster deployment. Multiple servers can access the same shared EVS disk at the same time.

A shared EVS disk can be attached to a maximum of 16 servers. Servers that EVS supports include ECSs and BMSs. To achieve file sharing, you need to deploy a shared file system or a cluster management system, such as Windows MSCS, Veritas VCS, or CFS.

.. important::

   To use shared EVS disks, you must set up a shared file system or similar cluster management system. If you directly attach EVS disks to multiple servers, the EVS disks cannot be shared and data may be overwritten.


.. figure:: /_static/images/en-us_image_0197136031.png
   :alt: **Figure 1** Application scenario of shared EVS disks

   **Figure 1** Application scenario of shared EVS disks

Usage Precautions
-----------------

Most common clusters, such as Windows MSCS and Veritas VCS and CFS, require SCSI reservations. Therefore, you are advised to use shared SCSI EVS disks for clusters. If a SCSI EVS disk is attached to a Xen ECS for use, you must install the driver. For details, see :ref:`Device Types and Usage Instructions <en-us_topic_0052554220>`.

You can create shared VBD disks or shared SCSI disks. It is recommended that you attach the shared disk to the ECSs in the same ECS group to improve service reliability.

-  Shared VBD EVS disks: The device type of a newly created shared EVS disk is VBD by default. Such disks can be used as virtual block storage devices, but do not support SCSI reservations. If SCSI reservations are required for your applications, create shared SCSI EVS disks.

-  Shared SCSI EVS disks: These EVS disks support SCSI reservations.

   .. important::

      -  To improve data security, you are advised to use SCSI reservations together with the anti-affinity policy of an ECS group. That said, ensure that shared SCSI EVS disks are only attached to ECSs in the same anti-affinity ECS group.
      -  If an ECS does not belong to any anti-affinity ECS group, you are advised not to attach shared SCSI EVS disks to this ECS. Otherwise, SCSI reservations may not work properly, which may put your data at risk.

   Concepts of the anti-affinity ECS group and SCSI reservations:

   -  The anti-affinity policy of an ECS group allows ECSs to be created on different physical servers to improve service reliability.

      For details about ECS groups, see **Managing ECS Groups** in the *Elastic Cloud Server User Guide*.

   -  The SCSI reservation mechanism uses a SCSI reservation command to perform SCSI reservation operations. If an ECS sends such a command to an EVS disk, the disk is displayed as locked to other ECSs, preventing the data damage that may be caused by simultaneous read/write operations to the disk from multiple ECSs.

   -  ECS groups and SCSI reservations have the following relationship: A SCSI reservation on a single EVS disk cannot differentiate multiple ECSs on the same physical host. For that reason, if multiple ECSs that use the same shared EVS disk are running on the same physical host, SCSI reservations will not work properly. Therefore, you are advised to use SCSI reservations only on ECSs that are in the same ECS group, thus having a working anti-affinity policy.

Advantages
----------

-  Multiple attachments: A shared EVS disk can be attached to a maximum of 16 servers.
-  High-performance: When multiple servers concurrently access a shared ultra-high I/O EVS disk, random read/write IOPS can reach up to 160,000.
-  High-reliability: Shared EVS disks support both manual and automatic backup, delivering highly reliable data storage.
-  Wide application scenarios: Shared EVS disks can be used for Linux RHCS clusters where only VBD EVS disks are needed. Whereas, they can also be used for Windows MSCS and Veritas VCS clusters that require SCSI reservations.

Specifications and Performance
------------------------------

The specifications and performance of shared EVS disks are the same as those of non-shared EVS disks. For details, see :ref:`Disk Types and Performance <en-us_topic_0014580744>`.

Data Sharing Principle and Common Usage Mistakes
------------------------------------------------

A shared EVS disk is essentially the disk that can be attached to multiple servers for use, which is similar to a physical disk in that the disk can be attached to multiple physical servers, and each server can read data from and write data into any space on the disk. If the data read/write rules, such as the read/write sequence and meaning, between these servers are not defined, data read/write interference between servers or other unpredictable errors may occur.

Though shared EVS disks are block storage devices that provide shared access for servers, shared EVS disks do not have the cluster management capability. Therefore, you need to deploy a cluster system to manage shared EVS disks. Common cluster management systems include Windows MSCS, Linux RHCS, Veritas VCS, and Veritas CFS.

If shared EVS disks are not managed by a cluster system, the following issues may occur:

-  Data inconsistency caused by read/write conflicts

   When a shared EVS disk is attached to two servers (server A and server B), server A cannot recognize the disk spaces allocated to server B, vice versa. That said, a disk space allocated to server A may be already used by server B. In this case, repeated disk space allocation occurs, which leads to data errors.

   For example, a shared EVS disk has been formatted into the ext3 file system and attached to server A and server B. Server A has written metadata into the file system in space R and space G. Then server B has written metadata into space E and space G. In this case, the data written into space G by server A will be replaced. When the metadata in space G is read, an error will occur.

-  Data inconsistency caused by data caching

   When a shared EVS disk is attached to two servers (server A and server B), the application on server A has read the data in space R and space G, then cached the data. At that time, other processes and threads on server A would then read this data directly from the cache. At the same time, if the application on server B has modified the data in space R and space G, the application on server A cannot detect this data change and still reads this data from the cache. As a result, the user cannot view the modified data on server A.

   For example, a shared EVS disk has been formatted into the ext3 file system and attached to server A and server B. Both servers have cached the metadata in the file system. Then server A has created a new file (file F) on the shared disk, but server B cannot detect this modification and still reads data from its cached data. As a result, the user cannot view file F on server B.

Before you attach a shared EVS disk to multiple servers, the disk device type needs to be determined. The device type can be either VBD or SCSI. Shared SCSI EVS disks support SCSI reservations. Before using SCSI reservations, you need to install a driver in the server OS and ensure that the OS image is included in the compatibility list.

For details about the usages of shared EVS disks, see :ref:`Managing a Shared EVS Disk <evs_01_0010>`.

.. important::

   If you simply attach a shared EVS disk to multiple servers, files cannot be shared between the servers as shared EVS disks do not have the cluster capability. Therefore, build a shared file system or deploy a cluster management system if you need to share files between servers.
