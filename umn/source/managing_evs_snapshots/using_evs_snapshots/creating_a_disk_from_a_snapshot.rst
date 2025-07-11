:original_name: evs_01_0013.html

.. _evs_01_0013:

Creating a Disk from a Snapshot
===============================

Scenarios
---------

This section describes how to create an EVS disk on the **Snapshots** page. You can also create an EVS disk from a snapshot by specifying the **Create from snapshot** parameter on the disk creation page. For details, see :ref:`Creating an EVS Disk <en-us_topic_0021738346>`.

Constraints
-----------

-  Batch disk creation from a snapshot is not supported.
-  A disk created from a snapshot has the same device type (SCSI or VBD), encryption attribute, AZ, region, and disk type as the snapshot's source disk.
-  A snapshot whose name starts with **autobk_snapshot_vbs\_**, **manualbk_snapshot_vbs\_**, **autobk_snapshot_csbs\_**, or **manualbk_snapshot_csbs\_** is automatically generated during backup. Such a snapshot can only be viewed. It cannot be used to create new disks.

Creating an EVS Disk from a Snapshot
------------------------------------

#. Sign in to the console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click |image2| in the upper left corner and choose **Storage** > **Elastic Volume Service**.

   The **Elastic Volume Service** page is displayed.

#. In the navigation pane on the left, choose **Elastic Volume Service** > **Snapshots**.

   The **Snapshots** page is displayed.

#. In the snapshot list, locate the target snapshot and click **Create Disk** in the **Operation** column.

#. Configure the disk parameters. For details, see parameter descriptions and operations provided in :ref:`Creating an EVS Disk <en-us_topic_0021738346>`.

   .. note::

      If you create a disk from a snapshot, the disk capacity must be greater than or equal to the snapshot size. In the condition that you do not specify a disk capacity, if the snapshot size is smaller than 10 GiB, the default capacity 10 GiB will be used as the disk capacity; if the snapshot size is greater than 10 GiB, the snapshot size will be used as the disk capacity.

#. Click **Create Now**.

#. Confirm the configuration and click **Submit**.

#. In the disk list, view the disk status.

   When the disk status changes to **Available**, the disk is successfully created.

.. |image1| image:: /_static/images/en-us_image_0237893718.png
.. |image2| image:: /_static/images/en-us_image_0000001933286285.jpg
