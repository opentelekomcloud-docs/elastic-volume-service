:original_name: evs_01_0109.html

.. _evs_01_0109:

Extending Partitions and File Systems for Data Disks (Linux)
============================================================

Scenarios
---------

After a disk has been expanded on the management console, the disk size is enlarged, but the additional space cannot be used directly.

In Linux, you must allocate the additional space to an existing partition or a new partition.

This section uses CentOS 7.4 64bit as the sample OS to describe how to extend an MBR or GPT partition. The method for allocating the additional space varies with the server OS. This section is used for reference only. For detailed operations and differences, see the corresponding OS documents.

-  :ref:`Creating a New MBR Partition <evs_01_0109__section20200028194016>`
-  :ref:`Extending an Existing MBR Partition <evs_01_0109__section31113372194023>`
-  :ref:`Creating a New GPT Partition <evs_01_0109__section15940163415487>`
-  :ref:`Extending an Existing GPT Partition <evs_01_0109__section13346184710300>`

.. important::

   Performing the expansion operations with caution. Misoperation may lead to data loss or exceptions. Therefore, you are advised to back up the disk data using CBR or snapshots before expansion. For details about using CBR, see :ref:`Managing EVS Backups <evs_01_0110>`. For details about using snapshots, see :ref:`Creating a Snapshot <en-us_topic_0066615262>`.

Prerequisites
-------------

-  You have expanded the disk capacity and attached the disk to a server on the management console. For details, see :ref:`Expanding Capacity for an In-use EVS Disk <evs_01_0007>` or :ref:`Expanding Capacity for an Available EVS Disk <evs_01_0008>`.
-  You have logged in to the server.

   -  For how to log in to an ECS, see the *Elastic Cloud Server User Guide*.
   -  For how to log in to a BMS, see the *Bare Metal Server User Guide*.

Constraints
-----------

The additional space cannot be added to the root partition of a data disk. To extend the root partition, expand the system disk instead.

.. _evs_01_0109__section20200028194016:

Creating a New MBR Partition
----------------------------

Originally, data disk **/dev/vdb** has 100 GiB and one partition (**/dev/vdb1**), and then 50 GiB is added to the disk. The following procedure shows you how to create a new MBR partition **/dev/vdb2** with this 50 GiB.

#. Run the following command to view the disk partition information:

   **fdisk** **-l**

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

#. Run the following command to enter fdisk:

   **fdisk** *Disk*

   In this example, run the following command:

   **fdisk** **/dev/vdb**

   Information similar to the following is displayed:

   .. code-block:: console

      [root@ecs-test-0001 ~]# fdisk /dev/vdb
      Welcome to fdisk (util-linux 2.23.2).

      Changes will remain in memory only, until you decide to write them.
      Be careful before using the write command.


      Command (m for help):

#. Enter **n** and press **Enter** to create a new partition.

   Information similar to the following is displayed:

   .. code-block::

      Command (m for help): n
      Partition type:
         p   primary (1 primary, 0 extended, 3 free)
         e   extended
      Select (default p):

   There are two types of disk partitions:

   -  Choosing **p** creates a primary partition.
   -  Choosing **e** creates an extended partition.

   .. note::

      If the MBR partition style is used, a maximum of 4 primary partitions, or 3 primary partitions and 1 extended partition can be created. The extended partition cannot be used directly and must be divided into logical partitions before use.

      Disk partitions created using GPT are not categorized.

#. In this example, a primary partition is created. Therefore, enter **p** and press **Enter** to create a primary partition.

   Information similar to the following is displayed:

   .. code-block::

      Select (default p): p
      Partition number (2-4, default 2):

   **Partition number** indicates the serial number of the primary partition. Because partition number 1 has been used, the value ranges from **2** to **4**.

#. Enter the serial number of the primary partition and press **Enter**. Partition number **2** is used in this example. Therefore, enter **2** and press **Enter.**

   Information similar to the following is displayed:

   .. code-block::

      Partition number (2-4, default 2): 2
      First sector (209715200-314572799, default 209715200):

   **First sector** indicates the start sector. The value ranges from **209715200** to **314572799**, and the default value is **209715200**.

#. Enter the new partition's start sector and press **Enter**. In this example, the default start sector is used.

   The system displays the start and end sectors of the partition's available space. You can customize the value within this range or use the default value. The start sector must be smaller than the partition's end sector.

   Information similar to the following is displayed:

   .. code-block::

      First sector (209715200-314572799, default 209715200):
      Using default value 209715200
      Last sector, +sectors or +size{K,M,G} (209715200-314572799, default 314572799):

   **Last sector** indicates the end sector. The value ranges from **209715200** to **314572799**, and the default value is **314572799**.

#. Enter the new partition's end sector and press **Enter**. In this example, the default end sector is used.

   The system displays the start and end sectors of the partition's available space. You can customize the value within this range or use the default value. The start sector must be smaller than the partition's end sector.

   Information similar to the following is displayed:

   .. code-block::

      Last sector, +sectors or +size{K,M,G} (209715200-314572799, default 314572799):
      Using default value 314572799
      Partition 2 of type Linux and of size 50 GiB is set

      Command (m for help):

