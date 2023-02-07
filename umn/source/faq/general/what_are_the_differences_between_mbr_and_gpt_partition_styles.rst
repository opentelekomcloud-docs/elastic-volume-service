:original_name: evs_faq_0092.html

.. _evs_faq_0092:

What Are the Differences Between MBR and GPT Partition Styles?
==============================================================

:ref:`Table 1 <evs_faq_0092__table2729705994129>` lists the common disk partition styles. In Linux, different partition styles require different partitioning tools.

.. _evs_faq_0092__table2729705994129:

.. table:: **Table 1** Disk partition styles

   +----------------------------+---------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------+
   | Disk Partition Style       | Maximum Disk Capacity Supported | Maximum Number of Partitions Supported                                                                                                                                                                                                                     | Linux Partitioning Tool                    |
   +============================+=================================+============================================================================================================================================================================================================================================================+============================================+
   | Master Boot Record (MBR)   | 2 TiB                           | -  4 primary partitions                                                                                                                                                                                                                                    | You can use either of the following tools: |
   |                            |                                 | -  3 primary partitions and 1 extended partition                                                                                                                                                                                                           |                                            |
   |                            |                                 |                                                                                                                                                                                                                                                            | -  fdisk                                   |
   |                            |                                 | With MBR, you can create several primary partitions and one extended partition. The extended partition must be divided into logical partitions before use. For example, if 6 partitions need to be created, you can create them in the following two ways: | -  parted                                  |
   |                            |                                 |                                                                                                                                                                                                                                                            |                                            |
   |                            |                                 | -  3 primary partitions and 1 extended partition, with the extended partition divided into 3 logical partitions                                                                                                                                            |                                            |
   |                            |                                 | -  1 primary partition and 1 extended partition, with the extended partition divided into 5 logical partitions                                                                                                                                             |                                            |
   +----------------------------+---------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------+
   | Guid Partition Table (GPT) | 18 EiB                          | Unlimited                                                                                                                                                                                                                                                  | parted                                     |
   |                            |                                 |                                                                                                                                                                                                                                                            |                                            |
   |                            | 1 EiB = 1048576 TiB             | Disk partitions created using GPT are not categorized.                                                                                                                                                                                                     |                                            |
   +----------------------------+---------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------+

.. important::

   The maximum disk size supported by MBR is 2 TiB, and that supported by GPT is 18 EiB. Because an EVS data disk currently supports up to 32 TiB, use GPT if your disk size is larger than 2 TiB.

   If you change the partition style after the disk has been used, the data on the disk will be cleared. Therefore, select an appropriate partition style when initializing the disk.
