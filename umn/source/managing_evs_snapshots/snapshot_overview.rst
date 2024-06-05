:original_name: evs_01_0098.html

.. _evs_01_0098:

Snapshot Overview
=================

What Is EVS Snapshot?
---------------------

An EVS snapshot is a complete copy or image of the disk data at a specific point in time. Snapshots can be used as a disaster recovery (DR) approach, and you can use snapshots to fully restore data to the time when the snapshot was taken. You can create snapshots for disks on the console or via the API.

EVS snapshots are sometimes referred to as snapshots in this document.

You can create snapshots to rapidly save the disk data at specified time points. In addition, you can use snapshots to create new disks so that the created disks will contain the snapshot data in the beginning.

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

Operation Overview
------------------

You can create snapshots according to :ref:`Creating a Snapshot <en-us_topic_0066615262>` to rapidly save the disk data at specified points in time.

If a data loss happened, you can roll back the disk data to the time when the snapshot was created based on :ref:`Rolling Back Data from a Snapshot <evs_01_0012>`. In addition, you can create a new disk from the snapshot so that the disk will contain the snapshot data in the beginning. For details, see :ref:`Creating an EVS Disk from a Snapshot <evs_01_0013>`.

When a snapshot is no longer needed, delete it according to :ref:`Deleting a Snapshot <evs_01_0011>` to release the virtual resources.

Snapshot FAQ
------------

For more snapshot FAQs, see :ref:`Snapshot <evs_01_0092>`.
