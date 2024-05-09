:original_name: en-us_topic_0017616396.html

.. _en-us_topic_0017616396:

Extending Disk Partitions and File Systems (Windows Server 2008)
================================================================

Scenarios
---------

After a disk is expanded on the management console, the disk size is enlarged, but the additional space cannot be used directly.

In Windows, you must allocate the additional space to an existing partition or a new partition.

If the disk capacity is expanded on a stopped server, the additional space of a Windows system disk or Windows data disk will be automatically added to the partition at the end of the disk upon the server startup. In this case, the additional space can be used directly.

This section uses Windows Server 2008 R2 Enterprise 64bit as the sample OS to describe the expansion methods:

-  For a system disk:

   -  If volume (C:) already exists, you can add the additional space to volume (C:) and use it as a system volume. For details, see :ref:`System Disk: Add the Additional Space to the Original Volume <en-us_topic_0017616396__section56589192192644>`.
   -  If volume (C:) already exists, you can create a new volume such as volume (F:) with the additional space and use the new volume as a data volume. For details, see :ref:`System Disk: Create a New Volume with the Additional Space <en-us_topic_0017616396__section17412322419>`.
   -  If the additional space has been added to volume (C:), you can shrink volume (C:), create a new volume with the available space, and use the new volume as a data volume. Only the available space can be shrunk and used to create the new volume. The additional space cannot be shrunk if it has already been used. This section uses a system disk to describe how to perform extension operations for a Windows disk. These operations are also suitable for data disks. For details, see :ref:`System Disk: Create a New Volume Using the Available Space Shrunk from the Original Volume <en-us_topic_0017616396__section172461313408>`.

-  For a data disk:

   -  If volume (D:) already exists, you can add the additional space to volume (D:) and use it as a data volume. For details, see :ref:`Data Disk: Add the Additional Space to the Original Volume <en-us_topic_0017616396__section20686303192651>`.
   -  If volume (D:) already exists, you can create a new volume such as volume (E:) with the additional space and use the new volume as a data volume. For details, see :ref:`Data Disk: Create a New Volume with the Additional Space <en-us_topic_0017616396__section1971024320173>`.

The method for allocating the additional space varies with the server OS. This section is used for reference only. For detailed operations and differences, see the corresponding OS documents.

.. important::

   Performing the expansion operations with caution. Incorrect operations may lead to data loss or exceptions. So you are advised to back up the disk data using CBR or snapshots before expansion. For details about using CBR, see :ref:`Managing EVS Backups <evs_01_0110>`. For details about using snapshots, see :ref:`Creating a Snapshot <en-us_topic_0066615262>`.

Prerequisites
-------------

-  You have expanded the disk capacity and attached the disk to a server on the management console. For details, see :ref:`Expanding Capacity for an In-use EVS Disk <evs_01_0007>` or :ref:`Expanding Capacity for an Available EVS Disk <evs_01_0008>`.
-  You have logged in to the server.

   -  For how to log in to an ECS, see the *Elastic Cloud Server User Guide*.
   -  For how to log in to a BMS, see the *Bare Metal Server User Guide*.

.. _en-us_topic_0017616396__section56589192192644:

System Disk: Add the Additional Space to the Original Volume
------------------------------------------------------------

In this example, the system disk has 50 GiB originally, and 22 GiB is added on the management console. The following procedure describes how to add this 22 GiB to volume (C:) on the server. After the operation is complete, volume (C:) will have 72 GiB of capacity and can be used as a system volume.

#. On the desktop of the server, right-click **Computer** and choose **Manage** from the shortcut menu.

   The **Server Manager** window is displayed.

#. In the navigation tree, choose **Storage** > **Disk Management**.

   The **Disk Management** window is displayed.


   .. figure:: /_static/images/en-us_image_0090103571.png
      :alt: **Figure 1** Disk Management (system disk)

      **Figure 1** Disk Management (system disk)

   .. note::

      If you cannot see the additional space, right-click **Disk Management** and choose **Refresh** from the shortcut menu.

#. On the **Disk Management** page, select the disk and volume that you want to extend. The current volume size and unallocated space are displayed.

#. Right-click the target volume and choose **Extend Volume**.


   .. figure:: /_static/images/en-us_image_0044524716.png
      :alt: **Figure 2** Choosing **Extend Volume**

      **Figure 2** Choosing **Extend Volume**

