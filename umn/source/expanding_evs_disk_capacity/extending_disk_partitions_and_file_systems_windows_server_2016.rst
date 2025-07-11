:original_name: evs_01_0126.html

.. _evs_01_0126:

Extending Disk Partitions and File Systems (Windows Server 2016)
================================================================

Scenarios
---------

After a disk is expanded on the console, the disk size is enlarged, but the additional space cannot be used directly.

In Windows, you must allocate the additional space to an existing partition or a new partition.

If the disk capacity is expanded on a stopped server, the additional space of a Windows system disk or Windows data disk will be automatically added to the partition at the end of the disk upon the server startup. In this case, the additional space can be used directly.

This section uses Windows Server 2016 Standard 64bit as the example OS to describe the expansion methods:

-  For a system disk:

   -  If volume (C:) already exists, you can add the additional space to volume (C:) and use it as a system volume. For details, see :ref:`System Disk: Add the Additional Space to the Original Volume <evs_01_0126__en-us_topic_0000001093561979_section026022982311>`.
   -  If volume (C:) already exists, you can create a new volume such as volume (F:) with the additional space and use the new volume as a data volume. For details, see :ref:`System Disk: Create a New Volume with the Additional Space <evs_01_0126__en-us_topic_0000001093561979_section19471943163216>`.

-  For a data disk:

   -  If volume (D:) already exists, you can add the additional space to volume (D:) and use it as a data volume. For details, see :ref:`Data Disk: Add the Additional Space to the Original Volume <evs_01_0126__en-us_topic_0000001093561979_section17259018135819>`.
   -  If volume (D:) already exists, you can create a new volume such as volume (E:) with the additional space and use the new volume as a data volume. For details, see :ref:`Data Disk: Create a New Volume with the Additional Space <evs_01_0126__en-us_topic_0000001093561979_section1983618124920>`.

The method for allocating the additional space varies with the server OS. This section is used for reference only. For detailed operations and differences, see the corresponding OS documents.

.. important::

   Incorrect operations may lead to data loss or exceptions, so you are advised to back up the disk data using CBR or snapshots before expansion. For details about using CBR, see :ref:`Managing EVS Disk Backups <evs_01_0110>`. For details about using snapshots, see :ref:`Managing EVS Snapshots <evs_01_0111>`.

Constraints
-----------

-  The additional space of a data disk cannot be added to the root partition. To extend the root partition, expand the system disk instead.
-  During an expansion, the additional space is added to the end of the disk. If the disk has multiple partitions, the additional space can only be allocated to the last partition of the disk.
-  If the target partition is an extended MBR partition (whose partition number is usually greater than or equal to 5), you need to first expand the extended partition and then the logical partition. Assume that you have three partitions, **/dev/vdb1** (primary partition), **/dev/vdb2** (extended partition), and **/dev/vdb5** (logical partition), you need to run **growpart /dev/vdb2** and then **growpart /dev/vdb5** to extend the partitions.
-  The maximum disk capacity that MBR supports is 2 TiB, and the disk space in access of 2 TiB cannot be used. If your disk already uses MBR for partitioning and you require more than 2 TiB after the capacity expansion, do as follows:

   -  (Recommended) Create a new EVS disk and use GPT.
   -  Back up the disk data, perform the expansion, and then change the partition style from MBR to GPT. During this change, services will be interrupted and data on the disk will be erased.

Prerequisites
-------------

-  You have expanded the disk capacity and attached the disk to a server on the console. For details, see :ref:`Expanding Capacity for an In-use EVS Disk <evs_01_0007>` or :ref:`Expanding Capacity for an Available EVS Disk <evs_01_0008>`.
-  You have logged in to the ECS.

   -  For how to log in to an ECS, see the *Elastic Cloud Server User Guide*.
   -  For how to log in to a BMS, see the *Bare Metal Server User Guide*.

.. _evs_01_0126__en-us_topic_0000001093561979_section026022982311:

System Disk: Add the Additional Space to the Original Volume
------------------------------------------------------------

In this example, the system disk has 40 GiB originally, and 30 GiB is added on the console. The following procedure describes how to add this 30 GiB to volume (C:) on the server. After the operation is complete, volume (C:) will have 70 GiB of capacity and can be used as a system volume.

#. On the desktop of the server, right-click the start icon in lower left corner and choose **Disk Management**.

   The **Disk Management** window is displayed.


   .. figure:: /_static/images/en-us_image_0000002182261641.png
      :alt: **Figure 1** Disk Management (Windows Server 2016)

      **Figure 1** Disk Management (Windows Server 2016)

   .. note::

      If you cannot see the additional space, right-click **Disk Management** and choose **Refresh** from the shortcut menu.

#. On the **Disk Management** page, select the disk and volume that you want to extend. The current volume size and unallocated space are displayed.

