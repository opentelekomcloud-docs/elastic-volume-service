:original_name: evs_01_0108.html

.. _evs_01_0108:

Initializing a Windows Data Disk (Windows Server 2008)
======================================================

Scenarios
---------

This section uses Windows Server 2008 R2 Enterprise 64bit to describe how to initialize a data disk attached to a server running Windows.

The maximum disk capacity supported by MBR is 2 TB, and that supported by GPT is 18 EB. Therefore, use the GPT partition style if your disk capacity is larger than 2 TB. For details about disk partition styles, see :ref:`Introduction to Data Disk Initialization Scenarios and Partition Styles <evs_01_0038>`.

The method for initializing a disk varies depending on the OS running on the server. This document is used for reference only. For the detailed operations and differences, see the product documents of the corresponding OS.

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

   -  If :ref:`Figure 1 <evs_01_0108__fig40496387105554>` is displayed, the new disk is offline. Go to :ref:`3 <evs_01_0108__li33296033102625>`.
   -  If :ref:`Figure 4 <evs_01_0108__fig68332918241>` is displayed, the **Initialize Disk** window is prompted. Go to :ref:`5 <evs_01_0108__li34991214122212>`.

   .. _evs_01_0108__fig40496387105554:

   .. figure:: /_static/images/en-us_image_0095024494.png
      :alt: **Figure 1** Disk Management


      **Figure 1** Disk Management

#. .. _evs_01_0108__li33296033102625:

   Disks are displayed in the right pane. In the **Disk 1** area, right-click **Offline** and choose **Online** from the shortcut menu to online the disk.

   .. _evs_01_0108__fig102484362217:

   .. figure:: /_static/images/en-us_image_0132359404.png
      :alt: **Figure 2** Online the disk


      **Figure 2** Online the disk

   .. note::

      If the disk is offline, you need to online the disk before initializing it.

#. After making the disk online, the disk status changes from **Offline** to **Not Initialized**. Right-click the disk status and choose **Initialize Disk** from the shortcut menu, as shown in :ref:`Figure 3 <evs_01_0108__fig409808111224>`.

   .. _evs_01_0108__fig409808111224:

   .. figure:: /_static/images/en-us_image_0132360430.png
      :alt: **Figure 3** Initialize Disk


      **Figure 3** Initialize Disk

#. .. _evs_01_0108__li34991214122212:

   In the **Initialize Disk** dialog box, select the target disk, click **MBR (Master Boot Record)** or **GPT (GUID Partition Table)**, and click **OK**, as shown in :ref:`Figure 4 <evs_01_0108__fig68332918241>`.

   .. _evs_01_0108__fig68332918241:

   .. figure:: /_static/images/en-us_image_0097597141.png
      :alt: **Figure 4** Unallocated space


      **Figure 4** Unallocated space

   .. important::

      The maximum disk capacity supported by MBR is 2 TB, and that supported by GPT is 18 EB. Because a data disk currently supports up to 32 TB, use the GPT partition style if your disk capacity is larger than 2 TB.

      If you change the disk partition style after the disk has been used, the data on the disk will be cleared. Therefore, select a proper disk partition style when initializing the disk.

#. Right-click at the unallocated space and choose **New Simple Volume** from the shortcut menu, as shown in :ref:`Figure 5 <evs_01_0108__fig1945583522619>`.

   .. _evs_01_0108__fig1945583522619:

   .. figure:: /_static/images/en-us_image_0097597143.png
      :alt: **Figure 5** New Simple Volume


      **Figure 5** New Simple Volume

#. On the displayed **New Simple Volume Wizard** window, click **Next**.

   .. _evs_01_0108__fig1388010596281:

   .. figure:: /_static/images/en-us_image_0097597145.png
      :alt: **Figure 6** New Simple Volume Wizard


      **Figure 6** New Simple Volume Wizard

#. Specify the volume size and click **Next**. The default value is the maximum size.

   .. _evs_01_0108__fig311184311294:

   .. figure:: /_static/images/en-us_image_0097597147.png
      :alt: **Figure 7** Specify Volume Size


      **Figure 7** Specify Volume Size

#. Assign the driver letter and click **Next**.

   .. _evs_01_0108__fig1400313143015:

   .. figure:: /_static/images/en-us_image_0097597149.png
      :alt: **Figure 8** Assign Driver Letter or Path


      **Figure 8** Assign Driver Letter or Path

#. Select **Format this volume with the following settings**, set parameters based on the actual requirements, and select **Perform a quick format**. Then, click **Next**.

   .. _evs_01_0108__fig19840335173018:

   .. figure:: /_static/images/en-us_image_0097597151.png
      :alt: **Figure 9** Format Partition


      **Figure 9** Format Partition

   .. _evs_01_0108__fig183312171318:

   .. figure:: /_static/images/en-us_image_0097597153.png
      :alt: **Figure 10** Completing the partition creation


      **Figure 10** Completing the partition creation

   .. important::

      The partition sizes supported by file systems vary. Therefore, you are advised to choose an appropriate file system based on your service requirements.

#. Click **Finish**. Wait for the initialization to complete. When the volume status changes to **Healthy**, the initialization has finished successfully, as shown in :ref:`Figure 11 <evs_01_0108__fig14464150329>`.

   .. _evs_01_0108__fig14464150329:

   .. figure:: /_static/images/en-us_image_0097597155.png
      :alt: **Figure 11** Disk initialization succeeded


      **Figure 11** Disk initialization succeeded