:original_name: en-us_topic_0017616396.html

.. _en-us_topic_0017616396:

Extending Disk Partitions and File Systems (Windows Server 2008)
================================================================

Scenarios
---------

After a disk has been expanded on the management console, the disk size is enlarged, but the additional space cannot be used directly.

In Windows, you must allocate the additional space to an existing partition or a new partition.

This section uses Windows Server 2008 R2 Enterprise 64bit as the sample OS to describe the expansion methods:

-  For a system disk:

   -  If volume (C:) already exists, you can add the additional space to volume (C:) and use it as a system volume. For details, see :ref:`System Disk: Add Additional Space to Volume (C:) <en-us_topic_0017616396__section56589192192644>`.
   -  If volume (C:) already exists, you can create a new volume such as volume (F:) with the additional space and use the new volume as a data volume. For details, see :ref:`System Disk: Create New Volume (F:) with Additional Space <en-us_topic_0017616396__section17412322419>`.

-  For a data disk:

   -  If volume (D:) already exists, you can add the additional space to volume (D:) and use it as a data volume. For details, see :ref:`Data Disk: Add Additional Space to Volume (D:) <en-us_topic_0017616396__section20686303192651>`.
   -  If volume (D:) already exists, you can create a new volume such as volume (E:) with the additional space and use the new volume as a data volume. For details, see :ref:`Data Disk: Create New Volume (E:) with Additional Space <en-us_topic_0017616396__section1971024320173>`.

The method for allocating the additional space varies with the server OS. This section is used for reference only. For detailed operations and differences, see the corresponding OS documents.

.. important::

   Performing the expansion operations with caution. Misoperation may lead to data loss or exceptions. Therefore, you are advised to back up the disk data using backups or snapshots before expansion. For details about backups, see :ref:`Managing EVS Backup <evs_01_0110>`. For details about snapshots, see :ref:`Creating a Snapshot <en-us_topic_0066615262>`.

Prerequisites
-------------

-  You have expanded the disk capacity and attached the disk to a server on the management console. For details, see :ref:`Expanding Capacity for an In-use EVS Disk <evs_01_0007>` or :ref:`Expanding Capacity for an Available EVS Disk <evs_01_0008>`.
-  You have logged in to the server.

   -  For how to log in to an ECS, see the *Elastic Cloud Server User Guide*.
   -  For how to log in to a BMS, see the *Bare Metal Server User Guide*.

.. _en-us_topic_0017616396__section56589192192644:

System Disk: Add Additional Space to Volume (C:)
------------------------------------------------

In this example, the system disk has 50 GB originally, and 22 GB is added on the management console. The following procedure describes how to add this 22 GB to volume (C:) on the server. After the operation is complete, volume (C:) will have 72 GB of capacity and can be used as a system volume.

#. On the desktop of the server, right-click **Computer** and choose **Manage** from the shortcut menu.

   The **Server Manager** window is displayed.

#. In the navigation tree, choose **Storage** > **Disk Management**.

   The **Disk Management** window is displayed.

   .. _en-us_topic_0017616396__fig1686908719287:

   .. figure:: /_static/images/en-us_image_0090103571.png
      :alt: **Figure 1** Disk Management (system disk)


      **Figure 1** Disk Management (system disk)

   .. note::

      If you cannot view the additional space, right-click **Disk Management** and choose **Refresh** from the shortcut menu.

#. On the **Disk Management** page, select the disk and volume that you want to extend. The current volume size and unallocated space are displayed.

#. Right-click the target volume and choose **Extend Volume**.

   .. _en-us_topic_0017616396__fig585833019287:

   .. figure:: /_static/images/en-us_image_0044524716.png
      :alt: **Figure 2** Choosing **Extend Volume**


      **Figure 2** Choosing **Extend Volume**

#. On the displayed **Extend Volume Wizard** window, click **Next**.

   .. _en-us_topic_0017616396__fig4944876519287:

   .. figure:: /_static/images/en-us_image_0044524701.png
      :alt: **Figure 3** Extend Volume Wizard


      **Figure 3** Extend Volume Wizard

#. In the text box to the right of **Select the amount of space in MB**, enter the amount of the additional space and click **Next**.

   .. _en-us_topic_0017616396__fig6057097319287:

   .. figure:: /_static/images/en-us_image_0044524678.png
      :alt: **Figure 4** Selecting space


      **Figure 4** Selecting space

#. Click **Finish**.

   After the expansion succeeded, the partition size is larger than the original size.

   .. _en-us_topic_0017616396__fig2139119119287:

   .. figure:: /_static/images/en-us_image_0044524671.png
      :alt: **Figure 5** Capacity expansion succeeded


      **Figure 5** Capacity expansion succeeded

.. _en-us_topic_0017616396__section17412322419:

System Disk: Create New Volume (F:) with Additional Space
---------------------------------------------------------

