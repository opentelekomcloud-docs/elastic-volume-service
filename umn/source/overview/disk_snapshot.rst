:original_name: evs_01_2722.html

.. _evs_01_2722:

Disk Snapshot
=============

What Is Disk Snapshot?
----------------------

A snapshot is a complete copy or image of the disk data taken at a specific time. Snapshot is a major DR approach, and you can use a snapshot to restore disk data to the time when the snapshot was created. You can create snapshots for disks on the console or by calling the API.

EVS disk snapshots are sometimes referred to as snapshots in this document.

You can create snapshots to rapidly save the disk data at specified time points. You can also use snapshots to create new disks so that the created disks will contain the snapshot data in the beginning.

Snapshot Principles
-------------------

The following example describes the snapshot principles with two snapshots s1 and s2 created for disk v1 at different points in time:

#. Disk v1 is created, which contains no data.

#. Data d1 and d2 are written to disk v1. Data d1 and d2 are written to new spaces.

#. Snapshot s1 is created for disk v1 modified in step 2. Data d1 and d2 are not saved as another copy elsewhere. Instead, a relationship between snapshot s1 and data d1 and d2 is established.

#. Data d3 is written to disk v1, and data d2 is changed to d4. Data d3 and d4 are written to new spaces, and data d2 is not overwritten. The relationship between snapshot s1 and data d1 and d2 is still valid. Snapshot s1 can be used to restore data if needed.

#. Snapshot s2 is created for disk v1 modified in step 4, and a relationship between snapshot s2 and data d1, d3, and d4 is established.


   .. figure:: /_static/images/en-us_image_0000002049065922.png
      :alt: **Figure 1** Snapshot Principles

      **Figure 1** Snapshot Principles

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

Usage Restrictions
------------------

For details about the limitations on using snapshots, see :ref:`Notes and Constraints <evs_01_0085>` or the "Notes and Constraints" part in the corresponding snapshot section.

Usage Instructions
------------------

For details about how to use snapshots, see :ref:`Managing EVS Snapshots <evs_01_0111>`.
