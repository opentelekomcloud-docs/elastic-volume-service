:original_name: evs_01_0005.html

.. _evs_01_0005:

Deleting an EVS Disk
====================

Scenarios
---------

If an EVS disk is no longer used, you can delete the disk to release the virtual resources. When a disk is deleted, EVS immediately destroys the metadata to ensure that data can no longer be accessed. In addition, the physical storage space of the disk is reclaimed and cleared before being re-assigned. For any new disk created based on the re-assigned physical space, before data is written to the disk, EVS returns zero for all the read requests to the disk.

Notes and Constraints
---------------------

-  The disk status is **Available**, **Error**, **Expansion failed**, **Restoration failed**, or **Rollback failed**.
-  The disk is not locked by any service.
-  The shared disk has been detached from all its servers.

.. important::

   When you delete a disk, all the disk data including the legacy snapshots created for this disk will be deleted.

   A deleted disk cannot be recovered.

Deleting EVS Disks
------------------

#. Log in to the console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click |image2| in the upper left corner and choose **Storage** > **Elastic Volume Service**.

   The **Elastic Volume Service** page is displayed.

#. In the disk list, locate the row that contains the target disk, click **More** in the **Operation** column, and choose **Delete**.

#. (Optional) If multiple disks are to be deleted, select |image3| in front of each disk and click **Delete** in the upper area of the list.

#. In the displayed dialog box, confirm the information and click **Yes**.

Helpful Links
-------------

For more deletion FAQs, see :ref:`Deletion <evs_01_0083>`.

.. |image1| image:: /_static/images/en-us_image_0237893718.png
.. |image2| image:: /_static/images/en-us_image_0000001933286285.jpg
.. |image3| image:: /_static/images/en-us_image_0238263087.png
