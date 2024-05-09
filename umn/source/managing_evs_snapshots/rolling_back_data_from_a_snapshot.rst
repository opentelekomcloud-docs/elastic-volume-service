:original_name: evs_01_0012.html

.. _evs_01_0012:

Rolling Back Data from a Snapshot
=================================

Scenarios
---------

If data on an EVS disk is incorrect or damaged, you can roll back data from a snapshot to the source disk.

Constraints
-----------

-  Data of a snapshot can be rolled back only to its source disk. Rollback to another disk is not possible.
-  Data of a snapshot can be rolled back only when the snapshot status is **Available** and its source disk status is **Available** (not attached to any server) or **Rollback failed**. If the source disk is attached, detach the disk first.
-  A snapshot whose name starts with **autobk_snapshot_vbs\_**, **manualbk_snapshot_vbs\_**, **autobk_snapshot_csbs\_**, or **manualbk_snapshot_csbs\_** is automatically generated during backup. Such a snapshot can only be viewed. It cannot be used to roll back the disk data.
-  Spot instances do not support snapshot-based rollback of the disk data.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Under **Storage**, click **Elastic Volume Service**.

#. In the navigation pane on the left, choose **Elastic Volume Service** > **Snapshots**.

   The snapshot list page is displayed.

#. In the snapshot list, locate the row that contains the target snapshot and click **Roll Back Disk** in the **Operation** column.

#. In the displayed dialog box, click **Yes**.

   The snapshot list is displayed. After the snapshot status changes from **Rolling back** to **Available**, the data rollback is successful.

.. |image1| image:: /_static/images/en-us_image_0237893718.png
