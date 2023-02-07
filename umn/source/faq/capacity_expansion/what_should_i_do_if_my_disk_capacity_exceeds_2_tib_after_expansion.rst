:original_name: evs_faq_0024.html

.. _evs_faq_0024:

What Should I Do If My Disk Capacity Exceeds 2 TiB After Expansion?
===================================================================

An EVS system disk can be as large as 1 TiB (1,024 GiB). You can expand the capacity of a system disk to up to 1 TiB.

An EVS data disk can be as large as 32 TiB (32,768 GiB).

-  With MBR, any disk space in excess of 2 TiB cannot be allocated and used, because the maximum disk capacity supported by MBR is 2 TiB (2,048 GiB).

   In this case, if you want to expand the disk capacity to over 2 TiB, change the partition style from MBR to GPT. Ensure that the disk data has been backed up before changing the partition style because services will be interrupted and data on the disk will be deleted during this change.

-  With GPT, you can expand the capacity of a data disk to up to 32 TiB because the maximum disk capacity supported by GPT is 18 EiB (19,327,352,832 GiB).

   If the in-use partition style is GPT, see the following methods:

   -  Windows:

      Extending Disk Partitions and File Systems (Windows Server 2016)

   -  Linux:

      Extending Partitions and File Systems for Data Disks (Linux)