#. Enter **p** and press **Enter** to view the new partition.

   Information similar to the following is displayed:

   .. code-block::

      Command (m for help): p

      Disk /dev/vdb: 161.1 GB, 161061273600 bytes, 314572800 sectors
      Units = sectors of 1 * 512 = 512 bytes
      Sector size (logical/physical): 512 bytes / 512 bytes
      I/O size (minimum/optimal): 512 bytes / 512 bytes
      Disk label type: dos
      Disk identifier: 0x38717fc1

         Device Boot      Start         End      Blocks   Id  System
      /dev/vdb1            2048   209715199   104856576   83  Linux
      /dev/vdb2       209715200   314572799    52428800   83  Linux

      Command (m for help):

#. Enter **w** and press **Enter** to write the changes to the partition table.

   Information similar to the following is displayed:

   .. code-block::

      Command (m for help): w
      The partition table has been altered!

      Calling ioctl() to re-read partition table.

      WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
      The kernel still uses the old table. The new table will be used at
      the next reboot or after you run partprobe(8) or kpartx(8)
      Syncing disks.

   .. note::

      In case that you want to discard the changes made before, you can exit fdisk by entering **q**.

#. Run the following command to synchronize the new partition table to the OS:

   **partprobe**

#. Run the following command to set the file system format for the new partition:

   **mkfs** **-t** *File system* *Disk partition*

   -  Sample command of the ext\* file system:

      **mkfs** **-t** **ext4** **/dev/vdb2**

      Information similar to the following is displayed:

      .. code-block:: console

         [root@ecs-test-0001 ~]# mkfs -t ext4 /dev/vdb2
         mke2fs 1.42.9 (28-Dec-2013)
         Filesystem label=
         OS type: Linux
         Block size=4096 (log=2)
         Fragment size=4096 (log=2)
         Stride=0 blocks, Stripe width=0 blocks
         3276800 inodes, 13107200 blocks
         655360 blocks (5.00%) reserved for the super user
         First data block=0
         Maximum filesystem blocks=2162163712
         400 block groups
         32768 blocks per group, 32768 fragments per group
         8192 inodes per group
         Superblock backups stored on blocks:
                 32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
                 4096000, 7962624, 11239424

         Allocating group tables: done
         Writing inode tables: done
         Creating journal (32768 blocks): done
         Writing superblocks and filesystem accounting information: done

   -  Sample command of the xfs file system:

      **mkfs** **-t** **xfs** **/dev/vdb2**

      Information similar to the following is displayed:

      .. code-block:: console

         [root@ecs-test-0001 ~]# mkfs -t xfs /dev/vdb2
         meta-data=/dev/vdb2              isize=512     agcount=4, agsize=3276800 blks
                  =                       sectsz=512    attr=2, projid32bit=1
                  =                       crc=1         finobt=0, sparse=0
         data     =                       bsize=4096    blocks=13107200, imaxpct=25
                  =                       sunit=0       swidth=0 blks
         naming   =version2               bsize=4096    ascii-ci=0 ftype=1
         log      =internal log           bsize=4096    blocks=6400, version=2
                  =                       sectsz=512    sunit=0 blks, lazy-count=1
         realtime =none                   extsz=4096    blocks=0, rtextents=0

   The formatting takes a while, and you need to observe the system running status. Once **done** is displayed in the command output, the formatting is complete.

#. (Optional) Run the following command to create a mount point:

   Perform this step if you want to mount the partition on a new mount point.

   **mkdir** *Mount point*

   In this example, run the following command to create the **/mnt/test** mount point:

   **mkdir** **/mnt/test**

#. Run the following command to mount the new partition:

   **mount** *Disk partition* *Mount point*

   In this example, run the following command to mount the new partition **/dev/vdb2** on **/mnt/test**:

   **mount** **/dev/vdb2** **/mnt/test**

   .. note::

      If the new partition is mounted on a directory that is not empty, the subdirectories and files in the directory will be hidden. Therefore, you are advised to mount the new partition on an empty directory or a new directory. If the new partition must be mounted on a directory that is not empty, move the subdirectories and files in this directory to another directory temporarily. After the partition is successfully mounted, move the subdirectories and files back.

#. Run the following command to view the mount result:

   **df** **-TH**

   Information similar to the following is displayed:

   .. code-block:: console

      [root@ecs-test-0001 ~]# df -TH
      Filesystem     Type      Size  Used Avail Use% Mounted on
      /dev/vda1      ext4       43G  1.9G   39G   5% /
      devtmpfs       devtmpfs  2.0G     0  2.0G   0% /dev
      tmpfs          tmpfs     2.0G     0  2.0G   0% /dev/shm
      tmpfs          tmpfs     2.0G  9.1M  2.0G   1% /run
      tmpfs          tmpfs     2.0G     0  2.0G   0% /sys/fs/cgroup
      tmpfs          tmpfs     398M     0  398M   0% /run/user/0
      /dev/vdb1      ext4      106G   63M  101G   1% /mnt/sdc
      /dev/vdb2      ext4       53G   55M   50G   1% /mnt/test

   .. note::

      If the server is restarted, the mounting will become invalid. You can set automatic mounting for partitions at system start by modifying the **/etc/fstab** file. For details, see :ref:`Setting Automatic Mounting at System Start <evs_01_0109__section1107170115310>`.

.. _evs_01_0109__section31113372194023:

Extending an Existing MBR Partition
-----------------------------------

.. important::

   If the additional space is allocated to an existing partition, data on the disk will not be cleared but you must use **umount** to unmount the existing partition. In this case, services will be affected.

Originally, data disk **/dev/vdb** has 150 GiB and two partitions (**/dev/vdb1** and **/dev/vdb2**), and then 80 GiB is added to the disk. The following procedure shows you how to add this 80 GiB to the existing MBR partition **/dev/vdb2**.

