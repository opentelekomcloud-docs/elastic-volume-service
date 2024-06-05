:original_name: evs_01_0010.html

.. _evs_01_0010:

Managing Shared EVS Disks
=========================

How to Use Shared VBD and SCSI Disks
------------------------------------

You can create shared VBD disks or shared SCSI disks. It is recommended that you attach a shared disk to the ECSs in the same ECS group to improve service reliability.

-  Shared VBD disks: The device type of a newly created shared disk is VBD by default. Such disks can be used as virtual block storage devices, but do not support SCSI reservations. If SCSI reservations are required for your applications, create shared SCSI EVS disks.

-  Shared SCSI disks: Such disks support SCSI reservations.

   .. important::

      -  To improve data security, you are advised to use SCSI reservations together with the anti-affinity policy of an ECS group. That said, ensure that shared SCSI disks are only attached to ECSs in the same anti-affinity ECS group.
      -  If an ECS does not belong to any anti-affinity ECS group, you are advised not to attach shared SCSI disks to this ECS. Otherwise, SCSI reservations may not work properly, which may put your data at risk.

   Concepts of the anti-affinity ECS group and SCSI reservations:

   -  The anti-affinity policy of an ECS group allows ECSs to be created on different physical servers to improve service reliability.

      For details about ECS groups, see **Managing ECS Groups** in the *Elastic Cloud Server User Guide*.

   -  The SCSI reservation mechanism uses a SCSI reservation command to perform SCSI reservation operations. If an ECS sends such a command to an EVS disk, the disk is displayed as locked to other ECSs, preventing the data damage that may be caused by simultaneous read/write operations to the disk from multiple ECSs.

   -  ECS groups and SCSI reservations have the following relationship: A SCSI reservation on a single EVS disk cannot differentiate multiple ECSs on the same physical host. For that reason, if multiple ECSs that use the same shared EVS disk are running on the same physical host, SCSI reservations will not work properly. So you are advised to use SCSI reservations only on ECSs that are in the same ECS group, thus having a working anti-affinity policy.

Constraints on Shared Disks
---------------------------

-  A shared disk can be attached to a maximum of 16 servers.
-  The sharing attribute of a disk cannot be changed after the disk is created.
-  Shared disks can only be used as data disks. The sharing function is not supported for system disks.
-  A shared file system or cluster management system must be set up before you can properly use a shared disk. If you simply attach a shared disk to multiple servers, the sharing function will not work and data may be overwritten.
-  When a shared disk is attached to multiple servers, the total performance of the disk on all servers cannot exceed the maximum allowed on a single disk.

Attaching a Shared EVS Disk
---------------------------

A non-shared EVS disk can only be attached to one server, whereas a shared EVS disk can be attached to up to 16 servers.

For details, see :ref:`Attaching a Shared Disk <evs_01_0037>`.

Deleting a Shared EVS Disk
--------------------------

Because a shared EVS disk can be attached to multiple servers, ensure that the shared EVS disk is detached from all the servers before deletion.

For details, see :ref:`Deleting EVS Disks <evs_01_0005>`.

Expanding a Shared EVS Disk
---------------------------

Shared EVS disks must be expanded when they are in the **Available** state. For details, see :ref:`Expanding Capacity for an In-use EVS Disk <evs_01_0007>`.

Related Operations
------------------

For more disk sharing FAQs, see :ref:`Sharing <evs_01_0084>`.
