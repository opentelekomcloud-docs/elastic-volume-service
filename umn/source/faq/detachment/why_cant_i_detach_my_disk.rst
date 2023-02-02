:original_name: evs_faq_0056.html

.. _evs_faq_0056:

Why Can't I Detach My Disk?
===========================

EVS disks can be used as system disks or data disks, but the way you detach each one is different.

-  System disks: A system disk can only be detached offline. You must first stop the server that uses this system disk and then detach the disk.

   .. note::

      In Linux, a system disk is typically mounted on **/dev/vda**. In Windows, a system disk is normally **Volume (C:)**.

-  Data disks: A data disk can be detached regardless of whether it is offline or online.

   .. note::

      In Linux, a data disk is typically mounted on a mount point other than **/dev/vda**. In Windows, a data disk is normally a volume other than **Volume (C:)**.

   -  Offline detachment: The server must be in the **Stopped** state. If it is not, stop the server and then detach the data disk.
   -  Online detachment: Some OSs support online detachment. In this case, you do not need to stop the server before detaching the data disk. For more information, see **Storage** > **Detaching an EVS Disk from a Running ECS** in the *Elastic Cloud Server* *User Guide*.