.. important::

   During an expansion, the additional space is added to the end of the disk. Therefore, if the disk has multiple partitions, the additional space can only be allocated to the partition at the disk end.

#. .. _evs_01_0109__li6396237219479:

   Run the following command to view the disk partition information:

   **fdisk** **-l**

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

      Disk /dev/vdb: 247.0 GB, 246960619520 bytes, 482344960 sectors
      Units = sectors of 1 * 512 = 512 bytes
      Sector size (logical/physical): 512 bytes / 512 bytes
      I/O size (minimum/optimal): 512 bytes / 512 bytes
      Disk label type: dos
      Disk identifier: 0x38717fc1

         Device Boot      Start         End      Blocks   Id  System
      /dev/vdb1            2048   209715199   104856576   83  Linux
      /dev/vdb2       209715200   314572799    52428800   83  Linux

   In the command output, take note of the partition's start and end sectors. In this example, **/dev/vdb2**'s start sector is **209715200**, and its end sector is **314572799**.

   View the **/dev/vdb** capacity and check whether the additional space is included.

   -  If the additional space is not included, refresh the capacity according to :ref:`Extending Partitions and File Systems for SCSI Disks (Linux) <evs_01_0018>`.
   -  If the additional space is included, take note of the start and end sectors of the target partition and then go to :ref:`2 <evs_01_0109__li3879043619479>`. These values will be used in the subsequent operations.

#. .. _evs_01_0109__li3879043619479:

   Run the following command to unmount the partition:

   **umount** *Disk partition*

   In this example, run the following command:

   **umount** **/dev/vdb2**

#. Run the following command to enter fdisk:

   **fdisk** *Disk*

   In this example, run the following command:

   **fdisk** **/dev/vdb**

   Information similar to the following is displayed:

   .. code-block:: console

      [root@ecs-test-0001 ~]# fdisk /dev/vdb
      Welcome to fdisk (util-linux 2.23.2).

      Changes will remain in memory only, until you decide to write them.
      Be careful before using the write command.


      Command (m for help):

#. Run the following command to delete the partition to be extended:

   a. Enter **d** and press **Enter** to delete the partition.

      Information similar to the following is displayed:

      .. code-block::

         Command (m for help): d
         Partition number (1,2, default 2):

   b. Enter the partition number and press **Enter** to delete the partition. In this example, enter **2**.

      Information similar to the following is displayed:

      .. code-block::

         Partition number (1,2, default 2): 2
         Partition 2 is deleted

         Command (m for help):

      .. note::

         After deleting the partition, recreate the partition according to the following steps, and data on this disk will not be lost.

#. Enter **n** and press **Enter** to create a new partition.

   Information similar to the following is displayed:

   .. code-block::

      Command (m for help): n
      Partition type:
         p   primary (1 primary, 0 extended, 3 free)
         e   extended
      Select (default p):

   There are two types of disk partitions:

   -  Choosing **p** creates a primary partition.
   -  Choosing **e** creates an extended partition.

   .. note::

      If the MBR partition style is used, a maximum of 4 primary partitions, or 3 primary partitions and 1 extended partition can be created. The extended partition cannot be used directly and must be divided into logical partitions before use.

      Disk partitions created using GPT are not categorized.

#. Ensure that the entered partition type is the same as the partition had before. In this example, a primary partition is used. Therefore, enter **p** and press **Enter** to create a primary partition.

   Information similar to the following is displayed:

   .. code-block::

      Select (default p): p
      Partition number (2-4, default 2):

   **Partition number** indicates the serial number of the primary partition.

#. Ensure that entered partition number is the same as the partition had before. In this example, partition number **2** is used. Therefore, enter **2** and press **Enter**.

   Information similar to the following is displayed:

   .. code-block::

      Partition number (2-4, default 2): 2
      First sector (209715200-482344959, default 209715200):

   In the command output, **First sector** specifies the start sector.

   .. note::

      Data will be lost if the following operations are performed:

      -  Select a start sector other than the partition had before.
      -  Select an end sector smaller than the partition had before.

#. Ensure that the entered start sector is the same as the partition had before. In this example, start sector **209715200** is recorded in :ref:`1 <evs_01_0109__li6396237219479>`. Therefore, enter **209715200** and press **Enter**.

   Information similar to the following is displayed:

   .. code-block::

      First sector (209715200-482344959, default 209715200):
      Using default value 209715200
      Last sector, +sectors or +size{K,M,G} (209715200-482344959, default 482344959):

   In the command output, **Last sector** specifies the end sector.

#. Ensure that the entered end sector is larger than or equal to the end sector recorded in :ref:`1 <evs_01_0109__li6396237219479>`. In this example, the recorded end sector is **314572799**, and the default end sector is used. Therefore, enter **482344959** and press **Enter**.

   Information similar to the following is displayed:

   .. code-block::

      Using default value 209715200
      Last sector, +sectors or +size{K,M,G} (209715200-482344959, default 482344959):
      Using default value 482344959
      Partition 2 of type Linux and of size 130 GiB is set

      Command (m for help):

   The partition is created.

#. Enter **p** and press **Enter** to view the partition details.

   Information similar to the following is displayed:

   .. code-block::

      Command (m for help): p

      Disk /dev/vdb: 247.0 GB, 246960619520 bytes, 482344960 sectors
      Units = sectors of 1 * 512 = 512 bytes
      Sector size (logical/physical): 512 bytes / 512 bytes
      I/O size (minimum/optimal): 512 bytes / 512 bytes
      Disk label type: dos
      Disk identifier: 0x38717fc1

         Device Boot      Start         End      Blocks   Id  System
      /dev/vdb1            2048   209715199   104856576   83  Linux
      /dev/vdb2       209715200   482344959   136314880   83  Linux

      Command (m for help):