In this example, the system disk has 40 GB originally, and 60 GB is added on the management console. The following procedure describes how to use this 60 GB to create a new volume, for example volume (F:), on the server. After the operation is complete, new volume (F:) has 60 GB of capacity and can be used as a data volume.

#. On the desktop of the server, right-click **Computer** and choose **Manage** from the shortcut menu.

   The **Server Manager** window is displayed.

#. In the navigation tree, choose **Storage** > **Disk Management**.

   The **Disk Management** window is displayed.

   .. _en-us_topic_0017616396__fig1875632841:

   .. figure:: /_static/images/en-us_image_0169144806.png
      :alt: **Figure 6** Refresh (system disk)


      **Figure 6** Refresh (system disk)

#. If you cannot view the additional space, right-click **Disk Management** and choose **Refresh** from the shortcut menu.

   After the refresh, the additional space is displayed in the right area and is unallocated.

   .. _en-us_topic_0017616396__fig107563216410:

   .. figure:: /_static/images/en-us_image_0169144807.png
      :alt: **Figure 7** Unallocated disk space (system disk)


      **Figure 7** Unallocated disk space (system disk)

#. In the **Unallocated** area of **Disk 0**, right-click the blank area and choose **New Simple Volume**.

   .. _en-us_topic_0017616396__fig376153211419:

   .. figure:: /_static/images/en-us_image_0169144808.png
      :alt: **Figure 8** New Simple Volume (system disk)


      **Figure 8** New Simple Volume (system disk)

#. On the displayed **New Simple Volume Wizard** window, click **Next**.

   .. _en-us_topic_0017616396__fig57610321448:

   .. figure:: /_static/images/en-us_image_0169144809.png
      :alt: **Figure 9** New Simple Volume Wizard (system disk)


      **Figure 9** New Simple Volume Wizard (system disk)

#. On the displayed **Specify Volume Size** page, set **Simple volume size in MB** and click **Next**. In this example, the default size is used.

   .. _en-us_topic_0017616396__fig157611321419:

   .. figure:: /_static/images/en-us_image_0169144810.png
      :alt: **Figure 10** Specify Volume Size (system disk)


      **Figure 10** Specify Volume Size (system disk)

#. On the displayed **Assign Drive Letter and Path** page, click **Assign the following drive letter**, select a drive letter, and click **Next**. In this example, drive letter **F** is selected.

   .. _en-us_topic_0017616396__fig1576332646:

   .. figure:: /_static/images/en-us_image_0169144811.png
      :alt: **Figure 11** Assign Driver Letter or Path (system disk)


      **Figure 11** Assign Driver Letter or Path (system disk)

#. On the displayed **Format Partition** page, click **Format this volume with the following settings**, set parameters based on the requirements, and select **Perform a quick format**. Then, click **Next**.

   .. _en-us_topic_0017616396__fig3771732147:

   .. figure:: /_static/images/en-us_image_0169144812.png
      :alt: **Figure 12** Format Partition (system disk)


      **Figure 12** Format Partition (system disk)

#. Click **Finish**.

   After the expansion succeeded, new volume (F:) is displayed.

   .. _en-us_topic_0017616396__fig16777321443:

   .. figure:: /_static/images/en-us_image_0169144813.png
      :alt: **Figure 13** Completing the New Simple Volume Wizard (new volume F:)


      **Figure 13** Completing the New Simple Volume Wizard (new volume F:)

   .. _en-us_topic_0017616396__fig207719321442:

   .. figure:: /_static/images/en-us_image_0169144814.png
      :alt: **Figure 14** New Volume (F:)


      **Figure 14** New Volume (F:)

.. _en-us_topic_0017616396__section20686303192651:

Data Disk: Add Additional Space to Volume (D:)
----------------------------------------------

In this example, the data disk has 100 GB originally, and 50 GB is added on the management console. The following procedure describes how to add this 50 GB to volume (D:) on the server. After the operation is complete, volume (D:) has 150 GB of capacity and can be used as a data volume.

#. On the desktop of the server, right-click **Computer** and choose **Manage** from the shortcut menu.

   The **Server Manager** window is displayed.

#. In the navigation tree, choose **Storage** > **Disk Management**.

   The **Disk Management** window is displayed.

   .. _en-us_topic_0017616396__fig129789723114:

   .. figure:: /_static/images/en-us_image_0125151939.png
      :alt: **Figure 15** Disk Management (data disk)


      **Figure 15** Disk Management (data disk)

   .. note::

      If you cannot view the additional space, right-click **Disk Management** and choose **Refresh** from the shortcut menu.

#. On the **Disk Management** page, select the disk and volume that you want to extend. The current volume size and unallocated space are displayed.

#. Right-click the target volume and choose **Extend Volume**.

   .. _en-us_topic_0017616396__fig6892073193332:

   .. figure:: /_static/images/en-us_image_0044524713.png
      :alt: **Figure 16** Choosing Extend Volume (Windows Server 2008)


      **Figure 16** Choosing Extend Volume (Windows Server 2008)

