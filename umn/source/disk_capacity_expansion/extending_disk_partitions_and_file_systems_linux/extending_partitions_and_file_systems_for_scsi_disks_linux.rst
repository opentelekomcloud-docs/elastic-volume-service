:original_name: evs_01_0018.html

.. _evs_01_0018:

Extending Partitions and File Systems for SCSI Disks (Linux)
============================================================

Scenarios
---------

After a disk has been expanded on the management console, the disk size is enlarged, but the additional space cannot be used directly.

In Linux, you must allocate the additional space to an existing partition or a new partition.

This section uses CentOS 7.4 64bit as the sample OS to describe how to extend an MBR partition of a SCSI data disk. The method for allocating the additional space varies depending on the server OS. This document is used for reference only. For detailed operations and differences, see the corresponding OS documents.

-  :ref:`Creating a New MBR Partition <evs_01_0018__section12265143819280>`
-  :ref:`Extending an Existing MBR Partition <evs_01_0018__section31113372194023>`

.. important::

   Performing the expansion operations with caution. Misoperation may lead to data loss or exceptions. Therefore, you are advised to back up the disk data using backups or snapshots before expansion. For details about backups, see :ref:`Managing EVS Backup <evs_01_0110>`. For details about snapshots, see :ref:`Creating a Snapshot <en-us_topic_0066615262>`.

Prerequisites
-------------

-  You have expanded the disk capacity and attached the disk to a server on the management console. For details, see :ref:`Expanding Capacity for an In-use EVS Disk <evs_01_0007>` or :ref:`Expanding Capacity for an Available EVS Disk <evs_01_0008>`.
-  You have logged in to the server.

   -  For how to log in to an ECS, see the *Elastic Cloud Server User Guide*.
   -  For how to log in to a BMS, see the *Bare Metal Server User Guide*.

.. _evs_01_0018__section12265143819280:

Creating a New MBR Partition
----------------------------

Originally, data disk **/dev/sda** has 50 GB and one partition (**/dev/sda1**), and then 50 GB is added to the disk. The following procedure shows you how to create a new MBR partition **/dev/sda2** with this 50 GB.

#. Run the following command to view the disk partition information:

   **fdisk -l**

   Information similar to the following is displayed:

   .. code-block:: console

      [root@ecs-scsi ~]# fdisk -l

      Disk /dev/vda: 42.9 GB, 42949672960 bytes, 83886080 sectors
      Units = sectors of 1 * 512 = 512 bytes
      Sector size (logical/physical): 512 bytes / 512 bytes
      I/O size (minimum/optimal): 512 bytes / 512 bytes
      Disk label type: dos
      Disk identifier: 0x000bcb4e

         Device Boot      Start         End      Blocks   Id  System
      /dev/vda1   *        2048    83886079    41942016   83  Linux

      Disk /dev/sda: 107.4 GB, 107374182400 bytes, 209715200 sectors
      Units = sectors of 1 * 512 = 512 bytes
      Sector size (logical/physical): 512 bytes / 512 bytes
      I/O size (minimum/optimal): 512 bytes / 512 bytes
      Disk label type: dos
      Disk identifier: 0x915ffe6a

         Device Boot      Start         End      Blocks   Id  System
      /dev/sda1            2048   104857599    52427776   83  Linux

   View the **/dev/sda** capacity and check whether the additional space is included.

   -  If the additional space is not included, refresh the capacity according to :ref:`2 <evs_01_0018__li1311112192367>`.
   -  If the additional space is included, go to :ref:`3 <evs_01_0018__li14771329195025>`.

