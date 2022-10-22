:original_name: evs_01_0013.html

.. _evs_01_0013:

Creating an EVS Disk from a Snapshot
====================================

Scenarios
---------

This section describes how to create an EVS disk on the **Snapshots** page. Besides, you can also create an EVS disk from a snapshot by specifying the **Create from snapshot** parameter on the disk creation page. For details, see :ref:`Create an EVS Disk <en-us_topic_0021738346>`.

Constraints
-----------

-  The disk type of the new disk is the same as that of the snapshot's source disk.
-  The device type of the new disk is the same as that of the snapshot's source disk.
-  The encryption attribute of the new disk is the same as that of the snapshot's source disk.
-  A maximum of 128 disks can be created from this snapshot.
-  Batch disk creation is not possible, and the quantity parameter must be set to **1**.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Under **Storage**, click **Elastic Volume Service**.

#. In the navigation tree on the left, choose **Elastic Volume Service** > **Snapshots**.

   The snapshot list page is displayed.

#. In the snapshot list, locate the row that contains the target snapshot and click **Create Disk** in the **Operation** column.

#. Set the EVS disk parameters. For details, see parameter descriptions and operations provided in :ref:`Create an EVS Disk <en-us_topic_0021738346>`.

   .. note::

      A maximum of 128 disks can be created from a snapshot.

      If you create a disk from a snapshot, the disk capacity must be greater than or equal to the snapshot size. In the condition that you do not specify the disk capacity, if the snapshot size is smaller than 10 GB, the default capacity 10 GB will be used as the disk capacity; if the snapshot size is greater than 10 GB, the disk capacity will be consistent with the snapshot size.

#. Click **Create Now**.

#. Go back to the disk list page and view the disk status.

   When the disk status changes to **Available**, the disk is successfully created.

.. |image1| image:: /_static/images/en-us_image_0237893718.png