#. Right-click the target volume and choose **Extend Volume**.


   .. figure:: /_static/images/en-us_image_0000002146900762.png
      :alt: **Figure 2** Choosing Extend Volume (Windows Server 2016)

      **Figure 2** Choosing Extend Volume (Windows Server 2016)

#. On the displayed **Extend Volume Wizard** window, click **Next**.


   .. figure:: /_static/images/en-us_image_0000002182139989.png
      :alt: **Figure 3** Extend Volume Wizard (Windows Server 2016)

      **Figure 3** Extend Volume Wizard (Windows Server 2016)

#. In the text box to the right of **Select the amount of space in MB**, enter the amount of the additional space and click **Next**.


   .. figure:: /_static/images/en-us_image_0000002146742694.png
      :alt: **Figure 4** Selecting space (Windows Server 2016)

      **Figure 4** Selecting space (Windows Server 2016)

#. Click **Finish**.

   After the expansion succeeded, the partition size is larger than the original size.


   .. figure:: /_static/images/en-us_image_0000002182261645.png
      :alt: **Figure 5** Capacity expansion succeeded (Windows Server 2016)

      **Figure 5** Capacity expansion succeeded (Windows Server 2016)

.. _evs_01_0126__en-us_topic_0000001093561979_section19471943163216:

System Disk: Create a New Volume with the Additional Space
----------------------------------------------------------

In this example, the system disk has 40 GiB originally, and 60 GiB is added on the console. The following procedure describes how to use this 60 GiB to create a new volume, for example volume (F:), on the server. After the operation is complete, new volume (F:) has 60 GiB of capacity and can be used as a data volume.

#. On the desktop of the server, right-click the start icon in lower left corner and choose **Disk Management**.

   The **Disk Management** window is displayed.


   .. figure:: /_static/images/en-us_image_0000002146900766.png
      :alt: **Figure 6** Unallocated disk space (Windows Server 2016 system disk)

      **Figure 6** Unallocated disk space (Windows Server 2016 system disk)

   .. note::

      If you cannot see the additional space, right-click **Disk Management** and choose **Refresh** from the shortcut menu.

#. In the **Unallocated** area of **Disk 0**, right-click the blank area and choose **New Simple Volume**.


   .. figure:: /_static/images/en-us_image_0000002182139993.png
      :alt: **Figure 7** New Simple Volume (Windows Server 2016 system disk)

      **Figure 7** New Simple Volume (Windows Server 2016 system disk)

#. On the displayed **New Simple Volume Wizard** window, click **Next**.


   .. figure:: /_static/images/en-us_image_0000002146742698.png
      :alt: **Figure 8** New Simple Volume Wizard (Windows Server 2016 system disk)

      **Figure 8** New Simple Volume Wizard (Windows Server 2016 system disk)

#. On the displayed **Specify Volume Size** page, set **Simple volume size in MB** and click **Next**. In this example, the default size is used.


   .. figure:: /_static/images/en-us_image_0000002182261649.png
      :alt: **Figure 9** Specify Volume Size (Windows Server 2016 system disk)

      **Figure 9** Specify Volume Size (Windows Server 2016 system disk)

#. On the displayed **Assign Drive Letter and Path** page, click **Assign the following drive letter**, select a drive letter, and click **Next**. In this example, drive letter **F** is selected.


   .. figure:: /_static/images/en-us_image_0000002146900770.png
      :alt: **Figure 10** Assign Drive Letter or Path (Windows Server 2016 system disk)

      **Figure 10** Assign Drive Letter or Path (Windows Server 2016 system disk)

#. On the displayed **Format Partition** page, click **Format this volume with the following settings**, set parameters based on the requirements, and select **Perform a quick format**. Then, click **Next**.


   .. figure:: /_static/images/en-us_image_0000002182139997.png
      :alt: **Figure 11** Format Partition (Windows Server 2016 system disk)

      **Figure 11** Format Partition (Windows Server 2016 system disk)

#. Click **Finish**.

   After the expansion succeeded, new volume (F:) is displayed.


   .. figure:: /_static/images/en-us_image_0000002146742702.png
      :alt: **Figure 12** Volume (F:) (Windows Server 2016)

      **Figure 12** Volume (F:) (Windows Server 2016)

.. _evs_01_0126__en-us_topic_0000001093561979_section17259018135819:

Data Disk: Add the Additional Space to the Original Volume
----------------------------------------------------------

In this example, the data disk has 30 GiB originally, and 50 GiB is added on the console. The following procedure describes how to add this 50 GiB to volume (D:) on the server. After the operation is complete, volume (D:) has 80 GiB of capacity and can be used as a data volume.

