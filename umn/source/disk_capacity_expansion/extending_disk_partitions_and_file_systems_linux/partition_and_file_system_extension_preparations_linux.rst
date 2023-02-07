:original_name: evs_01_0035.html

.. _evs_01_0035:

Partition and File System Extension Preparations (Linux)
========================================================

Before extending the disk partition and file system, you must check the disk partition style and file system format, and then select the appropriate operation accordingly.

#. To view the disk partition style, see the following methods:

   -  :ref:`Method 1: Check Partition Style and File System Format Using fdisk <evs_01_0035__section45741613172812>`
   -  :ref:`Method 2: Check Partition Style and File System Format Using parted <evs_01_0035__section7627683297>`

#. To select the appropriate operation, see :ref:`Table 1 <evs_01_0035__table45743268308>`.

   .. _evs_01_0035__table45743268308:

   .. table:: **Table 1** Disk partition and file system extension scenarios

      +-----------------------+-------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------+
      | Disk                  | Scenario                                                    | Method                                                                                                               |
      +=======================+=============================================================+======================================================================================================================+
      | System disk           | Create a new MBR partition with the additional space.       | :ref:`Creating a New MBR Partition <evs_01_0072__section9194153012119>`                                              |
      +-----------------------+-------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------+
      |                       | Allocate the additional space to an existing MBR partition. | -  :ref:`Extending an Existing MBR Partition (Kernel Version Later Than 3.6.0) <evs_01_0072__section143412109355>`   |
      |                       |                                                             | -  :ref:`Extending an Existing MBR Partition (Kernel Version Earlier Than 3.6.0) <evs_01_0072__section158762021831>` |
      +-----------------------+-------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------+
      | Data disk             | Create a new MBR partition with the additional space.       | :ref:`Creating a New MBR Partition <evs_01_0109__section20200028194016>`                                             |
      +-----------------------+-------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------+
      |                       | Allocate the additional space to an existing MBR partition. | :ref:`Extending an Existing MBR Partition <evs_01_0109__section31113372194023>`                                      |
      +-----------------------+-------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------+
      |                       | Create a new GPT partition with the additional space.       | :ref:`Creating a New GPT Partition <evs_01_0109__section15940163415487>`                                             |
      +-----------------------+-------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------+
      |                       | Allocate the additional space to an existing GPT partition. | :ref:`Extending an Existing GPT Partition <evs_01_0109__section13346184710300>`                                      |
      +-----------------------+-------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------+
      | SCSI data disk        | Create a new MBR partition with the additional space.       | :ref:`Creating a New MBR Partition <evs_01_0018__section12265143819280>`                                             |
      +-----------------------+-------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------+
      |                       | Allocate the additional space to an existing MBR partition. | :ref:`Extending an Existing MBR Partition <evs_01_0018__section31113372194023>`                                      |
      +-----------------------+-------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------+

   .. note::

      The maximum disk capacity that MBR supports is 2 TiB, and the disk space exceeding 2 TiB cannot be used.

      If your disk uses MBR and you need to expand the disk capacity to over 2 TiB, change the partition style from MBR to GPT. Ensure that the disk data has been backed up before changing the partition style because services will be interrupted and data on the disk will be cleared during this change.

.. _evs_01_0035__section45741613172812:

Method 1: Check Partition Style and File System Format Using fdisk
------------------------------------------------------------------

#. .. _evs_01_0035__li4640174163019:

   Run the following command to view all the disks attached to the server:

   **lsblk**

   Information similar to the following is displayed:

   .. code-block:: console

      [root@ecs-test-0001 ~]# lsblk
      NAME   MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
      vda    253:0    0   40G  0 disk
      └─vda1 253:1    0   40G  0 part /
      vdb    253:16   0  150G  0 disk
      └─vdb1 253:17   0  100G  0 part /mnt/sdc

   In this example, data disk **/dev/vdb** already has partition **/dev/vdb1** before capacity expansion, and the additional 50 GiB added has not been allocated yet. Therefore, **/dev/vdb** has 150 GiB, and **/dev/vdb1** has 100 GiB.

#. Run the following command to view the current disk partition style:

   **fdisk -l**

   Information similar to the following is displayed:

   .. code-block:: console

      [root@ecs-test-0001 ~]# fdisk -l

      Disk /dev/vda: 42.9 GB, 42949672960 bytes, 83886080 sectors
      Units = sectors of 1 * 512 = 512 bytes
      Sector size (logical/physical): 512 bytes / 512 bytes
      I/O size (minimum/optimal): 512 bytes / 512 bytes
      Disk label type: dos
      Disk identifier: 0x000bcb4e

         Device Boot      Start         End      Blocks   Id  System
      /dev/vda1   *        2048    83886079    41942016   83  Linux

      Disk /dev/vdb: 161.1 GB, 161061273600 bytes, 314572800 sectors
      Units = sectors of 1 * 512 = 512 bytes
      Sector size (logical/physical): 512 bytes / 512 bytes
      I/O size (minimum/optimal): 512 bytes / 512 bytes
      Disk label type: dos
      Disk identifier: 0x38717fc1

         Device Boot      Start         End      Blocks   Id  System
      /dev/vdb1            2048   209715199   104856576   83  Linux

   The value in the **System** column indicates the disk partition style. Value **Linux** indicates the MBR partition style. Value **GPT** indicates the GPT partition style.

   -  If the disk partitions displayed are inconsistent with those obtained in :ref:`1 <evs_01_0035__li4640174163019>`, the partition that is not displayed uses the GPT partition style and has unallocated space. In this case, you cannot query all the partition information using the **fdisk -l** command. Go to :ref:`Method 2: Check Partition Style and File System Format Using parted <evs_01_0035__section7627683297>`.
   -  If the disk partitions displayed are consistent with those obtained in :ref:`1 <evs_01_0035__li4640174163019>`, continue with the following operations.

