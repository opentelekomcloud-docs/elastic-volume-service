:original_name: evs_01_0012.html

.. _evs_01_0012:

Rolling Back Data from a Snapshot
=================================

Scenarios
---------

If the data on an EVS disk is incorrect or damaged, you can roll back the data from a snapshot to the source disk to restore data. Snapshot rollback has the following constraints:

Constraints
-----------

-  A snapshot can be rolled back only to its source disk. Rollback to another disk is not possible.
-  A snapshot can be rolled back only when the snapshot status is **Available** and the source disk status is **Available** (not attached to any server) or **Rollback failed**.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Under **Storage**, click **Elastic Volume Service**.

#. In the navigation tree on the left, choose **Elastic Volume Service** > **Snapshots**.

   The snapshot list page is displayed.

#. In the snapshot list, locate the row that contains the target snapshot and click **Roll Back Disk** in the **Operation** column.

#. In the displayed dialog box, click **Yes**.

#. The snapshot list is displayed. After the snapshot status changes from **Rolling back** to **Available**, the data rollback is successful.

.. |image1| image:: /_static/images/en-us_image_0237893718.png

