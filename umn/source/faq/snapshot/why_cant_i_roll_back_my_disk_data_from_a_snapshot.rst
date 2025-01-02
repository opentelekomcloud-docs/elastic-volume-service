:original_name: evs_faq_0058.html

.. _evs_faq_0058:

Why Can't I Roll Back My Disk Data from a Snapshot?
===================================================

Possible causes are as follows:

-  Snapshot data can only be rolled back when the status of the snapshot's source disk is **Available** or **Rollback failed**. If the snapshot's source disk is **In-use**, detach the disk and then use the snapshot to roll back disk data. After the rollback succeeds, re-attach the disk.
-  Snapshot data can only be rolled back to source EVS disks. Rollback to a different disk is not possible.
-  If the snapshot is being created, it cannot be used to roll back disk data.
-  A snapshot whose name starts with **autobk_snapshot_vbs\_**, **manualbk_snapshot_vbs\_**, **autobk_snapshot_csbs\_**, or **manualbk_snapshot_csbs\_** is automatically generated during backup. Such a snapshot can only be viewed. It cannot be used to roll back the disk data.
