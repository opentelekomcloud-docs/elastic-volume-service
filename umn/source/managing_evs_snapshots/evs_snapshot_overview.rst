:original_name: evs_01_0098.html

.. _evs_01_0098:

EVS Snapshot Overview
=====================

Overview
--------

An EVS snapshot is a complete copy or image of the disk data taken at a specific time. Snapshot is a major disaster recovery (DR) approach, and you can use a snapshot to restore disk data to the time when the snapshot was created.

.. table:: **Table 1** Snapshot-related operations

   +--------------------------------+--------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------+
   | Operation                      | Description                                                                                                                    | Reference                                                   |
   +================================+================================================================================================================================+=============================================================+
   | Creating snapshots             | You can create a snapshot to save the disk data at a specified time.                                                           | :ref:`Creating an EVS Snapshot <evs_01_2721>`               |
   |                                |                                                                                                                                |                                                             |
   |                                | .. note::                                                                                                                      |                                                             |
   |                                |                                                                                                                                |                                                             |
   |                                |    Snapshots are read-only. After snapshots are created, data in the snapshots cannot be modified.                             |                                                             |
   +--------------------------------+--------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------+
   | Rolling back data              | If data on a disk is incorrect or damaged, you can roll back data from a snapshot to the source disk.                          | :ref:`Rolling Back Disk Data from a Snapshot <evs_01_0012>` |
   +--------------------------------+--------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------+
   | Creating disks from a snapshot | You can create disks from a snapshot to quickly copy the snapshot data to disks.                                               | :ref:`Creating a Disk from a Snapshot <evs_01_0013>`        |
   +--------------------------------+--------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------+
   | Checking snapshot information  | You can check the snapshot details, including the region and AZ, source disk information, and tags.                            | :ref:`Checking EVS Snapshot Details <evs_01_0122>`          |
   +--------------------------------+--------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------+
   | Deleting snapshots             | If you no longer require certain snapshots or the snapshot quantity reaches the maximum allowed, you can delete the snapshots. | :ref:`Deleting an EVS Snapshot <evs_01_0011>`               |
   +--------------------------------+--------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------+

Snapshot Usage Scenarios
------------------------

The snapshot function helps address your following needs:

-  Routine data backup

   You can create snapshots for disks on a timely basis and use snapshots to recover your data in case that data loss or data inconsistency occurred due to unintended operations, viruses, or attacks.

-  Rapid data restoration

   You can create a snapshot or multiple snapshots before an application software upgrade or a service data migration. If an exception occurs during the upgrade or migration, service data can be rapidly restored to the time when the snapshot was created.

   For example, a fault occurred on system disk A of server A, and therefore server A cannot be started. As system disk A is already faulty, data on system disk A cannot be restored by rolling back data from snapshots. However, you can create disk B using an existing snapshot of system disk A and attach disk B to a properly running server, for example server B. In this case, server B obtains the data of system disk A from disk B.

   .. note::

      When rolling back data from snapshots, data can only be rolled back to the source disk, and a rollback to a different disk is not possible.

-  Multi-service quick deployment

   You can use a snapshot to create multiple disks containing the same initial data. These disks can be used as data resources for various services, for example data mining, report query, and development and testing. This method protects the initial data and creates disks rapidly, meeting diverse service requirements.

Snapshot Principles
-------------------

The following example describes the snapshot principles with two snapshots s1 and s2 created for disk v1 at different points in time:

#. Disk v1 is created, which contains no data.

#. Data d1 and d2 are written to disk v1. Data d1 and d2 are written to new spaces.

#. Snapshot s1 is created for disk v1 modified in step 2. Data d1 and d2 are not saved as another copy elsewhere. Instead, a relationship between snapshot s1 and data d1 and d2 is established.

#. Data d3 is written to disk v1, and data d2 is changed to d4. Data d3 and d4 are written to new spaces, and data d2 is not overwritten. The relationship between snapshot s1 and data d1 and d2 is still valid. Snapshot s1 can be used to restore data if needed.

#. Snapshot s2 is created for disk v1 modified in step 4, and a relationship between snapshot s2 and data d1, d3, and d4 is established.


   .. figure:: /_static/images/en-us_image_0000001991047461.png
      :alt: **Figure 1** Snapshot principles

      **Figure 1** Snapshot principles

Differences Between Disk Backups and Disk Snapshots
---------------------------------------------------

Both disk backups and disk snapshots provide redundancies for improved disk data reliability. :ref:`Table 2 <evs_01_0098__en-us_topic_0197597144_table8676102116384>` lists the differences between them.

.. _evs_01_0098__en-us_topic_0197597144_table8676102116384:

.. table:: **Table 2** Differences between backups and snapshots

   +-------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+
   | Item        | Storage Solution                                                                                                                                                                                        | Data Synchronization                                                                                                                                                                                                                                                                                                                    | DR Range                                              | Service Recovery                                                                                             |
   +=============+=========================================================================================================================================================================================================+=========================================================================================================================================================================================================================================================================================================================================+=======================================================+==============================================================================================================+
   | Backup      | Backups are stored in OBS, instead of disks. This ensures data restoration upon disk damage or corruption.                                                                                              | A backup is a copy of a disk taken at a given time and is stored in a different location. Automatic backup can be performed based on backup policies. Deleting a disk will not delete its backups.                                                                                                                                      | A backup and its source disk reside in different AZs. | You can use a backup to roll back data to its source disk or create a new disk. The data durability is high. |
   +-------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+
   | Snapshot    | Snapshots are stored on the same disk as the source data.                                                                                                                                               | A snapshot is the state of a disk at a specific point in time and is stored on the same disk. If the disk is deleted, all its snapshots will also be deleted. For example, if you reinstalled or changed the server OS, snapshots of the system disk were also automatically deleted. Snapshots of the data disks can be used as usual. | A snapshot and its source disk reside in the same AZ. | You can use a snapshot to roll back data to its source disk or create a new disk.                            |
   |             |                                                                                                                                                                                                         |                                                                                                                                                                                                                                                                                                                                         |                                                       |                                                                                                              |
   |             | .. note::                                                                                                                                                                                               |                                                                                                                                                                                                                                                                                                                                         |                                                       |                                                                                                              |
   |             |                                                                                                                                                                                                         |                                                                                                                                                                                                                                                                                                                                         |                                                       |                                                                                                              |
   |             |    Creating a backup requires a certain amount of time because data needs to be transferred to OBS. Creating a snapshot or rolling back data from a snapshot consumes less time than creating a backup. |                                                                                                                                                                                                                                                                                                                                         |                                                       |                                                                                                              |
   +-------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------+--------------------------------------------------------------------------------------------------------------+
