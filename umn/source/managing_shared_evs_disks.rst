:original_name: evs_01_0010.html

.. _evs_01_0010:

Managing Shared EVS Disks
=========================

How to Use Shared VBD and SCSI Disks?
-------------------------------------

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

Attaching a Shared EVS Disk
---------------------------

A common EVS disk can only be attached to one server, whereas a shared EVS disk can be attached to up to 16 servers.

For details about how to attach a shared EVS disk, see :ref:`Attaching a Shared Disk <evs_01_0037>`.

Deleting a Shared EVS Disk
--------------------------

Because a shared EVS disk can be attached to multiple servers, ensure that the shared EVS disk is detached from all the servers before deletion.

For details about how to delete a shared EVS disk, see :ref:`Deleting EVS Disks <evs_01_0005>`.

Expanding a Shared EVS Disk
---------------------------

Shared EVS disks must be expanded when they are in the **Available** state. For details, see :ref:`Expanding Capacity for an In-use EVS Disk <evs_01_0007>`.

Related Operations
------------------

For more disk sharing FAQs, see :ref:`Sharing <evs_01_0084>`.
