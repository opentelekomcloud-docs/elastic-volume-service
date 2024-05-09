:original_name: evs_01_0005.html

.. _evs_01_0005:

Deleting EVS Disks
==================

Scenarios
---------

If an EVS disk is no longer used, you can release the virtual resources by deleting it.

-  The disk status is **Available**, **Error**, **Expansion failed**, **Restoration failed**, or **Rollback failed**.
-  The disk is not locked by any service.
-  The shared disk has been detached from all its servers.

When a disk is deleted, EVS immediately destroys the metadata so that data can no longer be accessed. In addition, the physical storage space of the disk is reclaimed and cleared before being re-assigned. For any new disk created based on the re-assigned physical space, before data is written to the disk, EVS returns zero for all the read and write requests to the disk.

.. important::

   -  When you delete a disk, all the disk data including the snapshots created for this disk will be deleted.
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

Related Operations
------------------

For more deletion FAQs, see :ref:`Deletion <evs_01_0083>`.

.. |image1| image:: /_static/images/en-us_image_0237893718.png
.. |image2| image:: /_static/images/en-us_image_0238263087.png