#. Enter **w** and press **Enter** to write the changes to the partition table.

   Information similar to the following is displayed:

   .. code-block::

      Command (m for help): w
      The partition table has been altered!

      Calling ioctl() to re-read partition table.

      WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
      The kernel still uses the old table. The new table will be used at
      the next reboot or after you run partprobe(8) or kpartx(8)
      Syncing disks.

   .. note::

      In case that you want to discard the changes made before, you can exit fdisk by entering **q**.

#. Run the following command to synchronize the new partition table to the OS:

   **partprobe**

#. Perform the following operations based on the file system of the disk:

   -  For the **ext**\ ``*`` file system

      a. Run the following command to check the correctness of the file system on the partition:

         **e2fsck** **-f** *Disk partition*

         In this example, run the following command:

         **e2fsck** **-f** **/dev/vdb2**

         Information similar to the following is displayed:

         .. code-block:: console

            [root@ecs-test-0001 ~]# e2fsck -f /dev/vdb2
            e2fsck 1.42.9 (28-Dec-2013)
            Pass 1: Checking inodes, blocks, and sizes
            Pass 2: Checking directory structure
            Pass 3: Checking directory connectivity
            Pass 4: Checking reference counts
            Pass 5: Checking group summary information
            /dev/vdb2: 11/3276800 files (0.0% non-contiguous), 251790/13107200 blocks

      b. Run the following command to extend the file system of the partition:

         **resize2fs** *Disk partition*

         In this example, run the following command:

         **resize2fs** **/dev/vdb2**

         Information similar to the following is displayed:

         .. code-block:: console

            [root@ecs-test-0001 ~]# resize2fs /dev/vdb2
            resize2fs 1.42.9 (28-Dec-2013)
            Resizing the filesystem on /dev/vdb2 to 34078720 (4k) blocks.
            The filesystem on /dev/vdb2 is now 34078720 blocks long.

      c. (Optional) Run the following command to create a mount point:

         Perform this step if you want to mount the partition on a new mount point.

         **mkdir** *Mount point*

         In this example, run the following command to create the **/mnt/test** mount point:

         **mkdir** **/mnt/test**

      d. Run the following command to mount the partition:

         **mount** *Disk partition* *Mount point*

         In this example, run the following command to mount partition **/dev/vdb2** on **/mnt/test**:

         **mount** **/dev/vdb2** **/mnt/test**

         .. note::

            If the new partition is mounted on a directory that is not empty, the subdirectories and files in the directory will be hidden. Therefore, you are advised to mount the new partition on an empty directory or a new directory. If the new partition must be mounted on a directory that is not empty, move the subdirectories and files in this directory to another directory temporarily. After the partition is successfully mounted, move the subdirectories and files back.

   -  For the **xfs** file system

      a. (Optional) Run the following command to create a mount point:

         Perform this step if you want to mount the partition on a new mount point.

         **mkdir** *Mount point*

         In this example, run the following command to create the **/mnt/test** mount point:

         **mkdir** **/mnt/test**

      b. Run the following command to mount the partition:

         **mount** *Disk partition* *Mount point*

         In this example, run the following command to mount partition **/dev/vdb2** on **/mnt/test**:

         **mount** **/dev/vdb2** **/mnt/test**

         .. note::

            If the new partition is mounted on a directory that is not empty, the subdirectories and files in the directory will be hidden. Therefore, you are advised to mount the new partition on an empty directory or a new directory. If the new partition must be mounted on a directory that is not empty, move the subdirectories and files in this directory to another directory temporarily. After the partition is successfully mounted, move the subdirectories and files back.

      c. Run the following command to extend the file system of the partition:

         **sudo** **xfs\_growfs** *Disk partition*

         In this example, run the following command:

         **sudo** **xfs\_growfs** **/dev/vdb2**

         Information similar to the following is displayed:

         .. code-block:: console

            [root@ecs-test-0001 ~]# sudo xfs_growfs /dev/vdb2
            meta-data=/dev/vdb2              isize=512     agcount=4, agsize=3276800 blks
                     =                       sectsz=512    attr=2, projid32bit=1
                     =                       crc=1         finobt=0, spinodes=0
            data     =                       bsize=4096    blocks=13107200, imaxpct=25
                     =                       sunit=0       swidth=0 blks
            naming   =version2               bsize=4096    ascii-ci=0 ftype=1
            log      =internal               bsize=4096    blocks=6400, version=2
                     =                       sectsz=512    sunit=0 blks, lazy-count=1
            realtime =none                   extsz=4096    blocks=0, rtextents=0
            data blocks changed from 13107200 to 34078720.

#. Run the following command to view the mount result:

   **df** **-TH**

   Information similar to the following is displayed:

   .. code-block:: console

      [root@ecs-test-0001 ~]# df -TH
      Filesystem     Type      Size  Used Avail Use% Mounted on
      /dev/vda1      ext4       43G  1.9G   39G   5% /
      devtmpfs       devtmpfs  2.0G     0  2.0G   0% /dev
      tmpfs          tmpfs     2.0G     0  2.0G   0% /dev/shm
      tmpfs          tmpfs     2.0G  9.1M  2.0G   1% /run
      tmpfs          tmpfs     2.0G     0  2.0G   0% /sys/fs/cgroup
      tmpfs          tmpfs     398M     0  398M   0% /run/user/0
      /dev/vdb1      ext4      106G   63M  101G   1% /mnt/sdc
      /dev/vdb2      ext4      138G   63M  131G   1% /mnt/test

   .. note::

      If the server is restarted, the mounting will become invalid. You can set automatic mounting for partitions at system start by modifying the **/etc/fstab** file. For details, see :ref:`Setting Automatic Mounting at System Start <evs_01_0109__section1107170115310>`.

