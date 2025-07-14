:original_name: evs_01_0011.html

.. _evs_01_0011:

Deleting an EVS Snapshot
========================

Scenarios
---------

If you no longer require certain snapshots or the snapshot quantity reaches the maximum allowed, you can delete some snapshots.

Prerequisites
-------------

-  The snapshot status must be **Available** or **Error**.

Constraints
-----------

-  If a snapshot is deleted, disks rolled back or created from this snapshot are not affected.
-  If a snapshot's source disk is deleted, all snapshots of this disk are also deleted.
-  If you reinstall or change the server OS, snapshots of the system disk are automatically deleted. Those of the data disks can be used as usual.

Procedure
---------

#. Sign in to the console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click |image2| in the upper left corner and choose **Storage** > **Elastic Volume Service**.

   The **Elastic Volume Service** page is displayed.

#. In the navigation pane on the left, choose **Elastic Volume Service** > **Snapshots**.

   The **Snapshots** page is displayed.

#. In the snapshot list, locate the target snapshot and click **Delete** in the **Operation** column.

#. In the displayed dialog box, confirm the information and click **Yes**.

   If the snapshot disappears from the snapshot list, the snapshot is deleted successfully.

.. |image1| image:: /_static/images/en-us_image_0237893718.png
.. |image2| image:: /_static/images/en-us_image_0000001933286285.jpg