#. On the displayed **Extend Volume Wizard** window, click **Next**.


   .. figure:: /_static/images/en-us_image_0044524701.png
      :alt: **Figure 3** Extend Volume Wizard

      **Figure 3** Extend Volume Wizard

#. In the text box to the right of **Select the amount of space in MB**, enter the amount of the additional space and click **Next**.


   .. figure:: /_static/images/en-us_image_0044524678.png
      :alt: **Figure 4** Selecting space

      **Figure 4** Selecting space

#. Click **Finish**.

   After the expansion succeeded, the partition size is larger than the original size.


   .. figure:: /_static/images/en-us_image_0044524671.png
      :alt: **Figure 5** Capacity expansion succeeded

      **Figure 5** Capacity expansion succeeded

.. _en-us_topic_0017616396__section17412322419:

System Disk: Create a New Volume with the Additional Space
----------------------------------------------------------

In this example, the system disk has 40 GiB originally, and 60 GiB is added on the management console. The following procedure describes how to use this 60 GiB to create a new volume, for example volume (F:), on the server. After the operation is complete, new volume (F:) has 60 GiB of capacity and can be used as a data volume.

#. On the desktop of the server, right-click **Computer** and choose **Manage** from the shortcut menu.

   The **Server Manager** window is displayed.

#. In the navigation tree, choose **Storage** > **Disk Management**.

   The **Disk Management** window is displayed.


   .. figure:: /_static/images/en-us_image_0169144806.png
      :alt: **Figure 6** Refresh (system disk)

      **Figure 6** Refresh (system disk)

#. If you cannot see the additional space, right-click **Disk Management** and choose **Refresh** from the shortcut menu.

   After the refresh, the additional space is displayed in the right area and is unallocated.


   .. figure:: /_static/images/en-us_image_0169144807.png
      :alt: **Figure 7** Unallocated disk space (system disk)

      **Figure 7** Unallocated disk space (system disk)

#. In the **Unallocated** area of **Disk 0**, right-click the blank area and choose **New Simple Volume**.


   .. figure:: /_static/images/en-us_image_0169144808.png
      :alt: **Figure 8** New Simple Volume (system disk)

      **Figure 8** New Simple Volume (system disk)

#. On the displayed **New Simple Volume Wizard** window, click **Next**.


   .. figure:: /_static/images/en-us_image_0169144809.png
      :alt: **Figure 9** New Simple Volume Wizard (system disk)

      **Figure 9** New Simple Volume Wizard (system disk)

#. On the displayed **Specify Volume Size** page, set **Simple volume size in MB** and click **Next**. In this example, the default size is used.


   .. figure:: /_static/images/en-us_image_0169144810.png
      :alt: **Figure 10** Specify Volume Size (system disk)

      **Figure 10** Specify Volume Size (system disk)

#. On the displayed **Assign Drive Letter and Path** page, click **Assign the following drive letter**, select a drive letter, and click **Next**. In this example, drive letter **F** is selected.


   .. figure:: /_static/images/en-us_image_0169144811.png
      :alt: **Figure 11** Assign Drive Letter or Path (system disk)

      **Figure 11** Assign Drive Letter or Path (system disk)

#. On the displayed **Format Partition** page, click **Format this volume with the following settings**, set parameters based on the requirements, and select **Perform a quick format**. Then, click **Next**.


   .. figure:: /_static/images/en-us_image_0169144812.png
      :alt: **Figure 12** Format Partition (system disk)

      **Figure 12** Format Partition (system disk)

#. Click **Finish**.

   After the expansion succeeded, new volume (F:) is displayed.


   .. figure:: /_static/images/en-us_image_0169144813.png
      :alt: **Figure 13** Completing the New Simple Volume Wizard (new volume F:)

      **Figure 13** Completing the New Simple Volume Wizard (new volume F:)


   .. figure:: /_static/images/en-us_image_0169144814.png
      :alt: **Figure 14** New Volume (F:)

      **Figure 14** New Volume (F:)

.. _en-us_topic_0017616396__section172461313408:

System Disk: Create a New Volume Using the Available Space Shrunk from the Original Volume
------------------------------------------------------------------------------------------

In this example, the system disk has 40 GiB originally, and 60 GiB is added on the management console and then formatted and added to volume (C:). This 60 GiB has not been used.

The following procedure describes how to use the shrink function to create new volume (D:) with this 60 GiB. After the operation is complete, new volume (D:) can be used as a data volume.