.. _evs_01_0109__section15940163415487:

Creating a New GPT Partition
----------------------------

Originally, data disk **/dev/vdb** has 100 GiB and one partition (**/dev/vdb1**), and then 50 GiB is added to the disk. The following procedure shows you how to create a new GPT partition **/dev/vdb2** with this 50 GiB.

#. Run the following command to view the disk partition information:

   **lsblk**

   Information similar to the following is displayed:

   .. code-block:: console

      [root@ecs-test-0001 ~]# lsblk
      NAME   MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
      vda    253:0    0   40G  0 disk
      └─vda1 253:1    0   40G  0 part /
      vdb    253:16   0  150G  0 disk
      └─vdb1 253:17   0  100G  0 part /mnt/sdc

#. .. _evs_01_0109__li131751636184912:

   Run the following command to enter parted:

   **parted** *Disk*

   In this example, run the following command:

   **parted** **/dev/vdb**

   Information similar to the following is displayed:

   .. code-block:: console

      [root@ecs-test-0001 ~]# parted /dev/vdb
      GNU Parted 3.1
      Using /dev/vdb
      Welcome to GNU Parted! Type 'help' to view a list of commands.
      (parted)

#. Enter **unit s** and press **Enter** to set the measurement unit of the disk to sector.

#. .. _evs_01_0109__li317653664918:

   Enter **p** and press **Enter** to view the disk partition information.

   Information similar to the following is displayed:

   .. code-block::

      (parted) unit s
      (parted) p
      Error: The backup GPT table is not at the end of the disk, as it should be.  This might mean that another operating system believes the
      disk is smaller.  Fix, by moving the backup to the end (and removing the old backup)?
      Fix/Ignore/Cancel? Fix
      Warning: Not all of the space available to /dev/vdb appears to be used, you can fix the GPT to use all of the space (an extra 104857600
      blocks) or continue with the current setting?
      Fix/Ignore? Fix
      Model: Virtio Block Device (virtblk)
      Disk /dev/vdb: 314572800s
      Sector size (logical/physical): 512B/512B
      Partition Table: gpt
      Disk Flags:

      Number  Start  End         Size        File system  Name  Flags
       1      2048s  209713151s  209711104s  ext4         test

      (parted)

   In the command output, take note of the partition's end sector. In this example, the end sector of the **/dev/vdb1** partition is **209713151s**.

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

#. Run the following command and press **Enter**:

   **mkpart** *Partition name Start sector* *End sector*

   In this example, run the following command:

   **mkpart** **data** **209713152s** **100%**

   In this example, the additional space is used to create a new partition. In :ref:`4 <evs_01_0109__li317653664918>`, the end sector of partition **dev/vdb1** is **209713151s**. Therefore, the start sector of the new partition **dev/vdb2** is set to **209713152s** and the end sector **100%**. This start and end sectors are for reference only. You can plan the number of partitions and partition size based on service requirements.

   Information similar to the following is displayed:

   .. code-block::

      (parted) mkpart data 209713152s 100%
      (parted)

   .. note::

      The maximum sector can be obtained in either of the following ways:

      -  Query the disk's maximum end sector. For details, see :ref:`2 <evs_01_0109__li131751636184912>` to :ref:`4 <evs_01_0109__li317653664918>`.
      -  Enter **-1s** or **100%**, and the value displayed is the maximum end sector.

#. Enter **p** and press **Enter** to view the new partition.

   Information similar to the following is displayed:

   .. code-block::

      (parted) p
      Model: Virtio Block Device (virtblk)
      Disk /dev/vdb: 314572800s
      Sector size (logical/physical): 512B/512B
      Partition Table: gpt
      Disk Flags:

      Number  Start       End         Size        File system  Name  Flags
       1      2048s       209713151s  209711104s  ext4         test
       2      209713152s  314570751s  104857600s               data

      (parted)

#. Enter **q** and press **Enter** to exit parted.

   Information similar to the following is displayed:

   .. code-block::

      (parted) q
      Information: You may need to update /etc/fstab.

   You can set automatic disk mounting by updating the **/etc/fstab** file. Before updating the file, set the file system format for the partition and mount the partition on the mount point.

