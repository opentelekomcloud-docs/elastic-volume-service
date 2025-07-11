:original_name: evs_01_0012.html

.. _evs_01_0012:

Rolling Back Disk Data from a Snapshot
======================================

Scenarios
---------

If data on an EVS disk is incorrect or damaged, you can roll back data from a snapshot to the source disk.

Notes and Constraints
---------------------

-  Snapshot data can only be rolled back to source EVS disks. Rollback to a different disk is not possible.
-  You can only roll back disk data from a snapshot when the source disk status is **Available** (not attached to any server) or **Rollback failed**. If the source disk is attached, detach the disk first.
-  If a snapshot is being created, it cannot be used to roll back disk data.


Rolling Back Disk Data from a Snapshot
--------------------------------------

#. Sign in to the console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click |image2| in the upper left corner and choose **Storage** > **Elastic Volume Service**.

   The **Elastic Volume Service** page is displayed.

#. In the navigation pane on the left, choose **Elastic Volume Service** > **Snapshots**.

   The **Snapshots** page is displayed.

#. In the snapshot list, locate the target snapshot and click **Roll Back Disk** in the **Operation** column.

#. In the displayed dialog box, click **Yes**.

   The snapshot list is displayed. After the snapshot status changes from **Rolling back** to **Available**, the data rollback is successful.

.. |image1| image:: /_static/images/en-us_image_0237893718.png
.. |image2| image:: /_static/images/en-us_image_0000001933286285.jpg
