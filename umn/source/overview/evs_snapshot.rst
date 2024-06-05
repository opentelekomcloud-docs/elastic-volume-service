:original_name: en-us_topic_0066809008.html

.. _en-us_topic_0066809008:

EVS Snapshot
============

What Is EVS Snapshot?
---------------------

An EVS snapshot is a complete copy or image of the disk data at a specific point in time. Snapshots can be used as a disaster recovery (DR) approach, and you can use snapshots to fully restore data to the time when the snapshot was taken. You can create snapshots for disks on the console or via the API.

EVS snapshots are sometimes referred to as snapshots in this document.

You can create snapshots to rapidly save the disk data at specified time points. In addition, you can use snapshots to create new disks so that the created disks will contain the snapshot data in the beginning.

Snapshot Principles
-------------------

Snapshots and backups are different in that a backup saves the data as another copy in the storage system other than on the disk, whereas a snapshot establishes a relationship between the snapshot and disk data.

The following example describes the snapshot principle by creating snapshots s1 and s2 for disk v1 at different time points:

#. Create disk v1, which contains no data.

#. .. _en-us_topic_0066809008__li1929915245012:

   Write data d1 and d2 to disk v1. Data d1 and d2 are written to new spaces.

#. Create snapshot s1 for disk v1 that is modified in :ref:`2 <en-us_topic_0066809008__li1929915245012>`. Data d1 and d2 are not saved as another copy elsewhere. Instead, the relationship between snapshot s1 and data d1 and d2 is established.

#. .. _en-us_topic_0066809008__li1023661014141:

   Write data d3 to disk v1 and change data d2 to d4. Data d3 and d4 are written to new spaces, and data d2 is not overwritten. The relationship between snapshot s1 and data d1 and d2 is still valid. Therefore, snapshot s1 can be used to restore data if needed.

#. Create snapshot s2 for disk v1 that is modified in :ref:`4 <en-us_topic_0066809008__li1023661014141>`. The relationship between s2 and data d1, d3, and d4 is established.


   .. figure:: /_static/images/en-us_image_0000001911643677.png
      :alt: **Figure 1** Snapshot principle

      **Figure 1** Snapshot principle

Application Scenarios
---------------------

The snapshot function helps address your following needs:

-  Routine data backup

   You can create snapshots for disks on a timely basis and use snapshots to recover your data in case that data loss or data inconsistency occurred due to unintended operations, viruses, or attacks.

-  Rapid data restoration

   You can create a snapshot or multiple snapshots before an application software upgrade or a service data migration. If an exception occurs during the upgrade or migration, service data can be rapidly restored to the time point when the snapshot was created.

   For example, a fault occurred on system disk A of server A, and therefore server A cannot be started. As system disk A is already faulty, data on system disk A cannot be restored by rolling back snapshots. But, you can create disk B using an existing snapshot of system disk A and attach disk B to a properly running server, for example server B. In this case, server B obtains the data of system disk A from disk B.

   .. note::

      When rolling back data from snapshots, data can only be rolled back to the original disk, and a rollback to a different disk is not possible.

-  Multi-service quick deployment

   You can use a snapshot to create multiple disks containing the same initial data, and these disks can be used as data resources for various services, for example data mining, report query, and development and testing. This method protects the initial data and creates disks rapidly, meeting diverse service requirements.

Usage Restrictions
------------------

See :ref:`Constraints <evs_01_0085>` for the snapshot usage restrictions.

Usage Instructions
------------------

For details about the snapshot usages, see :ref:`Managing EVS Snapshots <evs_01_0111>`.
