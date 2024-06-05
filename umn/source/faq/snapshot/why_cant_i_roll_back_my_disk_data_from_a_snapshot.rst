:original_name: evs_faq_0058.html

.. _evs_faq_0058:

Why Can't I Roll Back My Disk Data from a Snapshot?
===================================================

Possible causes are as follows:

-  Snapshot data can be rolled back only when the status of the snapshot's source disk is **Available** or **Rollback failed**. If the snapshot's source disk is **In-use**, detach the disk and then roll back the snapshot data. After the rollback succeeds, re-attach the disk.
-  A snapshot whose name starts with **autobk_snapshot_vbs\_**, **manualbk_snapshot_vbs\_**, **autobk_snapshot_csbs\_**, or **manualbk_snapshot_csbs\_** is automatically generated during backup. Such a snapshot can only be viewed. It cannot be used to roll back the disk data.