#. On the desktop of the server, right-click the start icon in lower left corner and choose **Disk Management**.

   The **Disk Management** window is displayed.


   .. figure:: /_static/images/en-us_image_0000002182261653.png
      :alt: **Figure 13** Disk Management (Windows Server 2016 data disk)

      **Figure 13** Disk Management (Windows Server 2016 data disk)

   .. note::

      If you cannot see the additional space, right-click **Disk Management** and choose **Refresh** from the shortcut menu.

#. On the **Disk Management** page, select the disk and volume that you want to extend. The current volume size and unallocated space are displayed.

#. Right-click the target volume and choose **Extend Volume**.


   .. figure:: /_static/images/en-us_image_0000002146900774.png
      :alt: **Figure 14** Choosing Extend Volume (Windows Server 2016 operating system)

      **Figure 14** Choosing Extend Volume (Windows Server 2016 operating system)

#. On the displayed **Extend Volume Wizard** window, click **Next**.


   .. figure:: /_static/images/en-us_image_0000002182140001.png
      :alt: **Figure 15** Extend Volume Wizard (Windows Server 2016 operating system)

      **Figure 15** Extend Volume Wizard (Windows Server 2016 operating system)

#. In the text box to the right of **Select the amount of space in MB**, enter the amount of the additional space and click **Next**.


   .. figure:: /_static/images/en-us_image_0000002146742706.png
      :alt: **Figure 16** Selecting space (Windows Server 2016 operating system)

      **Figure 16** Selecting space (Windows Server 2016 operating system)

#. Click **Finish**.

   After the expansion succeeded, the partition size is larger than the original size.


   .. figure:: /_static/images/en-us_image_0000002182261657.png
      :alt: **Figure 17** Capacity expansion succeeded (Windows Server 2016 operating system)

      **Figure 17** Capacity expansion succeeded (Windows Server 2016 operating system)

.. _evs_01_0126__en-us_topic_0000001093561979_section1983618124920:

Data Disk: Create a New Volume with the Additional Space
--------------------------------------------------------

In this example, the data disk has 80 GiB originally, and 50 GiB is added on the console. The following procedure describes how to use this 50 GiB to create a new volume, for example volume (E:), on the server. After the operation is complete, new volume (E:) has 50 GiB of capacity and can be used as a data volume.

#. On the desktop of the server, right-click the start icon in lower left corner and choose **Disk Management**.

   The **Disk Management** window is displayed.


   .. figure:: /_static/images/en-us_image_0000002146900778.png
      :alt: **Figure 18** Unallocated disk space (Windows Server 2016 data disk)

      **Figure 18** Unallocated disk space (Windows Server 2016 data disk)

   .. note::

      If you cannot see the additional space, right-click **Disk Management** and choose **Refresh** from the shortcut menu.

#. In the **Unallocated** area of **Disk 1**, right-click the blank area and choose **New Simple Volume**.


   .. figure:: /_static/images/en-us_image_0000002182140005.png
      :alt: **Figure 19** New Simple Volume (Windows Server 2016 data disk)

      **Figure 19** New Simple Volume (Windows Server 2016 data disk)

#. On the displayed **New Simple Volume Wizard** window, click **Next**.


   .. figure:: /_static/images/en-us_image_0000002146742710.png
      :alt: **Figure 20** New Simple Volume Wizard (Windows Server 2016 data disk)

      **Figure 20** New Simple Volume Wizard (Windows Server 2016 data disk)

#. On the displayed **Specify Volume Size** page, set **Simple volume size in MB** and click **Next**. In this example, the default size is used.


   .. figure:: /_static/images/en-us_image_0000002182261661.png
      :alt: **Figure 21** Specify Volume Size (Windows Server 2016 data disk)

      **Figure 21** Specify Volume Size (Windows Server 2016 data disk)

#. On the displayed **Assign Drive Letter and Path** page, click **Assign the following drive letter**, select a drive letter, and click **Next**. In this example, drive letter **E** is selected.


   .. figure:: /_static/images/en-us_image_0000002146900782.png
      :alt: **Figure 22** Assign Drive Letter or Path (Windows Server 2016 data disk)

      **Figure 22** Assign Drive Letter or Path (Windows Server 2016 data disk)

#. On the displayed **Format Partition** page, click **Format this volume with the following settings**, set parameters based on the requirements, and select **Perform a quick format**. Then, click **Next**.


   .. figure:: /_static/images/en-us_image_0000002182140013.png
      :alt: **Figure 23** Format Partition (Windows Server 2016 data disk)

      **Figure 23** Format Partition (Windows Server 2016 data disk)

#. Click **Finish**.

   After the expansion succeeded, new volume (E:) is displayed.


   .. figure:: /_static/images/en-us_image_0000002146742714.png
      :alt: **Figure 24** Completed

      **Figure 24** Completed


   .. figure:: /_static/images/en-us_image_0000002182261665.png
      :alt: **Figure 25** New Volume (E:)

      **Figure 25** New Volume (E:)
