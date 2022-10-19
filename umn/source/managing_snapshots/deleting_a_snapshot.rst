:original_name: evs_01_0011.html

.. _evs_01_0011:

Deleting a Snapshot
===================

Scenarios
---------

If a snapshot is no longer needed, you can delete the snapshot to release the virtual resources. Snapshot deletion has the following constraints:

Constraints
-----------

-  The snapshot status must be **Available** or **Error**.
-  If a disk is deleted, all the snapshots created for this disk will also be deleted.
-  If a snapshot is deleted, disks rolled back and created from this snapshot are not affected.
-  If you have reinstalled or changed the server OS, snapshots of the system disk are automatically deleted. Snapshots of the data disks can be used as usual.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Under **Storage**, click **Elastic Volume Service**.

#. In the navigation tree on the left, choose **Elastic Volume Service** > **Snapshots**.

   The snapshot list page is displayed.

#. In the snapshot list, locate the row that contains the target snapshot and click **Delete** in the **Operation** column.

#. (Optional) If multiple snapshots are to be deleted, select |image2| in front of each snapshot and click **Delete** in the upper area of the list.

#. In the displayed dialog box, confirm the information and click **Yes**.

   If the snapshot is no longer displayed in the snapshot list, the snapshot is deleted successfully.

.. |image1| image:: /_static/images/en-us_image_0237893718.png

.. |image2| image:: /_static/images/en-us_image_0238263087.png