#. On the displayed **Extend Volume Wizard** window, click **Next**.

   .. _en-us_topic_0017616396__fig21912605193332:

   .. figure:: /_static/images/en-us_image_0044524709.png
      :alt: **Figure 17** Extend Volume Wizard (Windows Server 2008)


      **Figure 17** Extend Volume Wizard (Windows Server 2008)

#. In the text box to the right of **Select the amount of space in MB**, enter the amount of the additional space and click **Next**.

   .. _en-us_topic_0017616396__fig58557281193332:

   .. figure:: /_static/images/en-us_image_0044524739.png
      :alt: **Figure 18** Selecting space (Windows Server 2008)


      **Figure 18** Selecting space (Windows Server 2008)

#. Click **Finish**.

   After the expansion succeeded, the partition size is larger than the original size.

   .. _en-us_topic_0017616396__fig31824203193332:

   .. figure:: /_static/images/en-us_image_0044524683.png
      :alt: **Figure 19** Capacity expansion succeeded (Windows Server 2008)


      **Figure 19** Capacity expansion succeeded (Windows Server 2008)

.. _en-us_topic_0017616396__section1971024320173:

Data Disk: Create New Volume (E:) with Additional Space
-------------------------------------------------------

In this example, the data disk has 40 GB originally, and 60 GB is added on the management console. The following procedure describes how to use this 60 GB to create a new volume, for example volume (E:), on the server. After the operation is complete, new volume (E:) has 60 GB of capacity and can be used as a data volume.

#. On the desktop of the server, right-click **Computer** and choose **Manage** from the shortcut menu.

   The **Server Manager** window is displayed.

#. In the navigation tree, choose **Storage** > **Disk Management**.

   The **Disk Management** window is displayed.

   .. _en-us_topic_0017616396__fig1850964851716:

   .. figure:: /_static/images/en-us_image_0169138641.png
      :alt: **Figure 20** Refresh (data disk)


      **Figure 20** Refresh (data disk)

#. If you cannot view the additional space, right-click **Disk Management** and choose **Refresh** from the shortcut menu.

   After the refresh, the additional space is displayed in the right area and is unallocated.

   .. _en-us_topic_0017616396__fig2107588356:

   .. figure:: /_static/images/en-us_image_0169139666.png
      :alt: **Figure 21** Unallocated disk space (data disk)


      **Figure 21** Unallocated disk space (data disk)

#. In the **Unallocated** area of **Disk 1**, right-click the blank area and choose **New Simple Volume**.

   .. _en-us_topic_0017616396__fig650934818179:

   .. figure:: /_static/images/en-us_image_0169140345.png
      :alt: **Figure 22** New Simple Volume (data disk)


      **Figure 22** New Simple Volume (data disk)

#. On the displayed **New Simple Volume Wizard** window, click **Next**.

   .. _en-us_topic_0017616396__fig4509194818179:

   .. figure:: /_static/images/en-us_image_0169137709.png
      :alt: **Figure 23** New Simple Volume Wizard (data disk)


      **Figure 23** New Simple Volume Wizard (data disk)

#. On the displayed **Specify Volume Size** page, set **Simple volume size in MB** and click **Next**. In this example, the default size is used.

   .. _en-us_topic_0017616396__fig14509114811173:

   .. figure:: /_static/images/en-us_image_0169137710.png
      :alt: **Figure 24** Specify Volume Size (data disk)


      **Figure 24** Specify Volume Size (data disk)

#. On the displayed **Assign Drive Letter and Path** page, click **Assign the following drive letter**, select a drive letter, and click **Next**. In this example, drive letter **E** is selected.

   .. _en-us_topic_0017616396__fig2050063074520:

   .. figure:: /_static/images/en-us_image_0169142103.png
      :alt: **Figure 25** Assign Driver Letter or Path (data disk)


      **Figure 25** Assign Driver Letter or Path (data disk)

#. On the displayed **Format Partition** page, click **Format this volume with the following settings**, set parameters based on the requirements, and select **Perform a quick format**. Then, click **Next**.

   .. _en-us_topic_0017616396__fig19840335173018:

   .. figure:: /_static/images/en-us_image_0169142386.png
      :alt: **Figure 26** Format Partition (data disk)


      **Figure 26** Format Partition (data disk)

#. Click **Finish**.

   After the expansion succeeded, new volume (E:) is displayed.

   .. _en-us_topic_0017616396__fig11575389490:

   .. figure:: /_static/images/en-us_image_0169142986.png
      :alt: **Figure 27** Completing the New Simple Volume Wizard (new volume E:)


      **Figure 27** Completing the New Simple Volume Wizard (new volume E:)

   .. _en-us_topic_0017616396__fig55105489173:

   .. figure:: /_static/images/en-us_image_0169137711.png
      :alt: **Figure 28** New Volume (E:)


      **Figure 28** New Volume (E:)
