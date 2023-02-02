:original_name: evs_faq_0022.html

.. _evs_faq_0022:

Why Can't I View the Attached Data Disk on the Server?
======================================================

Troubleshooting
---------------

.. table:: **Table 1** Possible causes

   +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------+
   | OS                    | Possible Cause                                                                                                                                                             | Solution                                                      |
   +=======================+============================================================================================================================================================================+===============================================================+
   | Linux                 | -  New data disks are not formatted and partitioned by default, and an unformatted disk will not be listed in the command output. You must manually initialize the disk.   | :ref:`Linux Data Disk <evs_faq_0022__section1514019519474>`   |
   |                       | -  If a data disk cannot be found after the server is restarted, automatic partition mounting at system start may not be configured.                                       |                                                               |
   +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------+
   | Windows               | New data disks are not formatted and partitioned by default. Only formatted and partitioned drives show up in the resource manager. You must manually initialize the disk. | :ref:`Windows Data Disk <evs_faq_0022__section1894911274212>` |
   +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------------------+

.. _evs_faq_0022__section1514019519474:

Linux Data Disk
---------------

**Symptom**: A data disk has been attached to a Linux server on the management console, but the disk cannot be viewed on the server.

Run **df -TH** to view the disk information. CentOS 7.4 is used in this example. The normal command output is as follows:

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

Unlike the normal command output, only system disk **/dev/vda1** is visible, but data disk **/dev/vdb1** is missing from the command output.

**Cause Analysis**:

-  **Cause 1**: New data disks are not formatted and partitioned by default, and an unformatted disk will not be listed in the command output. You must manually initialize the disk.

   For details, see :ref:`Introduction to Data Disk Initialization Scenarios and Partition Styles <evs_01_0038>`.

-  **Cause 2**: If a data disk cannot be found after the server is restarted, automatic partition mounting at system start may not be configured. Perform the following steps:

   #. Run the following command to mount the partition again:

      **mount** *Disk partition* *Mount point*

      In this example, run the following command:

      **mount /dev/vdb1 /mnt/sdc**

      Perform the following steps to enable automatic partition mounting at system start:

   #. .. _evs_faq_0022__li840964143216:

      Run the following command to query the partition UUID:

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

      Press **i** to enter editing mode.

   #. Move the cursor to the end of the file and press **Enter**. Then, add the following information:

      .. code-block::

         UUID=0b3040e2-1367-4abb-841d-ddb0b92693df /mnt/sdc                ext4    defaults        0 2

      The preceding content is used for reference only. Add the information that is used in the environment. The parameters are described as follows:

      -  The first column indicates the partition UUID obtained in :ref:`2 <evs_faq_0022__li840964143216>`.
      -  The second column indicates the directory on which the partition is mounted. You can query the mount point using the **df -TH** command.
      -  The third column indicates the file system format of the partition. You can query the file system format using the **df -TH** command.
      -  The fourth column indicates the partition mount option. Normally, this parameter is set to **defaults**.
      -  The fifth column indicates the Linux dump backup option.

         -  **0**: Linux dump backup is not used. Normally, dump backup is not used, and you can set this parameter to **0**.
         -  **1**: Linux dump backup is used.

      -  The sixth column indicates the fsck option, that is, whether to use fsck to check the attached disk during startup.

         -  **0**: not use fsck.

         -  If the mount point is the root partition (**/**), this parameter must be set to **1**.

            When this parameter is set to **1** for the root partition, this parameter for other partitions must start with **2** because the system checks the partitions in the ascending order of the values.

   #. Press **Esc**, enter **:wq**, and press **Enter**.

      The system saves the configurations and exits the vi editor.

      Perform the following operations to verify the automatic mounting function:

      a. Run the following command to unmount the partition:

         **umount** *Disk partition*

         In this example, run the following command:

         **umount /dev/vdb1**

      b. Run the following command to reload all the content in the **/etc/fstab** file:

         **mount -a**

      c. Run the following command to query the file system mounting information:

         **mount \| grep** *Mount point*

         In this example, run the following command:

         **mount \| grep** **/mnt/sdc**

         If information similar to the following is displayed, automatic mounting has been configured:

         .. code-block::

            root@ecs-test-0001 ~]# mount | grep /mnt/sdc
            /dev/vdb1 on /mnt/sdc type ext4 (rw,relatime,data=ordered)

.. _evs_faq_0022__section1894911274212:

Windows Data Disk
-----------------

**Symptom**: A data disk has been attached to a Windows server on the management console, but the disk cannot be viewed on the server. For example, Volume (D:) was not shown in **This PC** of a Windows server running Windows Server 2012. Normally, Volume (D:) appears, as shown in :ref:`Figure 1 <evs_faq_0022__fig156291639133210>`.

.. _evs_faq_0022__fig156291639133210:

.. figure:: /_static/images/en-us_image_0000001327868762.png
   :alt: **Figure 1** Volume (D:) appears

   **Figure 1** Volume (D:) appears

**Solution**: New data disks are not formatted and partitioned by default. Only formatted and partitioned drives show up in **This PC**. You must manually initialize the disk before it can be viewed here.

For details, see :ref:`Introduction to Data Disk Initialization Scenarios and Partition Styles <evs_01_0038>`.
