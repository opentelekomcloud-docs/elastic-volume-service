:original_name: evs_faq_0057.html

.. _evs_faq_0057:

How Is a Snapshot Created for My Disk?
======================================

There are two types of snapshots: manual snapshots you create on-demand and automatic snapshots created by the system.

-  Manual snapshots: You may manually create snapshots to rapidly save the disk data at specific points of time. For details about how to create snapshots, see :ref:`Creating an EVS Snapshot <evs_01_2721>`.
-  Automatic snapshots: During the creation of a cloud server backup, or a disk backup with the CBR service, the system automatically creates a snapshot and saves the latest snapshot for each disk. If the disk already has a backup and a new backup is created, the system will automatically delete the old snapshot and save the latest one generated. This snapshot is free of charge. You can view the snapshot details only but cannot perform any operations on it.
