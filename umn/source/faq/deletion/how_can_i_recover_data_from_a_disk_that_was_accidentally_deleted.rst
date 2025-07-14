:original_name: evs_faq_0079.html

.. _evs_faq_0079:

How Can I Recover Data from a Disk That Was Accidentally Deleted?
=================================================================

Disk data was deleted: Check whether the disk has any snapshots or backups created.

-  If there are, use a snapshot or backup to restore the disk data to the state when the snapshot or backup was created.

   -  To restore data from a snapshot, see :ref:`Rolling Back Disk Data from a Snapshot <evs_01_0012>`.
   -  To restore data from a backup, see `Restoring from a Cloud Disk Backup <https://docs.otc.t-systems.com/cloud-backup-recovery/umn/restoring_data/restoring_from_a_cloud_disk_backup.html#cbr-03-0033>`__.

   .. important::

      If the disk was deleted after the last snapshot backup was created, that incremental data cannot be restored.

-  If there are not, the disk data cannot be restored.
