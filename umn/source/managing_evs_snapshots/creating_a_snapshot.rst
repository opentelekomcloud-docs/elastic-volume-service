:original_name: en-us_topic_0066615262.html

.. _en-us_topic_0066615262:

Creating a Snapshot
===================

Scenarios
---------

You can create an EVS snapshot on the management console to save the EVS disk data at a specific time point.

Constraints
-----------

-  A maximum of 7 snapshots can be created for one disk.
-  Snapshots can be created for both system disks and data disks.
-  Snapshots can be created only for available or in-use disks.
-  Snapshots of encrypted disks are stored encrypted, and those of non-encrypted disks are stored non-encrypted.
-  If a disk is created from a snapshot, the AZ of the disk is the same as that of the snapshot's source disk and cannot be changed.

Creating a Snapshot on the Disks Page
-------------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Under **Storage**, click **Elastic Volume Service**.

   The disk list page is displayed.

#. In the disk list, locate the row that contains the target disk, click **Create Snapshot** in the **Operation** column.

   Configure the basic settings for the snapshot according to :ref:`Table 1 <en-us_topic_0066615262__table17584125003610>`.

   .. _en-us_topic_0066615262__table17584125003610:

   .. table:: **Table 1** Snapshot parameter

      +-----------------------+--------------------------------------------------+-----------------------+
      | Parameter             | Description                                      | Example Value         |
      +=======================+==================================================+=======================+
      | Snapshot Name         | Mandatory                                        | snapshot-01           |
      |                       |                                                  |                       |
      |                       | The name can contain a maximum of 64 characters. |                       |
      +-----------------------+--------------------------------------------------+-----------------------+

#. Click **Create Now**.

#. Go back to the **Snapshots** page to view the snapshot creation information.

   After the snapshot status changes to **Available**, the snapshot has been created.

Creating a Snapshot on the Snapshots Page
-----------------------------------------

#. Log in to the management console.

#. Click |image2| in the upper left corner and select the desired region and project.

#. Under **Storage**, click **Elastic Volume Service**.

   The disk list page is displayed.

#. In the navigation pane on the left, choose **Elastic Volume Service** > **Snapshots**.

   On the **Snapshots** page, click **Create Snapshot**.

   Configure the basic settings for the snapshot according to :ref:`Table 2 <en-us_topic_0066615262__table1097922420177>`.

   .. _en-us_topic_0066615262__table1097922420177:

   .. table:: **Table 2** Snapshot parameters

      +-----------------------+----------------------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Description                                                                                  | Example Value         |
      +=======================+==============================================================================================+=======================+
      | Region                | Mandatory                                                                                    | ``-``                 |
      |                       |                                                                                              |                       |
      |                       | After you select a region, disks in the selected region will be displayed for you to choose. |                       |
      +-----------------------+----------------------------------------------------------------------------------------------+-----------------------+
      | Snapshot Name         | Mandatory                                                                                    | snapshot-01           |
      |                       |                                                                                              |                       |
      |                       | The name can contain a maximum of 64 characters.                                             |                       |
      +-----------------------+----------------------------------------------------------------------------------------------+-----------------------+
      | Select Disk           | Mandatory                                                                                    | volume-01             |
      |                       |                                                                                              |                       |
      |                       | Select a disk based on which the snapshot will be created.                                   |                       |
      +-----------------------+----------------------------------------------------------------------------------------------+-----------------------+

#. Click **Create Now**.

#. Go back to the **Snapshots** page to view the snapshot creation information.

   After the snapshot status changes to **Available**, the snapshot has been created.

.. |image1| image:: /_static/images/en-us_image_0237893718.png
.. |image2| image:: /_static/images/en-us_image_0237893718.png
