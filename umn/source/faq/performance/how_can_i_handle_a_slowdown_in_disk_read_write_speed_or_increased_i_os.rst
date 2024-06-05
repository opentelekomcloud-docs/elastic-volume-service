:original_name: evs_faq_0081.html

.. _evs_faq_0081:

How Can I Handle a Slowdown in Disk Read/Write Speed or Increased I/Os?
=======================================================================

**Symptom**

If you are aware of a service slowdown, depending on if you are examining a Windows or Linux server, you can take the following actions:

-  Windows: Open **Task Manager** and view the average response time.
-  Linux: Run **iostat -dx** to view the I/O performance.

If the disk read/write speed is slowed down, disk I/O increases, or the await time increases, the disk is likely encounters a performance bottleneck.

**Solution**

It is recommended that you change to a disk type with a higher specification. .