#. .. _evs_01_0018__li1311112192367:

   (Optional) Run the following command to update the capacity of the SCSI data disk:

   a. Run the following command to update the disk capacity on the server:

      **echo 1 > /sys/class/scsi_device/**\ *%d:%d:%d:%d*\ **/device/rescan &**

      In the command, **%d:%d:%d:%d** indicates a folder in the **/sys/class/scsi_device/** directory and can be obtained using **ll /sys/class/scsi_device/**.

      Information similar to the following is displayed: (**2:0:0:0** indicates the folder to be obtained.)

      .. code-block::

         cs-xen-02:/sys/class/scsi_device # ll /sys/class/scsi_device/
         total 0
         lrwxrwxrwx 1 root root 0 Sep 26 11:37 2:0:0:0 -> ../../devices/xen/vscsi-2064/host2/target2:0:0/2:0:0:0/scsi_device/2:0:0:0

      In this example, run the following command:

      **echo 1 > /sys/class/scsi_device/2:0:0:0/device/rescan &**

   b. After the disk capacity is updated, run the following command to view the disk partition information again:

      **fdisk -l**

      If the additional space is included, go to :ref:`3 <evs_01_0018__li14771329195025>`.

#. .. _evs_01_0018__li14771329195025:

   Run the following command to enter fdisk:

   **fdisk** *Disk*

   In this example, run the following command:

   **fdisk /dev/sda**

   Information similar to the following is displayed:

   .. code-block:: console

      [root@ecs-scsi ~]# fdisk /dev/sda
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
      First sector (104857600-209715199, default 104857600):

   **First sector** indicates the start sector. The value ranges from **104857600** to **209715199**, and the default value is **104857600**.

#. Enter the new partition's start sector and press **Enter**. In this example, the default start sector is used.

   The system displays the start and end sectors of the partition's available space. You can customize the value within this range or use the default value. The start sector must be smaller than the partition's end sector.

   Information similar to the following is displayed:

   .. code-block::

      First sector (104857600-209715199, default 104857600):
      Using default value 104857600
      Last sector, +sectors or +size{K,M,G} (104857600-209715199, default 209715199):

   **Last sector** indicates the end sector. The value ranges from **104857600** to **209715199**, and the default value is **209715199**.

#. Enter the new partition's end sector and press **Enter**. In this example, the default end sector is used.

   The system displays the start and end sectors of the partition's available space. You can customize the value within this range or use the default value. The start sector must be smaller than the partition's end sector.

   Information similar to the following is displayed:

   .. code-block::

      Last sector, +sectors or +size{K,M,G} (104857600-209715199, default 209715199):
      Using default value 209715199
      Partition 2 of type Linux and of size 50 GiB is set

      Command (m for help):

#. Enter **p** and press **Enter** to view the new partition.

   Information similar to the following is displayed:

   .. code-block::

      Command (m for help): p

      Disk /dev/sda: 107.4 GB, 107374182400 bytes, 209715200 sectors
      Units = sectors of 1 * 512 = 512 bytes
      Sector size (logical/physical): 512 bytes / 512 bytes
      I/O size (minimum/optimal): 512 bytes / 512 bytes
      Disk label type: dos
      Disk identifier: 0x915ffe6a

         Device Boot      Start         End      Blocks   Id  System
      /dev/sda1            2048   104857599    52427776   83  Linux
      /dev/sda2       104857600   209715199    52428800   83  Linux

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

   **mkfs -t** *File system* *Disk partition*

   -  Sample command of the ext\* file system:

      **mkfs -t ext4 /dev/sda2**

      Information similar to the following is displayed:

      .. code-block:: console

         [root@ecs-scsi ~]# mkfs -t ext4 /dev/sda2
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

      **mkfs -t xfs /dev/sda2**

      Information similar to the following is displayed:

      .. code-block:: console

         [root@ecs-scsi ~]# mkfs -t xfs /dev/sda2
         meta-data=/dev/sda2              isize=512     agcount=4, agsize=3276800 blks
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

   In this example, run the following command to mount the new partition **/dev/sda2** on **/mnt/test**:

   **mount /dev/sda2 /mnt/test**

   .. note::

      If the new partition is mounted on a directory that is not empty, the subdirectories and files in the directory will be hidden. Therefore, you are advised to mount the new partition on an empty directory or a new directory. If the new partition must be mounted on a directory that is not empty, move the subdirectories and files in this directory to another directory temporarily. After the partition is successfully mounted, move the subdirectories and files back.

