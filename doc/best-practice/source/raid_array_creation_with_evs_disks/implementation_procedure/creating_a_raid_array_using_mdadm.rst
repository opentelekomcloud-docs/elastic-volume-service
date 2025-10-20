:original_name: evs_02_0019.html

.. _evs_02_0019:

Creating a RAID Array Using mdadm
=================================

Scenarios
---------

This section shows how to create a RAID 10 array using mdadm.

In this example, the ECS runs CentOS Stream 9. Configurations vary depending on the OS running on the ECS. This section is used for reference only. For the detailed operations and differences, see the corresponding OS documents.

Procedure
---------

#. Log in to the ECS as user **root**.

#. .. _evs_02_0019__li1820454151114:

   Run the following command to view and take note of the device names:

   **fdisk -l \| grep /dev/vd \| grep -v vda**

   Information similar to the following is displayed:

   .. code-block:: console

      [root@ecs-raid10 ~]# fdisk -l | grep /dev/vd | grep -v vda
      Disk /dev/vdb: 10.7 GB, 10737418240 bytes, 20971520 sectors
      Disk /dev/vdc: 10.7 GB, 10737418240 bytes, 20971520 sectors
      Disk /dev/vdd: 10.7 GB, 10737418240 bytes, 20971520 sectors
      Disk /dev/vde: 10.7 GB, 10737418240 bytes, 20971520 sectors

   In the command output, four disks are attached to the ECS, and the device names are **/dev/vdb**, **/dev/vdc**, **/dev/vdd**, and **/dev/vde**, respectively.

#. Run the following command to install mdadm:

   **yum install mdadm -y**

   .. note::

      mdadm is a utility to create and manage software RAID arrays on Linux. Ensure that an EIP has been bound to the ECS where mdadm is to be installed.

   Information similar to the following is displayed:

   .. code-block:: console

      [root@ecs-raid10 ~]# yum install mdadm -y
      ......
      Installed:
        mdadm.x86_64 0:4.0-13.el7

      Dependency Installed:
        libreport-filesystem.x86_64 0:2.1.11-40.el7.centos

      Complete!

#. Run the following command to create a RAID array using the four disks queried in :ref:`2 <evs_02_0019__li1820454151114>`:

   **mdadm -Cv** *RAID array device name* **-a yes -n** *Disk quantity* **-l** *RAID level* *Device name of disk1 Device name of disk2 Device name of disk3 Device name of disk4*

   Parameter description:

   -  *RAID array device name*: The value can be user-definable. In this example, **/dev/md0** is used.

   -  *Disk quantity*: Set this parameter based on the actual condition. In this example, RAID 10 is created, and at least four disks are required.

      The minimum number of disks required varies depending on the RAID level. For details, see :ref:`Overview <evs_02_0014>`.

   -  *RAID level*: Set this parameter based on the actual condition. In this example, set it to RAID 10.

   -  *Device name of the disk*: Enter the device names of all the disks that will be used to create the RAID array. Multiple names are separated with spaces.

   In this example, run the following command:

   **mdadm -Cv /dev/md0 -a yes -n 4 -l 10 /dev/vdb /dev/vdc /dev/vdd /dev/vde**

   Information similar to the following is displayed:

   .. code-block:: console

      [root@ecs-raid10 ~]# mdadm -Cv /dev/md0 -a yes -n 4 -l 10 /dev/vdb /dev/vdc /dev/vdd /dev/vde
      mdadm: layout defaults to n2
      mdadm: layout defaults to n2
      mdadm: chunk size defaults to 512K
      mdadm: size set to 10476544K
      mdadm: Defaulting to version 1.2 metadata
      mdadm: array /dev/md0 started.

