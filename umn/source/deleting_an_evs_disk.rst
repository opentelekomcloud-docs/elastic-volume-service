:original_name: evs_01_0005.html

.. _evs_01_0005:

Deleting an EVS Disk
====================

Scenarios
---------

If an EVS disk is no longer used, you can release the virtual resources by deleting the disk from the system.

-  Before deleting a disk, ensure that the disk status is **Available**, **Error**, **Expansion failed**, **Restoration failed**, or **Rollback failed**.
-  Before deleting a shared disk, ensure that the disk has been detached from all its servers.

.. important::

   -  When you delete a disk, all the disk data including the snapshots created for this disk will be deleted. Exercise caution when performing this operation.
   -  A deleted disk cannot be recovered.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Under **Storage**, click **Elastic Volume Service**.

   The disk list page is displayed.

#. In the disk list, locate the row that contains the target disk, click **More** in the **Operation** column, and choose **Delete**.

#. (Optional) If multiple disks are to be deleted, select |image2| in front of each disk and click **Delete** in the upper area of the list.

#. In the displayed dialog box, confirm the information and click **Yes**.

.. |image1| image:: /_static/images/en-us_image_0237893718.png

.. |image2| image:: /_static/images/en-us_image_0238263087.png