#. On the desktop of the server, right-click **Computer** and choose **Manage** from the shortcut menu.

   The **Server Manager** window is displayed.

#. In the navigation tree, choose **Storage** > **Disk Management**.

   The **Disk Management** window is displayed.


   .. figure:: /_static/images/en-us_image_0169153665.png
      :alt: **Figure 15** Refresh (shrink volume)

      **Figure 15** Refresh (shrink volume)

#. In the **(C:)** area of **Disk 0**, right-click the blank area and choose **Shrink Volume**.


   .. figure:: /_static/images/en-us_image_0169153667.png
      :alt: **Figure 16** Shrink Volume

      **Figure 16** Shrink Volume

#. The system automatically queries the available shrink space. In the displayed dialog box, enter the available space and click **Shrink**.

   In this example, the volume available space is 60 GiB. Therefore, enter **61440** (60 x 1024 MiB).


   .. figure:: /_static/images/en-us_image_0169443743.png
      :alt: **Figure 17** Shrink (shrink volume)

      **Figure 17** Shrink (shrink volume)

   After the operation is complete, **Disk 0** has 60 GiB unallocated space.


   .. figure:: /_static/images/en-us_image_0169443885.png
      :alt: **Figure 18** Unallocated (shrink volume)

      **Figure 18** Unallocated (shrink volume)

#. In the **Unallocated** area of **Disk 0**, right-click the blank area and choose **New Simple Volume**.


   .. figure:: /_static/images/en-us_image_0169443887.png
      :alt: **Figure 19** New Simple Volume (shrink volume)

      **Figure 19** New Simple Volume (shrink volume)

#. On the displayed **New Simple Volume Wizard** window, click **Next**.


   .. figure:: /_static/images/en-us_image_0169153668.png
      :alt: **Figure 20** New Simple Volume Wizard (shrink volume)

      **Figure 20** New Simple Volume Wizard (shrink volume)

#. On the displayed **Specify Volume Size** page, set **Simple volume size in MB** and click **Next**. In this example, the default size is used.


   .. figure:: /_static/images/en-us_image_0169153669.png
      :alt: **Figure 21** Specify Volume Size (shrink volume)

      **Figure 21** Specify Volume Size (shrink volume)

#. On the displayed **Assign Drive Letter and Path** page, click **Assign the following drive letter**, select a drive letter, and click **Next**. In this example, drive letter **D** is selected.


   .. figure:: /_static/images/en-us_image_0169153670.png
      :alt: **Figure 22** Assign Drive Letter or Path (shrink volume)

      **Figure 22** Assign Drive Letter or Path (shrink volume)

#. On the displayed **Format Partition** page, click **Format this volume with the following settings**, set parameters based on the requirements, and select **Perform a quick format**. Then, click **Next**.


   .. figure:: /_static/images/en-us_image_0169153671.png
      :alt: **Figure 23** Format Partition (shrink volume)

      **Figure 23** Format Partition (shrink volume)

#. Click **Finish**.

   After the expansion succeeded, new volume (D:) is displayed.


   .. figure:: /_static/images/en-us_image_0169153672.png
      :alt: **Figure 24** Completing the New Simple Volume Wizard (new volume D:)

      **Figure 24** Completing the New Simple Volume Wizard (new volume D:)


   .. figure:: /_static/images/en-us_image_0169153673.png
      :alt: **Figure 25** New Volume (D:)

      **Figure 25** New Volume (D:)

.. _en-us_topic_0017616396__section20686303192651:

Data Disk: Add the Additional Space to the Original Volume
----------------------------------------------------------

In this example, the data disk has 100 GiB originally, and 50 GiB is added on the management console. The following procedure describes how to add this 50 GiB to volume (D:) on the server. After the operation is complete, volume (D:) has 150 GiB of capacity and can be used as a data volume.

#. On the desktop of the server, right-click **Computer** and choose **Manage** from the shortcut menu.

   The **Server Manager** window is displayed.

#. In the navigation tree, choose **Storage** > **Disk Management**.

   The **Disk Management** window is displayed.


   .. figure:: /_static/images/en-us_image_0125151939.png
      :alt: **Figure 26** Disk Management (data disk)

      **Figure 26** Disk Management (data disk)

   .. note::

      If you cannot see the additional space, right-click **Disk Management** and choose **Refresh** from the shortcut menu.

#. On the **Disk Management** page, select the disk and volume that you want to extend. The current volume size and unallocated space are displayed.

