:original_name: evs_faq_0035.html

.. _evs_faq_0035:

What Should I Do If I Use fdisk to Initialize a Disk Larger Than 2 TB and Then the Space in Excess of 2 TB Cannot Be Displayed?
===============================================================================================================================

If your disk capacity is greater than 2 TB, do not use fdisk to partition the disk. Or any space in excess of 2 TB will be unable to be displayed after the disk is partitioned.

In this case, use parted to repartition the disk and choose the GPT partition style because MBR does not support disks over 2 TB.

For details, see :ref:`Introduction to Data Disk Initialization Scenarios and Partition Styles <evs_01_0038>`.
