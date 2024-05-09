:original_name: evs_faq_0097.html

.. _evs_faq_0097:

Do I Need to Stop the Server Before Performing a Disk Backup?
=============================================================

No. You can back up disks when the server is in use. When a server is running, data is written into disks on the server, and some newly generated data is cached in the server memory. During a backup task, data in the memory will not be automatically written into disks, so the disk data and their backups may be inconsistent.

To ensure data integrity, you are advised to perform the backup during off-peak hours when no data is written to the disks.
