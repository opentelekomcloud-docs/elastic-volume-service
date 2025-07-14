:original_name: evs_faq_0023.html

.. _evs_faq_0023:

Can I Use Backups or Snapshots Created Before Capacity Expansion to Restore Data on Expanded Disks?
===================================================================================================

Yes. If backups or snapshots have been created for disks before capacity was expanded, you can restore your disk data from these backups or snapshots after the capacity is expanded. Expansion operations do not affect backups and snapshots.

After the disk data is restored, the disk capacity is increased, but the additional space still needs to be partitioned and formatted before it can be used. You must log in to the server to extend the disk partition or file system.

To extend disk partitions and file systems, see the following sections:

-  :ref:`Extending Disk Partitions and File Systems (Windows Server 2016) <evs_01_0126>`
-  :ref:`Extending Disk Partitions and File Systems (Linux) <evs_01_0094>`