#. Run the following command to view the mount result:

   **df -TH**

   Information similar to the following is displayed:

   .. code-block:: console

      [root@ecs-scsi ~]# df -TH
      Filesystem     Type      Size  Used Avail Use% Mounted on
      /dev/vda1      ext4       43G  2.0G   39G   5% /
      devtmpfs       devtmpfs  509M     0  509M   0% /dev
      tmpfs          tmpfs     520M     0  520M   0% /dev/shm
      tmpfs          tmpfs     520M  7.2M  513M   2% /run
      tmpfs          tmpfs     520M     0  520M   0% /sys/fs/cgroup
      tmpfs          tmpfs     104M     0  104M   0% /run/user/0
      /dev/sda1      ext4       53G   55M   50G   1% /mnt/sdc
      /dev/sda2      ext4       53G   55M   50G   1% /mnt/test

   .. note::

      If the server is restarted, the mounting will become invalid. You can set automatic mounting for partitions at system start by modifying the **/etc/fstab** file. For details, see :ref:`Setting Automatic Mounting at System Start <evs_01_0018__section1107170115310>`.

.. _evs_01_0018__section31113372194023:

Extending an Existing MBR Partition
-----------------------------------

.. important::

   If the additional space is allocated to an existing partition, data on the disk will not be cleared but you must use **umount** to unmount the existing partition. In this case, services will be affected.

Originally, SCSI data disk **/dev/sda** has 100 GB and two partitions (**/dev/sda1** and **/dev/sda2**), and then 50 GB is added to the disk. The following procedure shows you how to add this 50 GB to the existing MBR partition **/dev/sda2**.

During an expansion, the additional space is added to the end of the disk. Therefore, if the disk has multiple partitions, the additional space can only be allocated to the partition at the disk end.

#. .. _evs_01_0018__li6396237219479:

   Run the following command to view the disk partition information:

   **fdisk -l**

   Information similar to the following is displayed:

   .. code-block:: console

      [root@ecs-scsi ~]# fdisk -l

      Disk /dev/vda: 42.9 GB, 42949672960 bytes, 83886080 sectors
      Units = sectors of 1 * 512 = 512 bytes
      Sector size (logical/physical): 512 bytes / 512 bytes
      I/O size (minimum/optimal): 512 bytes / 512 bytes
      Disk label type: dos
      Disk identifier: 0x000bcb4e

         Device Boot      Start         End      Blocks   Id  System
      /dev/vda1   *        2048    83886079    41942016   83  Linux

      Disk /dev/sda: 161.1 GB, 161061273600 bytes, 314572800 sectors
      Units = sectors of 1 * 512 = 512 bytes
      Sector size (logical/physical): 512 bytes / 512 bytes
      I/O size (minimum/optimal): 512 bytes / 512 bytes
      Disk label type: dos
      Disk identifier: 0x915ffe6a

         Device Boot      Start         End      Blocks   Id  System
      /dev/sda1            2048   104857599    52427776   83  Linux
      /dev/sda2       104857600   209715199    52428800   83  Linux

   In the command output, take note of the partition's start and end sectors. In this example, **/dev/sda2**'s start sector is **104857600**, and its end sector is **209715199**.

   View the **/dev/sda** capacity and check whether the additional space is included.

   -  If the additional space is not included, refresh the capacity according to :ref:`2 <evs_01_0018__li11239195417383>`.
   -  If the additional space is included, take note of the start and end sectors of the target partition and then go to :ref:`3 <evs_01_0018__li3879043619479>`. These values will be used in the subsequent operations.