#. Run the following command to format the created RAID array:

   **mkfs.**\ *File system format* *Device name of the RAID array*

   In this example, run the following command:

   **mkfs.ext4 /dev/md0**

   Information similar to the following is displayed:

   .. code-block:: console

      [root@ecs-raid10 ~]# mkfs.ext4 /dev/md0
      mke2fs 1.42.9 (28-Dec-2013)
      Filesystem label=
      OS type: Linux
      Block size=4096 (log=2)
      Fragment size=4096 (log=2)
      Stride=128 blocks, Stripe width=256 blocks
      1310720 inodes, 5238272 blocks
      261913 blocks (5.00%) reserved for the super user
      First data block=0
      Maximum filesystem blocks=2153775104
      160 block groups
      32768 blocks per group, 32768 fragments per group
      8192 inodes per group
      Superblock backups stored on blocks:
              32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208,
              4096000

      Allocating group tables: done
      Writing inode tables: done
      Creating journal (32768 blocks): done
      Writing superblocks and filesystem accounting information: done

#. Run the following command to create a mounting directory:

   **mkdir** *Mounting directory*

   In this example, run the following command:

   **mkdir /RAID10**

#. Run the following command to mount the RAID array:

   **mount** *RAID array device name* *Mounting directory*

   In this example, run the following command:

   **mount /dev/md0 /RAID10**

#. Run the following command to view the mount result:

   **df -h**

   Information similar to the following is displayed:

   .. code-block:: console

      [root@ecs-raid10 ~]# df -h
      Filesystem      Size  Used Avail Use% Mounted on
      /dev/vda2        39G  1.5G   35G   5% /
      devtmpfs        911M     0  911M   0% /dev
      tmpfs           920M     0  920M   0% /dev/shm
      tmpfs           920M  8.6M  911M   1% /run
      tmpfs           920M     0  920M   0% /sys/fs/cgroup
      /dev/vda1       976M  146M  764M  17% /boot
      tmpfs           184M     0  184M   0% /run/user/0
      /dev/md0         20G   45M   19G   1% /RAID10

#. Perform the following operations to enable automatic mounting of the RAID array at the system start:

   a. Run the following command to open the **/etc/fstab** file:

      **vi /etc/fstab**

   b. Press **i** to enter editing mode.

      Information similar to the following is displayed:

      .. code-block:: console

         [root@ecs-raid10 ~]# vi /etc/fstab

         #
         # /etc/fstab
         # Created by anaconda on Tue Nov  7 14:28:26 2017
         #
         # Accessible filesystems, by reference, are maintained under '/dev/disk'
         # See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
         #
         UUID=27f9be47-838b-4155-b20b-e4c5e013cdf3 /                       ext4    defaults        1 1
         UUID=2b2000b1-f926-4b6b-ade8-695ee244a901 /boot                   ext4    defaults        1 2

   c. Add the following information to the end of the file:

      .. code-block::

         /dev/md0                                  /RAID10                 ext4    defaults        0 0

   d. Press **Esc**, enter **:wq!**, and press **Enter**.

      The system saves the modifications and exits the vi editor.

#. Run the following command to view the RAID array information:

   **mdadm -D** *RAID array device name*

   In this example, run the following command:

   **mdadm -D /dev/md0**

   Information similar to the following is displayed:

   .. code-block:: console

      [root@ecs-raid10 ~]# mdadm -D /dev/md0
      /dev/md0:
                 Version : 1.2
           Creation Time : Thu Nov  8 15:49:02 2018
              Raid Level : raid10
              Array Size : 20953088 (19.98 GiB 21.46 GB)
           Used Dev Size : 10476544 (9.99 GiB 10.73 GB)
            Raid Devices : 4
           Total Devices : 4
             Persistence : Superblock is persistent

             Update Time : Thu Nov  8 16:15:11 2018
                   State : clean
          Active Devices : 4
         Working Devices : 4
          Failed Devices : 0
           Spare Devices : 0

                  Layout : near=2
              Chunk Size : 512K

      Consistency Policy : resync

                    Name : ecs-raid10.novalocal:0  (local to host ecs-raid10.novalocal)
                    UUID : f400dbf9:60d211d9:e006e07b:98f8758c
                  Events : 19

          Number   Major   Minor   RaidDevice State
             0     253       16        0      active sync set-A   /dev/vdb
             1     253       32        1      active sync set-B   /dev/vdc
             2     253       48        2      active sync set-A   /dev/vdd
             3     253       64        3      active sync set-B   /dev/vde
