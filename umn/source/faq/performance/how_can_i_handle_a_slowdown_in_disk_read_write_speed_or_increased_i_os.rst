:original_name: evs_faq_0081.html

.. _evs_faq_0081:

How Can I Handle a Slowdown in Disk Read/Write Speed or Increased I/Os?
=======================================================================

**Symptom**

If you are aware of a service slowdown, depending on if you are examining a Windows or Linux server, you can take the following actions:

-  Windows: Open **Task Manager** and view the average response time.
-  Linux: Run **iostat -dx** to view the I/O performance.

If the disk read/write speed is slowed down, disk I/O increases, or the await time increases, the disk is likely to encounter a performance bottleneck.

**Solution**

Method 1: Change to a disk type with a higher specification. For details, see :ref:`Changing the EVS Disk Type (Beta) <evs_01_0062>`.

Method 2: Create a new disk from a disk backup to retain the disk data. The procedure is as follows:

#. Create a backup for the disk.


   .. figure:: /_static/images/en-us_image_0000002375826581.png
      :alt: **Figure 1** Create Backup

      **Figure 1** Create Backup

#. Create a new disk from this backup. During the creation, select a new disk type and configure advanced settings (sharing, SCSI, and encryption) based on your service requirements.


   .. figure:: /_static/images/en-us_image_0000002342028550.png
      :alt: **Figure 2** Create from backup

      **Figure 2** Create from backup