#. Run the following command to set the file system format for the new partition:

   **mkfs** **-t** *File system* *Disk partition*

   -  Sample command of the ext\* file system:

      **mkfs** **-t** **ext4** **/dev/vdb2**

      Information similar to the following is displayed:

      .. code-block:: console

         [root@ecs-test-0001 ~]# mkfs -t ext4 /dev/vdb2
         mke2fs 1.42.9 (28-Dec-2013)
         Filesystem label=
         OS type: Linux
         Block size=4096 (log=2)
         Fragment size=4096 (log=2)
         Stride=0 blocks, Stripe width=0 blocks
         3276800 inodes, 13107200 blocks
         655360 blocks (5.00%) reserved for the super user
         First data block=0
         Maximum filesystem blocks=2162163712
         400 block groups
         32768 blocks per group, 32768 fragments per group
         8192 inodes per group
         Superblock backups stored on blocks:
                 32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
                 4096000, 7962624, 11239424

         Allocating group tables: done
         Writing inode tables: done
         Creating journal (32768 blocks): done
         Writing superblocks and filesystem accounting information: done

   -  Sample command of the xfs file system:

      **mkfs** **-t** **xfs** **/dev/vdb2**

      Information similar to the following is displayed:

      .. code-block:: console

         [root@ecs-test-0001 ~]# mkfs -t xfs /dev/vdb2
         meta-data=/dev/vdb2              isize=512     agcount=4, agsize=3276800 blks
                  =                       sectsz=512    attr=2, projid32bit=1
                  =                       crc=1         finobt=0, sparse=0
         data     =                       bsize=4096    blocks=13107200, imaxpct=25
                  =                       sunit=0       swidth=0 blks
         naming   =version2               bsize=4096    ascii-ci=0 ftype=1
         log      =internal log           bsize=4096    blocks=6400, version=2
                  =                       sectsz=512    sunit=0 blks, lazy-count=1
         realtime =none                   extsz=4096    blocks=0, rtextents=0

   The formatting takes a while, and you need to observe the system running status. Once **done** is displayed in the command output, the formatting is complete.

#. (Optional) Run the following command to create a mount point:

   Perform this step if you want to mount the partition on a new mount point.

   **mkdir** *Mount point*

   In this example, run the following command to create the **/mnt/test** mount point:

   **mkdir** **/mnt/test**

#. Run the following command to mount the new partition:

   **mount** *Disk partition* *Mount point*

   In this example, run the following command to mount the new partition **/dev/vdb2** on **/mnt/test**:

   **mount** **/dev/vdb2** **/mnt/test**

   .. note::

      If the new partition is mounted on a directory that is not empty, the subdirectories and files in the directory will be hidden. Therefore, you are advised to mount the new partition on an empty directory or a new directory. If the new partition must be mounted on a directory that is not empty, move the subdirectories and files in this directory to another directory temporarily. After the partition is successfully mounted, move the subdirectories and files back.

#. Run the following command to view the mount result:

   **df** **-TH**

   Information similar to the following is displayed:

   .. code-block:: console

      [root@ecs-test-0001 ~]# df -TH
      Filesystem     Type      Size  Used Avail Use% Mounted on
      /dev/vda1      ext4       43G  1.9G   39G   5% /
      devtmpfs       devtmpfs  2.0G     0  2.0G   0% /dev
      tmpfs          tmpfs     2.0G     0  2.0G   0% /dev/shm
      tmpfs          tmpfs     2.0G  9.1M  2.0G   1% /run
      tmpfs          tmpfs     2.0G     0  2.0G   0% /sys/fs/cgroup
      tmpfs          tmpfs     398M     0  398M   0% /run/user/0
      /dev/vdb1      ext4      106G   63M  101G   1% /mnt/sdc
      /dev/vdb2      ext4       53G   55M   50G   1% /mnt/test

   .. note::

      If the server is restarted, the mounting will become invalid. You can set automatic mounting for partitions at system start by modifying the **/etc/fstab** file. For details, see :ref:`Setting Automatic Mounting at System Start <evs_01_0109__section1107170115310>`.

.. _evs_01_0109__section13346184710300:

Extending an Existing GPT Partition
-----------------------------------

.. important::

   If the additional space is allocated to an existing partition, data on the disk will not be cleared but you must use **umount** to unmount the existing partition. In this case, services will be affected.

Originally, data disk **/dev/vdb** has 150 GiB and two partitions (**/dev/vdb1** and **/dev/vdb2**), and then 80 GiB is added to the disk. The following procedure shows you how to add this 80 GiB to the existing GPT partition **/dev/vdb2**.

During an expansion, the additional space is added to the end of the disk. Therefore, if the disk has multiple partitions, the additional space can only be allocated to the partition at the disk end.

#. Run the following command to view the disk partition information:

   **lsblk**

   Information similar to the following is displayed:

   .. code-block:: console

      [root@ecs-test-0001 ~]# lsblk
      NAME   MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
      vda    253:0    0   40G  0 disk
      └─vda1 253:1    0   40G  0 part /
      vdb    253:16   0  230G  0 disk
      ├─vdb1 253:17   0  100G  0 part /mnt/sdc
      └─vdb2 253:18   0   50G  0 part /mnt/test

   View the **/dev/vdb** capacity and check whether the additional space is included.

   -  If the additional space is not included, refresh the capacity according to :ref:`Extending Partitions and File Systems for SCSI Disks (Linux) <evs_01_0018>`.
   -  If the additional space is included, go to :ref:`2 <evs_01_0109__li3879043619479>`.

#. Run the following command to unmount the partition:

   **umount** *Disk partition*

   In this example, run the following command:

   **umount** **/dev/vdb2**

#. Run the following command to view the unmount result:

   **lsblk**

   Information similar to the following is displayed:

   .. code-block:: console

      [root@ecs-test-0001 ~]# lsblk
      NAME   MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
      vda    253:0    0   40G  0 disk
      └─vda1 253:1    0   40G  0 part /
      vdb    253:16   0  230G  0 disk
      ├─vdb1 253:17   0  100G  0 part /mnt/sdc
      └─vdb2 253:18   0   50G  0 part

