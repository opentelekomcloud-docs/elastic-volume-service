:original_name: evs_01_0005.html

.. _evs_01_0005:

Deleting an EVS Disk
====================

Scenarios
---------

If an EVS disk is no longer used, you can delete the disk to release the virtual resources. After you permanently delete an EVS disk, EVS immediately destroys the metadata to ensure that data can no longer be accessed. In addition, the physical storage space of the EVS disk is reclaimed and cleared before being re-assigned. For any new disk created based on the re-assigned physical space, before data is written to the disk, EVS returns zero for all the read requests to the disk.

Notes and Constraints
---------------------

-  The disk status is **Available**, **Error**, **Expansion failed**, **Restoration failed**, or **Rollback failed**.
-  The disk is not locked by any service.
-  The shared disk has been detached from all its servers.

.. important::

   When you delete a disk, all the disk data including the snapshots created for this disk will be deleted.

   A deleted disk cannot be recovered.

Prerequisites
-------------

-  Ensure that separately created disks are detached. For details, see :ref:`Detaching an EVS Disk <evs_01_0003>`.
-  You are advised to back up data. You can :ref:`create standard snapshots <evs_01_2721>` or :ref:`use CBR to create disk backups <evs_01_0110>`.

Deleting EVS Disks
------------------

#. Sign in to the console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click |image2| in the upper left corner and choose **Storage** > **Elastic Volume Service**.

   The **Elastic Volume Service** page is displayed.

#. In the disk list, locate the target disk and choose **More** > **Delete** in the **Operation** column.

#. (Optional) If multiple disks are to be deleted, select |image3| in front of each target disk and click **Delete** in the upper left area of the list.

#. On the displayed page, confirm the information and click **Yes**.

#. Check that the disk disappears from the disk list.

Related Links
-------------

For more deletion FAQs, see :ref:`Deletion <evs_01_0083>`.

.. |image1| image:: /_static/images/en-us_image_0237893718.png
.. |image2| image:: /_static/images/en-us_image_0000001933286285.jpg
.. |image3| image:: /_static/images/en-us_image_0238263087.png
