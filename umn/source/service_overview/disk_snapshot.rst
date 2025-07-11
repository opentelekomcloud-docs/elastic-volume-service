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

#. Disk v1 was created, which contains no data.

#. Data d1 and d2 were written to disk v1. Data d1 and d2 were written to new spaces.

#. Snapshot s1 was created for disk v1 modified in step 2. Data d1 and d2 were not saved as another copy elsewhere. Instead, a relationship between snapshot s1 and data d1 and d2 was established.

#. Data d3 was written to disk v1, and data d2 was changed to d4. Data d3 and d4 were written to new spaces, and data d2 was not overwritten. The relationship between snapshot s1 and data d1 and d2 was still valid. Snapshot s1 can be used to restore data if needed.

#. Snapshot s2 was created for disk v1 modified in step 4, and a relationship between snapshot s2 and data d1, d3, and d4 was established.


   .. figure:: /_static/images/en-us_image_0000002049065922.png
      :alt: **Figure 1** Snapshot Principles

      **Figure 1** Snapshot Principles

Usage Restrictions
------------------

For details about the limitations on using snapshots, see :ref:`Notes and Constraints <evs_01_0085>` or the "Notes and Constraints" part in the corresponding snapshot section.

Usage Instructions
------------------

For details about how to use snapshots, see :ref:`Managing EVS Snapshots <evs_01_0111>`.