#. Run the following command to enter parted:

   **parted** *Disk*

   In this example, run the following command:

   **parted** **/dev/vdb**

   Information similar to the following is displayed:

   .. code-block:: console

      [root@ecs-test-0001 ~]# parted /dev/vdb
      GNU Parted 3.1
      Using /dev/vdb
      Welcome to GNU Parted! Type 'help' to view a list of commands.
      (parted)

#. Enter **unit s** and press **Enter** to set the measurement unit of the disk to sector.

#. .. _evs_01_0109__li17966161521416:

   Enter **p** and press **Enter** to view the disk partition information.

   Information similar to the following is displayed:

   .. code-block::

      (parted) unit s
      (parted) p
      Error: The backup GPT table is not at the end of the disk, as it should be.  This might mean that another operating system believes the
      disk is smaller.  Fix, by moving the backup to the end (and removing the old backup)?
      Fix/Ignore/Cancel? Fix
      Warning: Not all of the space available to /dev/vdb appears to be used, you can fix the GPT to use all of the space (an extra 167772160
      blocks) or continue with the current setting?
      Fix/Ignore? Fix
      Model: Virtio Block Device (virtblk)
      Disk /dev/vdb: 482344960s
      Sector size (logical/physical): 512B/512B
      Partition Table: gpt
      Disk Flags:

      Number  Start       End         Size        File system  Name  Flags
       1      2048s       209713151s  209711104s  ext4         test
       2      209713152s  314570751s  104857600s  ext4         data

      (parted)

   Take note of the start and end sectors of the **/dev/vdb2** partition. These values will be used during the partition recreation. In this example, the partition's start sector is **209713152s**, and its end sector is **314570751s**.

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

#. Enter **rm** and the partition number, and then press **Enter**. In this example, partition number **2** is used.

   Information similar to the following is displayed:

   .. code-block::

      (parted) rm
      Partition number? 2
      (parted)

#. Run the following command to recreate the partition and press **Enter**:

   **mkpart** *Partition name Start sector* *End sector*

   In this example, run the following command:

   **mkpart data 209713152s 100%**

   -  Ensure that the entered start sector is the same as the partition had before. In this example, start sector **209713152s** is recorded in :ref:`6 <evs_01_0109__li17966161521416>`. Therefore, enter **209713152s**.
   -  Ensure that the entered end sector is greater than the partition had before. In this example, the end sector recorded in :ref:`6 <evs_01_0109__li17966161521416>` is **314570751s**, and all the additional space needs to be allocated to **dev/vdb2**. Therefore, enter **100%**.

   Information similar to the following is displayed:

   .. code-block::

      (parted) mkpart data 209713152s 100%
      (parted)

   .. note::

      Data will be lost if the following operations are performed:

      -  Select a start sector other than the partition had before.
      -  Select an end sector smaller than the partition had before.

#. Enter **p** and press **Enter** to view the partition information.

   Information similar to the following is displayed:

   .. code-block::

      (parted) p
      Model: Virtio Block Device (virtblk)
      Disk /dev/vdb: 482344960s
      Sector size (logical/physical): 512B/512B
      Partition Table: gpt
      Disk Flags:

      Number  Start       End         Size        File system  Name  Flags
       1      2048s       209713151s  209711104s  ext4         test
       2      209713152s  482342911s  272629760s  ext4         data

      (parted)

#. Enter **q** and press **Enter** to exit parted.

   Information similar to the following is displayed:

   .. code-block::

      (parted) q
      Information: You may need to update /etc/fstab.

   You can set automatic disk mounting by updating the **/etc/fstab** file. Before updating the file, set the file system format for the partition and mount the partition on the mount point.

