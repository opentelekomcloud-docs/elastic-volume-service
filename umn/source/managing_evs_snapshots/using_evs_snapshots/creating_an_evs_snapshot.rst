:original_name: evs_01_2721.html

.. _evs_01_2721:

Creating an EVS Snapshot
========================

Scenarios
---------

You can create EVS snapshots to save disk data at specific time points. Before you perform any critical operation, such as a data rollback, software upgrade, or data migration, you are advised to create snapshots to back up data. This ensures that your data is not affected even if an exception occurred during the operation.

.. note::

   During the snapshot creation, disk I/Os are affected, so you may experience slow reads or writes at some points. It is recommended that you create snapshots at off-peak hours.

Prerequisites
-------------

Snapshots can only be created for **Available** or **In-use** disks.

Notes and Constraints
---------------------

-  Snapshots can be created for both system disks and data disks.
-  Snapshots of encrypted disks are stored encrypted, and those of non-encrypted disks are stored non-encrypted.

Creating a Snapshot on the **Disks** Page
-----------------------------------------

#. Log in to the console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click |image2| in the upper left corner and choose **Storage** > **Elastic Volume Service**.

   The **Elastic Volume Service** page is displayed.

#. In the disk list, locate the target disk and click **Create Snapshot** in the **Operation** column.

   Configure the snapshot parameter according to :ref:`Table 1 <evs_01_2721__en-us_topic_0066615262_table1227554519398>`.

   .. _evs_01_2721__en-us_topic_0066615262_table1227554519398:

   .. table:: **Table 1** Snapshot parameter

      +-----------------------+--------------------------------------------------+-----------------------+
      | Parameter             | Description                                      | Example Value         |
      +=======================+==================================================+=======================+
      | Snapshot Name         | Mandatory                                        | snapshot-01           |
      |                       |                                                  |                       |
      |                       | The name can contain a maximum of 64 characters. |                       |
      +-----------------------+--------------------------------------------------+-----------------------+


   .. figure:: /_static/images/en-us_image_0000001952166289.png
      :alt: **Figure 1** Create Snapshot

      **Figure 1** Create Snapshot

#. Click **Create Now**.

#. Go back to the **Snapshots** page to view the snapshot creation information.

   After the snapshot status changes to **Available**, the snapshot has been created.

Creating a Snapshot on the **Snapshots** Page
---------------------------------------------

#. Log in to the console.

#. Click |image3| in the upper left corner and select the desired region and project.

#. Click |image4| in the upper left corner and choose **Storage** > **Elastic Volume Service**.

   The **Elastic Volume Service** page is displayed.

#. In the navigation pane on the left, choose **Elastic Volume Service** > **Snapshots**.

   On the **Snapshots** page, click **Create Snapshot**.

   Configure the snapshot parameters according to :ref:`Table 2 <evs_01_2721__en-us_topic_0066615262_table81751226104013>`.

   .. _evs_01_2721__en-us_topic_0066615262_table81751226104013:

   .. table:: **Table 2** Snapshot parameters

      +-----------------------+---------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Description                                                                                       | Example Value         |
      +=======================+===================================================================================================+=======================+
      | Region                | Mandatory                                                                                         | ``-``                 |
      |                       |                                                                                                   |                       |
      |                       | After you select a region, disks in the selected region will be displayed for you to choose from. |                       |
      +-----------------------+---------------------------------------------------------------------------------------------------+-----------------------+
      | Snapshot Name         | Mandatory                                                                                         | snapshot-01           |
      |                       |                                                                                                   |                       |
      |                       | The name can contain a maximum of 64 characters.                                                  |                       |
      +-----------------------+---------------------------------------------------------------------------------------------------+-----------------------+
      | Select Disk           | Mandatory                                                                                         | volume-01             |
      |                       |                                                                                                   |                       |
      |                       | Select a disk based on which the snapshot will be created.                                        |                       |
      +-----------------------+---------------------------------------------------------------------------------------------------+-----------------------+


   .. figure:: /_static/images/en-us_image_0000001925046644.png
      :alt: **Figure 2** Create Snapshot

      **Figure 2** Create Snapshot

#. Click **Create Now**.

#. Go back to the **Snapshots** page to view the snapshot creation information.

   After the snapshot status changes to **Available**, the snapshot has been created.

.. |image1| image:: /_static/images/en-us_image_0237893718.png
.. |image2| image:: /_static/images/en-us_image_0000001933286285.jpg
.. |image3| image:: /_static/images/en-us_image_0237893718.png
.. |image4| image:: /_static/images/en-us_image_0000001933286285.jpg
