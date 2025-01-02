:original_name: evs_faq_0079.html

.. _evs_faq_0079:

How Can I Recover Data from a Disk That Was Accidentally Deleted?
=================================================================

Check whether the disk has any snapshots or backups created.

-  If there are, use a snapshot or backup to restore the disk data to the state when the snapshot or backup was created. For details, see :ref:`Rolling Back Disk Data from a Snapshot <evs_01_0012>` or .

   .. important::

      If the disk was deleted after the last snapshot or backup was created, that incremental data cannot be restored.

-  If there are not, the disk data cannot be restored.
