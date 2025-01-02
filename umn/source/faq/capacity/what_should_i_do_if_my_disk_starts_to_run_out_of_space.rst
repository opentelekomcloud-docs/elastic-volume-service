:original_name: evs_faq_0032.html

.. _evs_faq_0032:

What Should I Do If My Disk Starts to Run Out of Space?
=======================================================

If your disk space starts to fill up, you can:

#. Create a new disk and attach it to the server. For details, see :ref:`Creating an EVS Disk <en-us_topic_0021738346>`.

#. Expand the capacity of the existing disk. Both system disks and data disks can be expanded. An expansion operation includes two steps:

   a. Expand the disk capacity on the console.
   b. Log in to the server and extend the partition and file system.

   For details, see :ref:`Expanding EVS Disk Capacity <evs_01_0059>`.

#. Free up the space on the disk. For details, see :ref:`How Do I Clean Up My Disk Space on a Windows Server? <evs_02_0010>`

Differences Between Expanding an EVS Disk and Creating an EVS Disk
------------------------------------------------------------------

The differences are as follows:

-  Expanding an EVS disk is when you expand the capacity of an existing EVS disk. Some systems let you expand the capacity of EVS disks in use. In this case, services are not interrupted.
-  If you create a new EVS disk and attach it to a server that already has an existing EVS disk, the new EVS disk and the original EVS disk are attached to the same server but independent from each other.
