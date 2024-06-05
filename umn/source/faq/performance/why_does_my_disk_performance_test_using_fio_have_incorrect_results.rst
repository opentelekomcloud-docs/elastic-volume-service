:original_name: evs_faq_0080.html

.. _evs_faq_0080:

Why Does My Disk Performance Test Using Fio Have Incorrect Results?
===================================================================

Symptom
-------

You have followed the test performance method, but the test results do not meet expectations.

Troubleshooting
---------------

During a disk performance test, the disk and stress test conditions play an important role.

Possible causes are listed here in order of their probability.

If the fault persists after you have ruled out one cause, move on to the next one in the list.

.. important::

   Some operations may result in data loss. It is recommended that you use raw disks for performance test.


.. figure:: /_static/images/en-us_image_0000001080217203.png
   :alt: **Figure 1** Troubleshooting

   **Figure 1** Troubleshooting

.. table:: **Table 1** Troubleshooting

   +-----------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Possible Cause                                            | Solution                                                                                                                                                            |
   +===========================================================+=====================================================================================================================================================================+
   | The partition's start sector number is not 4-KiB aligned. | Go to :ref:`Check Whether Partition's Start Sector Number Is 4-KiB Aligned <evs_faq_0080__en-us_topic_0000001073763031_en-us_topic_0267670624_section83925230328>`. |
   |                                                           |                                                                                                                                                                     |
   |                                                           | Delete the partition and select a 4-KiB aligned start sector number for the new partition.                                                                          |
   +-----------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | The disk used in testing was not a raw disk.              | Purchase an empty disk and attach it to a server for testing.                                                                                                       |
   +-----------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Stress test conditions were not properly set.             | Configure multi-core processing and arrange queues properly to maximize the concurrent performance.                                                                 |
   +-----------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | An inappropriate data block size was used.                | Set a suitable data block size.                                                                                                                                     |
   |                                                           |                                                                                                                                                                     |
   |                                                           | -  When testing the disk IOPS, set the data block size to a small value, for example, 4 KiB.                                                                        |
   |                                                           | -  When testing the disk throughput, set the data block size to a large value, for example, 1024 KiB.                                                               |
   +-----------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _evs_faq_0080__en-us_topic_0000001073763031_en-us_topic_0267670624_section83925230328:

Check Whether Partition's Start Sector Number Is 4-KiB Aligned
--------------------------------------------------------------

#. Log in to the server and switch to user **root**.

#. Before you start the test, run the following command to check whether the start sector number is 4-KiB aligned:

   **fdisk -lu**

   Information similar to the following is displayed:

   .. code-block:: console

      [root@ecs-centos sdc]# fdisk -lu

      Disk /dev/xvda: 10.7 GiB, 10737418240 bytes, 20971520 sectors
      Units = sectors of 1 * 512 = 512 bytes
      Sector size (logical/physical): 512 bytes / 512 bytes
      I/O size (minimum/optimal): 512 bytes / 512 bytes
      Disk label type: dos
      Disk identifier: 0x7db77aa5

         Device Boot      Start         End      Blocks   Id  System
      /dev/xvda1   *        2048    20968919    10483436   83  Linux

      Disk /dev/xvdb: 10.7 GiB, 10737418240 bytes, 20971520 sectors
      Units = sectors of 1 * 512 = 512 bytes
      Sector size (logical/physical): 512 bytes / 512 bytes
      I/O size (minimum/optimal): 512 bytes / 512 bytes


      Disk /dev/xvdc: 53.7 GiB, 53687091200 bytes, 104857600 sectors
      Units = sectors of 1 * 512 = 512 bytes
      Sector size (logical/physical): 512 bytes / 512 bytes
      I/O size (minimum/optimal): 512 bytes / 512 bytes
      Disk label type: dos
      Disk identifier: 0x3cf3265c

         Device Boot      Start         End      Blocks   Id  System
      /dev/xvdc1            2048    41943039    20970496   83  Linux

   -  If 8 can be divided by the start sector number, the number is 4-KiB aligned.
   -  If 8 cannot be divided by the start sector number, the number is not 4-KiB aligned. Delete the partition and select a 4-KiB aligned start sector number for the new partition before continuing the test.

      .. important::

         If you delete the partition and select another start sector number for 4-KiB alignment, you will lose all the data on that partition. Exercise caution when performing this operation.