#. Right-click the target volume and choose **Extend Volume**.


   .. figure:: /_static/images/en-us_image_0044524713.png
      :alt: **Figure 27** Choosing Extend Volume (Windows Server 2008)

      **Figure 27** Choosing Extend Volume (Windows Server 2008)

#. On the displayed **Extend Volume Wizard** window, click **Next**.


   .. figure:: /_static/images/en-us_image_0044524709.png
      :alt: **Figure 28** Extend Volume Wizard (Windows Server 2008)

      **Figure 28** Extend Volume Wizard (Windows Server 2008)

#. In the text box to the right of **Select the amount of space in MB**, enter the amount of the additional space and click **Next**.


   .. figure:: /_static/images/en-us_image_0044524739.png
      :alt: **Figure 29** Selecting space (Windows Server 2008)

      **Figure 29** Selecting space (Windows Server 2008)

#. Click **Finish**.

   After the expansion succeeded, the partition size is larger than the original size.


   .. figure:: /_static/images/en-us_image_0044524683.png
      :alt: **Figure 30** Capacity expansion succeeded (Windows Server 2008)

      **Figure 30** Capacity expansion succeeded (Windows Server 2008)

.. _en-us_topic_0017616396__section1971024320173:

Data Disk: Create a New Volume with the Additional Space
--------------------------------------------------------

In this example, the data disk has 40 GiB originally, and 60 GiB is added on the management console. The following procedure describes how to use this 60 GiB to create a new volume, for example volume (E:), on the server. After the operation is complete, new volume (E:) has 60 GiB of capacity and can be used as a data volume.

#. On the desktop of the server, right-click **Computer** and choose **Manage** from the shortcut menu.

   The **Server Manager** window is displayed.

#. In the navigation tree, choose **Storage** > **Disk Management**.

   The **Disk Management** window is displayed.


   .. figure:: /_static/images/en-us_image_0169138641.png
      :alt: **Figure 31** Refresh (data disk)

      **Figure 31** Refresh (data disk)

#. If you cannot see the additional space, right-click **Disk Management** and choose **Refresh** from the shortcut menu.

   After the refresh, the additional space is displayed in the right area and is unallocated.


   .. figure:: /_static/images/en-us_image_0169139666.png
      :alt: **Figure 32** Unallocated disk space (data disk)

      **Figure 32** Unallocated disk space (data disk)

#. In the **Unallocated** area of **Disk 1**, right-click the blank area and choose **New Simple Volume**.


   .. figure:: /_static/images/en-us_image_0169140345.png
      :alt: **Figure 33** New Simple Volume (data disk)

      **Figure 33** New Simple Volume (data disk)

#. On the displayed **New Simple Volume Wizard** window, click **Next**.


   .. figure:: /_static/images/en-us_image_0169137709.png
      :alt: **Figure 34** New Simple Volume Wizard (data disk)

      **Figure 34** New Simple Volume Wizard (data disk)

#. On the displayed **Specify Volume Size** page, set **Simple volume size in MB** and click **Next**. In this example, the default size is used.


   .. figure:: /_static/images/en-us_image_0169137710.png
      :alt: **Figure 35** Specify Volume Size (data disk)

      **Figure 35** Specify Volume Size (data disk)

#. On the displayed **Assign Drive Letter and Path** page, click **Assign the following drive letter**, select a drive letter, and click **Next**. In this example, drive letter **E** is selected.


   .. figure:: /_static/images/en-us_image_0169142103.png
      :alt: **Figure 36** Assign Drive Letter or Path (data disk)

      **Figure 36** Assign Drive Letter or Path (data disk)

#. On the displayed **Format Partition** page, click **Format this volume with the following settings**, set parameters based on the requirements, and select **Perform a quick format**. Then, click **Next**.


   .. figure:: /_static/images/en-us_image_0169142386.png
      :alt: **Figure 37** Format Partition (data disk)

      **Figure 37** Format Partition (data disk)

#. Click **Finish**.

   After the expansion succeeded, new volume (E:) is displayed.


   .. figure:: /_static/images/en-us_image_0169142986.png
      :alt: **Figure 38** Completing the New Simple Volume Wizard (new volume E:)

      **Figure 38** Completing the New Simple Volume Wizard (new volume E:)


   .. figure:: /_static/images/en-us_image_0169137711.png
      :alt: **Figure 39** New Volume (E:)

      **Figure 39** New Volume (E:)
