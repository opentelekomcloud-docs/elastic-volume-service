:original_name: evs_01_0100.html

.. _evs_01_0100:

Recycle Bin Overview
====================

EVS recycle bin is disabled by default. You must :ref:`enable EVS recycle bin <evs_01_0065>` manually before you can use it.

If the recycle bin is enabled, EVS disks will be moved to the recycle bin upon deletion. This can help protect your disk data from accidental deletions.

To learn when deleted disks will be moved to the recycle bin, see :ref:`Recycle Bin Rules for Deleted EVS Disks <evs_01_0100__en-us_topic_0000001338775981_en-us_topic_0000001268924210_section10599940534>`.

You can configure a recycle bin policy to define when to move deleted disks to the recycle bin.

Constraints
-----------

-  When a disk is deleted, its snapshots are permanently deleted, regardless of whether the disk is moved to the recycle bin.
-  There are no limits on the capacity and quantity of disks in the recycle bin.

.. _evs_01_0100__en-us_topic_0000001338775981_en-us_topic_0000001268924210_section10599940534:

Recycle Bin Rules for Deleted EVS Disks
---------------------------------------

**When will EVS disks be moved to the recycle bin?**

You first have to configure a recycle bin policy to define when to move deleted disks to the recycle bin. Then, disks will be moved there if:

-  You delete disks.
-  You delete the cloud service resources that use the disks. The cloud services include ECS, BMS, CCE, and MRS.
-  You reinstall the ECS OS, and the system automatically creates a new system disk and deletes the old system disk.

**EVS disks will not be moved to the recycle bin if:**

-  Your account is restricted.
-  The number of days passes since the disk creation is less than what you specified in the recycle bin policy.

Recycle Bin Operations
----------------------

.. table:: **Table 1** Recycle bin operations

   +------------------------------------------------+-------------------------------------------------------------------------------------------------+----------------------------------------------------------------------+
   | Operation                                      | Description                                                                                     | Reference                                                            |
   +================================================+=================================================================================================+======================================================================+
   | Enable the recycle bin.                        | EVS recycle bin is disabled by default. You need to manually enable it before you can use it.   | :ref:`Enabling the Recycle Bin <evs_01_0065>`                        |
   +------------------------------------------------+-------------------------------------------------------------------------------------------------+----------------------------------------------------------------------+
   | Disable the recycle bin.                       | You can disable the recycle bin if you no longer need it.                                       | :ref:`Disabling the Recycle Bin <evs_01_0066>`                       |
   |                                                |                                                                                                 |                                                                      |
   |                                                | You must empty the recycle bin before disabling it.                                             |                                                                      |
   +------------------------------------------------+-------------------------------------------------------------------------------------------------+----------------------------------------------------------------------+
   | Configure a recycle bin policy.                | You can configure a recycle bin policy to define when to move deleted disks to the recycle bin. | :ref:`Configuring a Recycle Bin Policy <evs_01_0203>`                |
   +------------------------------------------------+-------------------------------------------------------------------------------------------------+----------------------------------------------------------------------+
   | Recover disks from the recycle bin.            | You can recover disks from the recycle bin.                                                     | :ref:`Recovering Disks from the Recycle Bin <evs_01_0067>`           |
   +------------------------------------------------+-------------------------------------------------------------------------------------------------+----------------------------------------------------------------------+
   | Permanently delete disks from the recycle bin. | You can permanently delete the EVS disks from the recycle bin at any time.                      | :ref:`Permanently Deleting Disks from the Recycle Bin <evs_01_0068>` |
   +------------------------------------------------+-------------------------------------------------------------------------------------------------+----------------------------------------------------------------------+