#. .. _evs_01_0018__li11239195417383:

   (Optional) Run the following command to update the capacity of the SCSI data disk:

   a. Run the following command to update the disk capacity on the server:

      **echo 1 > /sys/class/scsi_device/**\ *%d:%d:%d:%d*\ **/device/rescan &**

      In the command, **%d:%d:%d:%d** indicates a folder in the **/sys/class/scsi_device/** directory and can be obtained using **ll /sys/class/scsi_device/**.

      Information similar to the following is displayed: (**2:0:0:0** indicates the folder to be obtained.)

      .. code-block::

         cs-xen-02:/sys/class/scsi_device # ll /sys/class/scsi_device/
         total 0
         lrwxrwxrwx 1 root root 0 Sep 26 11:37 2:0:0:0 -> ../../devices/xen/vscsi-2064/host2/target2:0:0/2:0:0:0/scsi_device/2:0:0:0

      In this example, run the following command:

      **echo 1 > /sys/class/scsi_device/2:0:0:0/device/rescan &**

   b. After the disk capacity is updated, run the following command to view the disk partition information again:

      **fdisk -l**

      If the additional space is included, take note of the start and end sectors of the target partition and then go to :ref:`3 <evs_01_0018__li3879043619479>`. These values will be used in the subsequent operations.

#. .. _evs_01_0018__li3879043619479:

   Run the following command to unmount the partition:

   **umount** *Disk partition*

   In this example, run the following command:

   **umount /dev/sda2**

#. Run the following command to enter fdisk:

   **fdisk** *Disk*

   In this example, run the following command:

   **fdisk /dev/sda**

   Information similar to the following is displayed:

   .. code-block:: console

      [root@ecs-scsi ~]# fdisk /dev/sda
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
      First sector (104857600-314572799, default 104857600):

   In the command output, **First sector** specifies the start sector.

   .. note::

      Data will be lost if the following operations are performed:

      -  Select a start sector other than the partition had before.
      -  Select an end sector smaller than the partition had before.

#. Ensure that the entered start sector is the same as the partition had before. In this example, start sector **104857600** is recorded in :ref:`1 <evs_01_0018__li6396237219479>` or :ref:`2 <evs_01_0018__li11239195417383>`. Therefore, enter **104857600** and press **Enter**.

   Information similar to the following is displayed:

   .. code-block::

      First sector (104857600-314572799, default 104857600):
      Using default value 104857600
      Last sector, +sectors or +size{K,M,G} (104857600-314572799, default 314572799):

   In the command output, **Last sector** specifies the end sector.

#. Ensure that the entered end sector is larger than or equal to the end sector recorded in :ref:`1 <evs_01_0018__li6396237219479>` or :ref:`2 <evs_01_0018__li11239195417383>`. In this example, the recorded end sector is **209715199**, and the default end sector is used. Therefore, enter **314572799** and press **Enter**.

   Information similar to the following is displayed:

   .. code-block::

      Last sector, +sectors or +size{K,M,G} (104857600-314572799, default 314572799):
      Using default value 314572799
      Partition 2 of type Linux and of size 100 GiB is set

      Command (m for help):

   The partition is created.

#. Enter **p** and press **Enter** to view the partition details.

   Information similar to the following is displayed:

   .. code-block::

      Command (m for help): p

      Disk /dev/sda: 161.1 GB, 161061273600 bytes, 314572800 sectors
      Units = sectors of 1 * 512 = 512 bytes
      Sector size (logical/physical): 512 bytes / 512 bytes
      I/O size (minimum/optimal): 512 bytes / 512 bytes
      Disk label type: dos
      Disk identifier: 0x915ffe6a

         Device Boot      Start         End      Blocks   Id  System
      /dev/sda1            2048   104857599    52427776   83  Linux
      /dev/sda2       104857600   314572799    104857600  83  Linux

      Command (m for help):

#. Enter **w** and press **Enter** to write the changes to the partition table.

   Information similar to the following is displayed: (The partition is successfully created.)

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

   -  For the **ext**\ *\** file system

      a. Run the following command to check the correctness of the file system on the partition:

         **e2fsck -f** *Disk partition*

         In this example, run the following command:

         **e2fsck -f /dev/sda2**

         Information similar to the following is displayed:

         .. code-block:: console

            [root@ecs-scsi ~]# e2fsck -f /dev/sda2
            e2fsck 1.42.9 (28-Dec-2013)
            Pass 1: Checking inodes, blocks, and sizes
            Pass 2: Checking directory structure
            Pass 3: Checking directory connectivity
            Pass 4: Checking reference counts
            Pass 5: Checking group summary information
            /dev/sda2: 11/3276800 files (0.0% non-contiguous), 251790/13107200 blocks

      b. Run the following command to extend the file system of the partition:

         **resize2fs** *Disk partition*

         In this example, run the following command:

         **resize2fs /dev/sda2**

         Information similar to the following is displayed:

         .. code-block:: console

            [root@ecs-scsi ~]# resize2fs /dev/sda2
            resize2fs 1.42.9 (28-Dec-2013)
            Resizing the filesystem on /dev/sda2 to 26214400 (4k) blocks.
            The filesystem on /dev/sda2 is now 26214400 blocks long.

      c. (Optional) Run the following command to create a mount point:

         Perform this step if you want to mount the partition on a new mount point.

         **mkdir** *Mount point*

         In this example, run the following command to create the **/mnt/test** mount point:

         **mkdir** **/mnt/test**

      d. Run the following command to mount the partition:

         **mount** *Disk partition* *Mount point*

         In this example, run the following command to mount the partition **/dev/sda2** on **/mnt/test**:

         **mount /dev/sda2 /mnt/test**

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

         In this example, run the following command to mount the partition **/dev/sda2** on **/mnt/test**:

         **mount /dev/sda2 /mnt/test**

         .. note::

            If the new partition is mounted on a directory that is not empty, the subdirectories and files in the directory will be hidden. Therefore, you are advised to mount the new partition on an empty directory or a new directory. If the new partition must be mounted on a directory that is not empty, move the subdirectories and files in this directory to another directory temporarily. After the partition is successfully mounted, move the subdirectories and files back.

      c. Run the following command to extend the file system of the partition:

         **sudo** **xfs\_growfs** *Disk partition*

         In this example, run the following command:

         **sudo** **xfs\_growfs** **/dev/sda2**

         Information similar to the following is displayed:

         .. code-block:: console

            [root@ecs-scsi ~]# sudo xfs_growfs /dev/sda2
            meta-data=/dev/sda2              isize=512     agcount=4, agsize=3276800 blks
                     =                       sectsz=512    attr=2, projid32bit=1
                     =                       crc=1         finobt=0, spinodes=0
            data     =                       bsize=4096    blocks=13107200, imaxpct=25
                     =                       sunit=0       swidth=0 blks
            naming   =version2               bsize=4096    ascii-ci=0 ftype=1
            log      =internal               bsize=4096    blocks=6400, version=2
                     =                       sectsz=512    sunit=0 blks, lazy-count=1
            realtime =none                   extsz=4096    blocks=0, rtextents=0
            data blocks changed from 13107200 to 26214400df .