#. Run the following command to view the partition's file system format:

   **blkid** *Disk partition*

   In this example, run the following command:

   **blkid /dev/vdb1**

   In the command output, the **TYPE** value is **ext4**, indicating that **/dev/vdb1**'s file system format is **ext4**.

#. Run the following command to view the file system status:

   ext*: **e2fsck -n** *Disk partition*

   xfs: **xfs_repair -n** *Disk partition*

   In this example, the ext4 file system is used. Therefore, run the following command:

   **e2fsck -n /dev/vdb1**

   Information similar to the following is displayed:

   .. code-block:: console

      [root@ecs-test-0001 ~]# e2fsck -n /dev/vdb1
      e2fsck 1.42.9 (28-Dec-2013)
      Warning!  /dev/vdb1 is mounted.
      Warning: skipping journal recovery because doing a read-only filesystem check.
      /dev/vdb1: clean, 11/6553600 files, 459544/26214144 blocks

   If the file system status is **clean**, the file system status is normal. Otherwise, rectify the faulty and then perform the capacity expansion.

.. _evs_01_0035__section7627683297:

Method 2: Check Partition Style and File System Format Using parted
-------------------------------------------------------------------

#. Run the following command to view all the disks attached to the server:

   **lsblk**

   Information similar to the following is displayed:

   .. code-block:: console

      [root@ecs-test-0001 ~]# lsblk
      NAME   MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
      vda    253:0    0   40G  0 disk
      └─vda1 253:1    0   40G  0 part /
      vdb    253:16   0  150G  0 disk
      └─vdb1 253:17   0  100G  0 part /mnt/sdc

   In this example, data disk **/dev/vdb** already has partition **/dev/vdb1** before capacity expansion, and the additional 50 GiB added has not been allocated yet. Therefore, **/dev/vdb** has 150 GiB, and **/dev/vdb1** has 100 GiB.

#. Run the following command and enter **p** to view the disk partition style:

   **parted** *Disk*

   For example, run the following command to view **/dev/vdb**'s partition style:

   **parted /dev/vdb**

   Information similar to the following is displayed:

   .. code-block:: console

      [root@ecs-test-0001 ~]# parted /dev/vdb
      GNU Parted 3.1
      Using /dev/vdb
      Welcome to GNU Parted! Type 'help' to view a list of commands.
      (parted) p
      Error: The backup GPT table is not at the end of the disk, as it should be.  This might mean that another operating system believes the
      disk is smaller.  Fix, by moving the backup to the end (and removing the old backup)?
      Fix/Ignore/Cancel? Fix
      Warning: Not all of the space available to /dev/vdb appears to be used, you can fix the GPT to use all of the space (an extra 104857600
      blocks) or continue with the current setting?
      Fix/Ignore? Fix
      Model: Virtio Block Device (virtblk)
      Disk /dev/vdb: 161GB
      Sector size (logical/physical): 512B/512B
      Partition Table: gpt
      Disk Flags:

      Number  Start   End    Size   File system  Name  Flags
       1      1049kB  107GB  107GB  ext4         test

      (parted)

   In the command output, parameter **Partition Table** indicates the disk partition style. Value **msdos** indicates the MBR partition style, and value **gpt** indicates the GPT partition style.

   -  If the following error information is displayed, enter **Fix**.

      .. code-block::

         Error: The backup GPT table is not at the end of the disk, as it should be.  This might mean that another operating system believes the
         disk is smaller.  Fix, by moving the backup to the end (and removing the old backup)?

      The GPT partition table information is stored at the start of the disk. To reduce the risk of damage, a backup of the information is saved at the end of the disk. When you expand the disk capacity, the end of the disk changes accordingly. In this case, enter **Fix** to move the backup file of the information to new disk end.

   -  If the following warning information is displayed, enter **Fix**.

      .. code-block::

         Warning: Not all of the space available to /dev/vdb appears to be used, you can fix the GPT to use all of the space (an extra 104857600
         blocks) or continue with the current setting?
         Fix/Ignore? Fix

      Enter **Fix** as prompted. The system automatically sets the GPT partition style for the additional space.

#. Enter **q** and press **Enter** to exit parted.