#. Perform the following operations based on the file system of the disk:

   -  For the **ext**\ ``*`` file system

      a. Run the following command to check the correctness of the file system on the partition:

         **e2fsck** **-f** *Disk partition*

         In this example, run the following command:

         **e2fsck** **-f** **/dev/vdb2**

         Information similar to the following is displayed:

         .. code-block:: console

            [root@ecs-test-0001 ~]# e2fsck -f /dev/vdb2
            e2fsck 1.42.9 (28-Dec-2013)
            Pass 1: Checking inodes, blocks, and sizes
            Pass 2: Checking directory structure
            Pass 3: Checking directory connectivity
            Pass 4: Checking reference counts
            Pass 5: Checking group summary information
            /dev/vdb2: 11/3276800 files (0.0% non-contiguous), 251790/13107200 blocks

      b. Run the following command to extend the file system of the partition:

         **resize2fs** *Disk partition*

         In this example, run the following command:

         **resize2fs** **/dev/vdb2**

         Information similar to the following is displayed:

         .. code-block:: console

            [root@ecs-test-0001 ~]# resize2fs /dev/vdb2
            resize2fs 1.42.9 (28-Dec-2013)
            Resizing the filesystem on /dev/vdb2 to 34078720 (4k) blocks.
            The filesystem on /dev/vdb2 is now 34078720 blocks long.

      c. (Optional) Run the following command to create a mount point:

         Perform this step if you want to mount the partition on a new mount point.

         **mkdir** *Mount point*

         In this example, run the following command to create the **/mnt/test** mount point:

         **mkdir** **/mnt/test**

      d. Run the following command to mount the partition:

         **mount** *Disk partition* *Mount point*

         In this example, run the following command to mount partition **/dev/vdb2** on **/mnt/test**:

         **mount** **/dev/vdb2** **/mnt/test**

         .. note::

            If the new partition is mounted on a directory that is not empty, the subdirectories and files in the directory will be hidden. Therefore, you are advised to mount the new partition on an empty directory or a new directory. If the new partition must be mounted on a directory that is not empty, move the subdirectories and files in this directory to another directory temporarily. After the partition is successfully mounted, move the subdirectories and files back.

   -  For the **xfs** file system

      a. (Optional) Run the following command to create a mount point:

         Perform this step if you want to mount the partition on a new mount point.

         **mkdir** *Mount point*

         In this example, run the following command to create the **/mnt/test** mount point:

         **mkdir** **/mnt/test**

      b. Run the following command to mount the partition:

         **mount** *Disk partition* *Mount point*

         In this example, run the following command to mount partition **/dev/vdb2** on **/mnt/test**:

         **mount** **/dev/vdb2** **/mnt/test**

         .. note::

            If the new partition is mounted on a directory that is not empty, the subdirectories and files in the directory will be hidden. Therefore, you are advised to mount the new partition on an empty directory or a new directory. If the new partition must be mounted on a directory that is not empty, move the subdirectories and files in this directory to another directory temporarily. After the partition is successfully mounted, move the subdirectories and files back.

      c. Run the following command to extend the file system of the partition:

         **sudo** **xfs\_growfs** *Disk partition*

         In this example, run the following command:

         **sudo** **xfs\_growfs** **/dev/vdb2**

         Information similar to the following is displayed:

         .. code-block:: console

            [root@ecs-test-0001 ~]# sudo xfs_growfs /dev/vdb2
            meta-data=/dev/vdb2              isize=512     agcount=4, agsize=3276800 blks
                     =                       sectsz=512    attr=2, projid32bit=1
                     =                       crc=1         finobt=0, spinodes=0
            data     =                       bsize=4096    blocks=13107200, imaxpct=25
                     =                       sunit=0       swidth=0 blks
            naming   =version2               bsize=4096    ascii-ci=0 ftype=1
            log      =internal               bsize=4096    blocks=6400, version=2
                     =                       sectsz=512    sunit=0 blks, lazy-count=1
            realtime =none                   extsz=4096    blocks=0, rtextents=0
            data blocks changed from 13107200 to 34078720.

#. Run the following command to view the mount result:

   **df -TH**

   Information similar to the following is displayed:

   .. code-block:: console

      [root@ecs-test-0001 ~]# df -TH
      Filesystem     Type      Size  Used Avail Use% Mounted on
      /dev/vda1      ext4       43G  1.9G   39G   5% /
      devtmpfs       devtmpfs  2.0G     0  2.0G   0% /dev
      tmpfs          tmpfs     2.0G     0  2.0G   0% /dev/shm
      tmpfs          tmpfs     2.0G  9.1M  2.0G   1% /run
      tmpfs          tmpfs     2.0G     0  2.0G   0% /sys/fs/cgroup
      tmpfs          tmpfs     398M     0  398M   0% /run/user/0
      /dev/vdb1      ext4      106G   63M  101G   1% /mnt/sdc
      /dev/vdb2      ext4      138G   63M  131G   1% /mnt/test

   .. note::

      If the server is restarted, the mounting will become invalid. You can set automatic mounting for partitions at system start by modifying the **/etc/fstab** file. For details, see :ref:`Setting Automatic Mounting at System Start <evs_01_0109__section1107170115310>`.

.. _evs_01_0109__section1107170115310:

Setting Automatic Mounting at System Start
------------------------------------------

Modify the **fstab** file to set automatic disk mounting at server start. You can also set automatic mounting for the servers containing data. This operation will not affect the existing data.

The following procedure shows how to set automatic disk mounting at server start by using UUIDs to identify disks in the **fstab** file. You are advised not to use device names to identify disks in the file because a device name may change (for example, from /dev/vdb1 to /dev/vdb2) during the server stop or start, resulting in improper server running after restart.

.. note::

   UUID is the unique character string for disk partitions in a Linux system.

#. Run the following command to query the partition UUID:

   **blkid** *Disk partition*

   In this example, run the following command to query the UUID of the **/dev/vdb1** partition:

   **blkid /dev/vdb1**

   Information similar to the following is displayed:

   .. code-block:: console

      [root@ecs-test-0001 ~]# blkid /dev/vdb1
      /dev/vdb1: UUID="0b3040e2-1367-4abb-841d-ddb0b92693df" TYPE="ext4"

   The UUID of the **/dev/vdb1** partition is displayed.

#. Run the following command to open the **fstab** file using the vi editor:

   **vi /etc/fstab**

#. Press **i** to enter editing mode.

#. Move the cursor to the end of the file and press **Enter**. Then, add the following information:

   .. code-block::

      UUID=0b3040e2-1367-4abb-841d-ddb0b92693df /mnt/sdc                ext4    defaults        0 2

#. Press **Esc**, enter **:wq**, and press **Enter**.

   The system saves the configurations and exits the vi editor.

#. Perform the following operations to verify the automatic mounting function:

   a. Run the following command to unmount the partition:

      **umount** *Disk partition*

      In this example, run the following command:

      **umount /dev/vdb1**

   b. Run the following command to reload all the content in the **/etc/fstab** file:

      **mount -a**

   c. Run the following command to query the file system mounting information:

      **mount** **\|** **grep** *Mount point*

      In this example, run the following command:

      **mount** **\|** **grep** **/mnt/sdc**

      If information similar to the following is displayed, automatic mounting has been configured:

      .. code-block::

         root@ecs-test-0001 ~]# mount | grep /mnt/sdc
         /dev/vdb1 on /mnt/sdc type ext4 (rw,relatime,data=ordered)