#. Run the following command to view the mount result:

   **df -TH**

   Information similar to the following is displayed:

   .. code-block:: console

      [root@ecs-scsi ~]# df -TH
      Filesystem     Type      Size  Used Avail Use% Mounted on
      /dev/vda1      ext4       43G  2.0G   39G   5% /
      devtmpfs       devtmpfs  509M     0  509M   0% /dev
      tmpfs          tmpfs     520M     0  520M   0% /dev/shm
      tmpfs          tmpfs     520M  7.2M  513M   2% /run
      tmpfs          tmpfs     520M     0  520M   0% /sys/fs/cgroup
      tmpfs          tmpfs     104M     0  104M   0% /run/user/0
      /dev/sda1      ext4       53G   55M   50G   1% /mnt/sdc
      /dev/sda2      ext4      106G   63M  101G   1% /mnt/test

   .. note::

      If the server is restarted, the mounting will become invalid. You can set automatic mounting for partitions at system start by modifying the **/etc/fstab** file. For details, see :ref:`Setting Automatic Mounting at System Start <evs_01_0018__section1107170115310>`.

.. _evs_01_0018__section1107170115310:

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

#. Press **i** to enter the editing mode.

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

      If information similar to the following is displayed, the automatic mounting function takes effect:

      .. code-block::

         root@ecs-test-0001 ~]# mount | grep /mnt/sdc
         /dev/vdb1 on /mnt/sdc type ext4 (rw,relatime,data=ordered)
