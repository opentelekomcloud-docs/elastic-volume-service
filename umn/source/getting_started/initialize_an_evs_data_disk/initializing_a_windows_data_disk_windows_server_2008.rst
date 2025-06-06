:original_name: evs_01_0108.html

.. _evs_01_0108:

Initializing a Windows Data Disk (Windows Server 2008)
======================================================

Scenarios
---------

This section uses Windows Server 2008 R2 Enterprise 64bit to describe how to initialize a data disk attached to a server running Windows.

The maximum disk capacity supported by MBR is 2 TiB, and that supported by GPT is 18 EiB. Therefore, use the GPT partition style if your disk capacity is larger than 2 TiB. To learn more about disk partition styles, see :ref:`Introduction to Data Disk Initialization Scenarios and Partition Styles <evs_01_0038>`.

The method for initializing a disk varies slightly depending on the OS running on the server. This document is used for reference only. For the detailed operations and differences, see the product documents of the corresponding OS.

.. important::

   When using a disk for the first time, if you have not initialized it, including creating partitions and file systems, the additional space added to this disk in an expansion later may not be normally used.

Prerequisites
-------------

-  A data disk has been attached to a server and has not been initialized.
-  You have logged in to the server.

   -  For how to log in to an ECS, see the *Elastic Cloud Server User Guide*.
   -  For how to log in to a BMS, see the *Bare Metal Server User Guide*.

Procedure
---------

#. On the desktop of the server, right-click **Computer** and choose **Manage** from the shortcut menu.

   The **Server Manager** window is displayed.

#. In the navigation tree, choose **Storage** > **Disk Management**.

   The **Disk Management** window is displayed.

   -  If :ref:`Figure 1 <evs_01_0108__en-us_topic_0000001855867909_en-us_topic_0000001855169053_fig40496387105554>` is displayed, the new disk is offline. Go to :ref:`3 <evs_01_0108__en-us_topic_0000001855867909_en-us_topic_0000001855169053_li33296033102625>`.
   -  If :ref:`Figure 4 <evs_01_0108__en-us_topic_0000001855867909_en-us_topic_0000001855169053_fig68332918241>` is displayed, the **Initialize Disk** window is prompted. Go to :ref:`5 <evs_01_0108__en-us_topic_0000001855867909_en-us_topic_0000001855169053_li34991214122212>`.

   .. _evs_01_0108__en-us_topic_0000001855867909_en-us_topic_0000001855169053_fig40496387105554:

   .. figure:: /_static/images/en-us_image_0000001855948581.png
      :alt: **Figure 1** Disk Management

      **Figure 1** Disk Management

#. .. _evs_01_0108__en-us_topic_0000001855867909_en-us_topic_0000001855169053_li33296033102625:

   Disks are displayed in the right pane. In the **Disk 1** area, right-click **Offline** and choose **Online** from the shortcut menu to online the disk.


   .. figure:: /_static/images/en-us_image_0000001809029912.png
      :alt: **Figure 2** Online the disk

      **Figure 2** Online the disk

   .. note::

      If the disk is offline, you need to bring it online before initializing it.

#. After making the disk online, the status of **Disk 1** changes from **Offline** to **Not Initialized**. Right-click the disk status and choose **Initialize Disk** from the shortcut menu.


   .. figure:: /_static/images/en-us_image_0000001809189756.png
      :alt: **Figure 3** Initialize Disk

      **Figure 3** Initialize Disk

#. .. _evs_01_0108__en-us_topic_0000001855867909_en-us_topic_0000001855169053_li34991214122212:

   In the **Initialize Disk** dialog box, select the target disk, click **MBR (Master Boot Record)** or **GPT (GUID Partition Table)**, and click **OK**.

   .. _evs_01_0108__en-us_topic_0000001855867909_en-us_topic_0000001855169053_fig68332918241:

   .. figure:: /_static/images/en-us_image_0000001855868557.png
      :alt: **Figure 4** Unallocated space

      **Figure 4** Unallocated space

   .. important::

      The maximum disk size supported by MBR is 2 TiB, and that supported by GPT is 18 EiB. Because an EVS data disk currently supports up to 32 TiB, use GPT if your disk size is greater than 2 TiB.

      If the partition style is changed after the disk has been used, all data on the disk will be lost, so take care to select an appropriate partition style when initializing the disk. If you must change the partition style to GPT after a disk has been used, it is recommended that you back up the disk data before the change.

#. Right-click at the unallocated space and choose **New Simple Volume** from the shortcut menu.


   .. figure:: /_static/images/en-us_image_0000001855948589.png
      :alt: **Figure 5** New Simple Volume

      **Figure 5** New Simple Volume

#. On the displayed **New Simple Volume Wizard** window, click **Next**.


   .. figure:: /_static/images/en-us_image_0000001809029916.png
      :alt: **Figure 6** New Simple Volume Wizard

      **Figure 6** New Simple Volume Wizard

#. Specify the volume size and click **Next**. The default value is the maximum size.


   .. figure:: /_static/images/en-us_image_0000001809189760.png
      :alt: **Figure 7** Specify Volume Size

      **Figure 7** Specify Volume Size

#. Assign the drive letter and click **Next**.


   .. figure:: /_static/images/en-us_image_0000001855868569.png
      :alt: **Figure 8** Assign Drive Letter or Path

      **Figure 8** Assign Drive Letter or Path

#. On the displayed **Format Partition** page, click **Format this volume with the following settings**, set parameters based on the requirements, and select **Perform a quick format**. Then, click **Next**.


   .. figure:: /_static/images/en-us_image_0000001855948597.png
      :alt: **Figure 9** Format Partition

      **Figure 9** Format Partition


   .. figure:: /_static/images/en-us_image_0000001809029928.png
      :alt: **Figure 10** Completing the partition creation

      **Figure 10** Completing the partition creation

   .. important::

      The partition sizes supported by file systems vary. Choose an appropriate file system format based on your service requirements.

#. Click **Finish**. Wait for the initialization to complete. When the volume status changes to **Healthy**, the initialization has finished successfully.


   .. figure:: /_static/images/en-us_image_0000001809189772.png
      :alt: **Figure 11** Disk initialization succeeded

      **Figure 11** Disk initialization succeeded
