:original_name: evs_faq_0024.html

.. _evs_faq_0024:

What Should I Do If My Disk Capacity Exceeds 2 TB After Expansion?
==================================================================

An EVS system disk can be as large as 1 TB (1024 GB). You can expand the capacity of a system disk to up to 1 TB.

An EVS data disk can be as large as 32 TB (32768 GB).

-  With MBR, any disk space in excess of 2 TB cannot be allocated and used, because the maximum disk capacity supported by MBR is 2 TB (2048 GB).

   In this case, if you want to expand the disk capacity to over 2 TB, change the partition style from MBR to GPT. Ensure that the disk data has been backed up before changing the partition style because services will be interrupted and data on the disk will be deleted during this change.

-  With GPT, you can expand the capacity of a data disk to up to 32 TB because the maximum disk capacity supported by GPT is 18 EB (19,327,352,832 GB).

   If the in-use partition style is GPT, see the following materials for details on how to extend the capacity:

   -  Windows:

      :ref:`Extending Disk Partitions and File Systems (Windows Server 2008) <en-us_topic_0017616396>`

   -  Linux:

      :ref:`Extending Partitions and File Systems for Data Disks (Linux) <evs_01_0109>`
