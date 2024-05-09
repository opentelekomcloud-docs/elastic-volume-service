:original_name: evs_faq_0073.html

.. _evs_faq_0073:

How Do I Extend the File System of an Unpartitioned Data Disk in Linux?
=======================================================================

Scenarios
---------

If no partition but only a file system is created on a data disk, extend the file system according to the following operations:

Run the **lsblk** command. Information similar to the following is displayed:

.. code-block:: console

   [root@ecs-test ~]# lsblk
   NAME     MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
   vda      253:0    0   40G  0 disk
   └─vda1 253:1    0   40G  0 part /
   vdb      253:16   0   60G  0 disk /mnt/sdc

In the command output, no partition but only a file system is created on data disk **/dev/vdb**.

In the following example, CentOS 7.4 64bit is used as the sample OS, data disk **/dev/vdb** has 10 GiB, no partition but only a file system is created on the disk, and additional 50 GiB has been added to this data disk on the management console. The following steps show how to extend this 50 GiB to the file system.

-  :ref:`Extending the EXT* File System <evs_faq_0073__en-us_topic_0241810111_en-us_topic_0240716537_section63374919338>`
-  :ref:`Extending the XFS File System <evs_faq_0073__en-us_topic_0241810111_en-us_topic_0240716537_section1248016813484>`

The way you allocate additional space depends on the OS. This example is used for reference only. For the detailed operations and differences, see the corresponding OS documentations.

.. _evs_faq_0073__en-us_topic_0241810111_en-us_topic_0240716537_section63374919338:

Extending the EXT\* File System
-------------------------------

#. Run the following command to extend the file system:

   **resize2fs** *Disk name*

   In this example, run the following command:

   **resize2fs /dev/vdb**

   Information similar to the following is displayed:

   .. code-block:: console

      [root@ecs-test ~]# resize2fs /dev/vdb
      resize2fs 1.42.9 (28-Dec-2013)
      Filesystem at /dev/vdb is mounted on /root/test; on-line resizing required
      old_desc_blocs = 2, old_desc_blocs = 8
      [17744.521535] EXT4-fs (vdb): resizing filesystem from 26214400 to 15728640 blocks
      [17744.904470] EXT4-fs (vdb): resized filesystem to 15728640
      The filesystem on /dev/vdb is now 15728640 blocks long.

#. Run the following command to view the result:

   **df -TH**

   Information similar to the following is displayed:

   .. code-block:: console

      [root@ecs-test ~]# df -TH
      Filesystem     Type      Size  Used Avail Use% Mounted on
      /dev/vda1      ext4       43G  1.9G   39G   5% /
      devtmpfs       devtmpfs  2.0G     0  2.0G   0% /dev
      tmpfs          tmpfs     2.0G     0  2.0G   0% /dev/shm
      tmpfs          tmpfs     2.0G  9.1M  2.0G   1% /run
      tmpfs          tmpfs     2.0G     0  2.0G   0% /sys/fs/cgroup
      tmpfs          tmpfs     398M     0  398M   0% /run/user/0
      /dev/vdb       ext4       64G   55M   61G   1% /mnt/sdc

.. _evs_faq_0073__en-us_topic_0241810111_en-us_topic_0240716537_section1248016813484:

Extending the XFS File System
-----------------------------

#. Run the following command to extend the file system:

   **xfs_growfs** *Disk name*

   In this example, run the following command:

   **xfs_growfs** **/dev/vdb**

   Information similar to the following is displayed:

   .. code-block:: console

      [root@ecs-test ~]# xfs_growfs /dev/vdb
      meta-data=/dev/vdb               isize=512     agcount=4, agsize=655360 blks
               =                       sectsz=512    attr=2, projid32bit=1
               =                       crc=1         finobt=0, spinodes=0
      data     =                       bsize=4096    blocks=2621440, imaxpct=25
               =                       sunit=0       swidth=0 blks
      naming   =version2               bsize=4096    ascii-ci=0 ftype=1
      log      =internal               bsize=4096    blocks=2560, version=2
               =                       sectsz=512    sunit=0 blks, lazy-count=1
      realtime =none                   extsz=4096    blocks=0, rtextents=0
      data blocks changed from 2621440 to 15728640.

#. Run the following command to view the result:

   **df -TH**

   Information similar to the following is displayed:

   .. code-block:: console

      [root@ecs-test ~]# df -TH
      Filesystem     Type      Size  Used Avail Use% Mounted on
      /dev/vda1      ext4       40G  2.3G   35G   7% /
      devtmpfs       devtmpfs  1.9G     0  1.9G   0% /dev
      tmpfs          tmpfs     1.9G     0  1.9G   0% /dev/shm
      tmpfs          tmpfs     1.9G  8.6M  1.9G   1% /run
      tmpfs          tmpfs     1.9G     0  1.9G   0% /sys/fs/cgroup
      tmpfs          tmpfs     379M     0  379M   0% /run/user/0
      /dev/vdb       xfs        60G   34M   60G   1% /mnt/sdc
