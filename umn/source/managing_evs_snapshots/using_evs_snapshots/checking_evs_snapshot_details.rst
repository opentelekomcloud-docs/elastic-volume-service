:original_name: evs_01_0122.html

.. _evs_01_0122:

Checking EVS Snapshot Details
=============================

Scenarios
---------

You can check the snapshot details, including the region and AZ, source disk information, and tags.

Checking Snapshot Details
-------------------------

#. Sign in to the console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Choose **Storage** > **Elastic Volume Service**.

#. In the navigation pane on the left, choose **Elastic Volume Service** > **Snapshots**.

   The **Snapshots** page is displayed.

#. In the snapshot list, locate the target snapshot.

   Select the snapshot and check the snapshot details at the bottom of the page.

Snapshot Statuses
-----------------

An EVS snapshot has several statuses. :ref:`Table 1 <evs_01_0122__en-us_topic_0232543363_en-us_topic_0066854053_table64552624191747>` lists the EVS snapshot statuses, the meaning of each status, and the operations a snapshot in each status allows.

.. _evs_01_0122__en-us_topic_0232543363_en-us_topic_0066854053_table64552624191747:

.. table:: **Table 1** Snapshot status details

   +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | Snapshot Status       | Description                                                                                                                                                                                                                              | Allowed Operation                                 |
   +=======================+==========================================================================================================================================================================================================================================+===================================================+
   | Creating              | The snapshot is being created.                                                                                                                                                                                                           | None                                              |
   +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | Available             | The snapshot is successfully created.                                                                                                                                                                                                    | -  Creating EVS disks using snapshots             |
   |                       |                                                                                                                                                                                                                                          | -  Deleting snapshots                             |
   |                       |                                                                                                                                                                                                                                          | -  Rolling back data to EVS disks using snapshots |
   +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | Deleting              | The snapshot is being deleted.                                                                                                                                                                                                           | None                                              |
   +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | Error                 | An error occurs when you try to create a snapshot.                                                                                                                                                                                       | Deleting snapshots                                |
   +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | Deletion failed       | An error occurs when you try to delete a snapshot.                                                                                                                                                                                       | None                                              |
   +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | Rolling back          | The snapshot is being used to roll back data.                                                                                                                                                                                            | None                                              |
   |                       |                                                                                                                                                                                                                                          |                                                   |
   |                       | .. note::                                                                                                                                                                                                                                |                                                   |
   |                       |                                                                                                                                                                                                                                          |                                                   |
   |                       |    -  When you roll back data from a snapshot, you can only roll back data to the source EVS disk. Rollback to a specific disk is not supported.                                                                                         |                                                   |
   |                       |    -  A snapshot can only be used for rollback when its source disk is in the **Available** or **Rollback failed** state.                                                                                                                |                                                   |
   +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+
   | Backing up            | This status only shows up for temporary snapshots. When you create a backup for an EVS disk, a temporary snapshot is automatically created. This status indicates that a temporary snapshot is being created during the backup creation. | None                                              |
   |                       |                                                                                                                                                                                                                                          |                                                   |
   |                       | .. note::                                                                                                                                                                                                                                |                                                   |
   |                       |                                                                                                                                                                                                                                          |                                                   |
   |                       |    Temporary snapshots are created through the CBR service. Do not perform any operation on these snapshots.                                                                                                                             |                                                   |
   +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0237893718.png
