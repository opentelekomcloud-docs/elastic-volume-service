:original_name: evs_01_0004.html

.. _evs_01_0004:

Detaching a Data Disk
=====================

Scenarios
---------

If you want to use a data disk on another server in the same region and AZ, you can detach the data disk and then attach it to that server.

If a data disk is no longer required, you can detach it and then delete it.

Data disks can be detached online or offline, meaning that the server using the to-be-detached data disk can either be in the **Running** or **Stopped** state.

-  ECS

   Detach a disk from a running server. For details, see **Storage** > **Detaching an EVS Disk from a Running ECS** in the *Elastic Cloud Server User Guide*.

-  BMS

   SCSI disks can be attached to BMSs and used as data disks. You can detach a data disk either from a running or stopped BMS.

.. note::

   For an attached data disk, the disk function is displayed as **Data disk**, and the disk status is displayed as **In-use** in the disk list. After the data disk has been detached from the server, the disk function remains unchanged, the disk status changes to **Available** for a non-shared data disk, and the disk status changes to **Available** for a shared data disk after it is detached from all its servers.

Precautions
-----------

Data may be lost after you detach an encrypted disk. For more information, see :ref:`If I Detach a Disk, Will I Lose the Data on My Disk? <evs_faq_0012>`.

Prerequisites
-------------

-  Before detaching an EVS disk from a running Windows ECS, ensure that no programs are reading data from or writing data to the disk. Otherwise, data will be lost.

-  Before detaching an EVS disk from a running Linux ECS, you must log in to the ECS and run the **umount** command to cancel the association between the disk and the file system. In addition, ensure that no programs are reading data from or writing data to the disk. Otherwise, detaching the disk will fail.

Detaching a Non-shared Disk
---------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Under **Storage**, click **Elastic Volume Service**.

   The disk list page is displayed.

#. Choose a way to detach the disk by determining whether you want to check server information first.

   -  If yes, perform the following procedure:

      a. In the disk list, click the name of the to-be-detached disk.

         The disk details page is displayed.

      b. Click the **Attachments** tab to view the server where the target disk has been attached.

      c. Click |image2| to select the server and click **Detach Disk**.

         The **Detach Disk** dialog box is displayed, as shown in :ref:`Figure 1 <evs_01_0004__fig146481428813>`.

         .. _evs_01_0004__fig146481428813:

         .. figure:: /_static/images/en-us_image_0163801956.png
            :alt: **Figure 1** Detach Disk

            **Figure 1** Detach Disk

      d. Click **Yes** to detach the disk.

   -  If no, perform the following procedure:

      a. In the disk list, locate the row that contains the target disk and choose **More** > **Detach** in the **Operation** column.

         The **Detach Disk** dialog box is displayed, as shown in :ref:`Figure 2 <evs_01_0004__fig715496815241>`.

         .. _evs_01_0004__fig715496815241:

         .. figure:: /_static/images/en-us_image_0152754019.png
            :alt: **Figure 2** Detach Disk dialog box

            **Figure 2** Detach Disk dialog box

      b. Click **Yes** to detach the disk.

   The disk list is displayed. The disk status is **Detaching**, indicating that the disk is being detached from the server.

   When the status changes to **Available**, the disk is successfully detached.

Detaching a Shared Disk
-----------------------

#. Log in to the management console.

#. Click |image3| in the upper left corner and select the desired region and project.

#. Under **Storage**, click **Elastic Volume Service**.

   The disk list page is displayed.

#. Choose a way to detach the disk by determining whether you want to check server information first.

   -  If yes, perform the following procedure:

      a. In the disk list, click the name of the to-be-detached disk.

         The disk details page is displayed.

      b. Click the **Attachments** tab to view the servers where the target disk has been attached.

      c. Click |image4| to select the server and click **Detach Disk**.

         Shared EVS disks support batch detachment so that you can select multiple servers at a time.

         The **Detach Disk** dialog box is displayed, as shown in :ref:`Figure 3 <evs_01_0004__fig10503132745>`.

         .. _evs_01_0004__fig10503132745:

         .. figure:: /_static/images/en-us_image_0163801385.png
            :alt: **Figure 3** Detaching a shared disk

            **Figure 3** Detaching a shared disk

      d. Click **Yes** to detach the disk.

   -  If no, perform the following procedure:

      a. In the disk list, locate the row that contains the target disk and choose **More** > **Detach** in the **Operation** column.

         The **Detach Disk** dialog box is displayed, as shown in :ref:`Figure 4 <evs_01_0004__fig36494313113211>`.

         .. _evs_01_0004__fig36494313113211:

         .. figure:: /_static/images/en-us_image_0152754508.png
            :alt: **Figure 4** Detaching a shared disk dialog box

            **Figure 4** Detaching a shared disk dialog box

      b. Click |image5| to select the server.

         Shared EVS disks support batch detachment so that you can select multiple servers at a time.

      c. Click **Yes** to detach the disk.

   The disk list page is displayed. The disk status is **Detaching**, indicating that the disk is being detached from the server.

   If the shared EVS disk has been attached to multiple servers and needs to be detached from only some of its servers, the disk status will go back to **In-use** after the disk has been detached from the target servers. The disk status changes to **Available** only when it has been detached from all the servers.

.. |image1| image:: /_static/images/en-us_image_0237893718.png
.. |image2| image:: /_static/images/en-us_image_0238263087.png
.. |image3| image:: /_static/images/en-us_image_0237893718.png
.. |image4| image:: /_static/images/en-us_image_0238263087.png
.. |image5| image:: /_static/images/en-us_image_0238263087.png
