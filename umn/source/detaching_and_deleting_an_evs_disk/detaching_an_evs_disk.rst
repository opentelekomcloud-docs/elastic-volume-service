:original_name: evs_01_0003.html

.. _evs_01_0003:

Detaching an EVS Disk
=====================

Scenarios
---------

+-----------------+----------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------+
| Disk Function   | Server Status                                                                    | Scenarios                                                                                                                                                                                                                                                                   | Operation Instruction                                                                            |
+=================+==================================================================================+=============================================================================================================================================================================================================================================================================+==================================================================================================+
| System disk     | Only offline detachment is supported.                                            | -  If the file system on your system disk is damaged and the server cannot be started, you can detach the system disk and attach it to another server as a data disk. After the file system is fixed, you can re-attach the disk to the original server as the system disk. | :ref:`Detaching a System Disk <evs_01_0003__en-us_topic_0077656290_section58976207172837>`       |
|                 |                                                                                  | -  If you no longer need a system disk or want to replace it with a new one, you can detach it.                                                                                                                                                                             |                                                                                                  |
|                 | You can only detach a system disk when the server status is **Stopped**.         |                                                                                                                                                                                                                                                                             |                                                                                                  |
+-----------------+----------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------+
| Data disk       | Both online detachment and offline detachment are supported.                     | -  If you want to use a data disk on another server in the same region and AZ, you can detach it and then attach it to that server.                                                                                                                                         | :ref:`Detaching a Non-Shared Data Disk <evs_01_0003__en-us_topic_0077656290_section99431142597>` |
|                 |                                                                                  | -  If a data disk is no longer required, you can detach it and then delete it.                                                                                                                                                                                              |                                                                                                  |
|                 | You can detach a data disk when the server status is **Stopped** or **Running**. |                                                                                                                                                                                                                                                                             | :ref:`Detaching a Shared Data Disk <evs_01_0003__en-us_topic_0077656290_section547610551918>`    |
+-----------------+----------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------+

.. note::

   -  For an attached system disk, the disk function is displayed as **System disk**, and the disk status is displayed as **In-use** in the disk list. After the system disk is detached, the disk function changes to **Bootable disk**, and the status changes to **Available**.
   -  Bootable disks are the system disks detached from servers. A bootable disk can be re-attached to a server to be used as a system disk or data disk depending on the disk function selected.
   -  For an attached data disk, the disk function is displayed as **Data disk**, and the disk status is displayed as **In-use** in the disk list. After the data disk is detached, the disk function remains unchanged, and the status changes to **Available**. For a shared disk, the status changes to **Available** only after it is detached from all its servers.

Notes and Constraints
---------------------

-  You can attach SCSI disks to BMSs and use them as data disks.
-  After a system disk is detached, some operations cannot be performed on the original server and the system disk. The restrictions are as follows:

   -  Server: starting the server, remote login, resetting the password, changing server billing mode, changing server specifications, changing the OS, reinstalling the OS, creating images, creating backups, adding disks, changing the security group, and changing the VPC

Prerequisites
-------------

-  Before detaching an EVS disk from a running Windows server, ensure that no programs are reading data from or writing data to the disk. Otherwise, data will be lost.

-  Before detaching an EVS disk from a running Linux server, you must log in to the server and run the **umount** command to cancel the association between the disk and the file system, and ensure that no programs are reading data from or writing data to the disk. Otherwise, you will not be able to detach the disk.

.. _evs_01_0003__en-us_topic_0077656290_section58976207172837:

Detaching a System Disk
-----------------------

#. Log in to the console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Choose **Compute** > **Elastic Cloud Server**.

   The **Elastic Cloud Server** page is displayed.

#. In the server list, locate the row that contains the server whose system disk is to be detached, click **More** in the **Operation** column, and choose **Stop**.

   When the server status changes to **Stopped**, the server has been stopped.

#. Click the name of this server.

   The server details page is displayed.

#. Click the **Disks** tab to view the system disk attached to the server.

#. Locate the row that contains the system disk and click **Detach**.

   The **Detach Disk** dialog box is displayed.


   .. figure:: /_static/images/en-us_image_0152756082.png
      :alt: **Figure 1** Detach Disk (system disk)

      **Figure 1** Detach Disk (system disk)

#. Click **Yes** to detach the disk.

   After the operation had succeeded, the detached system disk is no longer displayed under the **Disks** tab.

#. (Optional) :ref:`Re-attach <evs_01_0002>` the bootable disk to a server. You can use it as a system disk or data disk depending on the disk function you select.

.. _evs_01_0003__en-us_topic_0077656290_section99431142597:

Detaching a Non-Shared Data Disk
--------------------------------

#. Log in to the console.

#. Click |image2| in the upper left corner and select the desired region and project.

#. Click |image3| in the upper left corner and choose **Storage** > **Elastic Volume Service**.

   The **Elastic Volume Service** page is displayed.

#. Choose a way to detach the disk by determining whether you want to check the server information first.

   -  If yes, perform the following procedure:

      a. In the disk list, click the name of the to-be-detached disk.

         The disk details page is displayed.

      b. Click the **Attachments** tab to view the server where the disk has been attached.

      c. Click |image4| to select the server and click **Detach Disk**.

         The **Detach Disk** dialog box is displayed.


         .. figure:: /_static/images/en-us_image_0000001962012184.png
            :alt: **Figure 2** Detach Disk

            **Figure 2** Detach Disk

      d. Click **Yes** to detach the disk.

   -  If no, perform the following procedure:

      a. In the disk list, locate the row that contains the target disk and choose **More** > **Detach** in the **Operation** column.

         The **Detach Disk** dialog box is displayed.


         .. figure:: /_static/images/en-us_image_0000001962012192.png
            :alt: **Figure 3** Detach Disk dialog box

            **Figure 3** Detach Disk dialog box

      b. Click **Yes** to detach the disk.

   In the disk list, the disk status is **Detaching**, indicating that the disk is being detached from the server.

   When the status changes to **Available**, the disk has been detached.

.. _evs_01_0003__en-us_topic_0077656290_section547610551918:

Detaching a Shared Data Disk
----------------------------

#. Log in to the console.

#. Click |image5| in the upper left corner and select the desired region and project.

#. Choose **Storage** > **Elastic Volume Service**.

   The **Elastic Volume Service** page is displayed.

#. Choose a way to detach the disk by determining whether you want to check server information first.

   -  If yes, perform the following procedure:

      a. In the disk list, click the name of the to-be-detached disk.

         The disk details page is displayed.

      b. Click the **Attachments** tab to view the servers where the disk has been attached.

      c. Click |image6| to select servers and click **Detach Disk**.

         Shared EVS disks support batch detachment so that you can select multiple servers at a time.

         The **Detach Disk** dialog box is displayed.


         .. figure:: /_static/images/en-us_image_0000001998573089.png
            :alt: **Figure 4** Detaching a shared disk

            **Figure 4** Detaching a shared disk

      d. Click **Yes** to detach the disk.

   -  If no, perform the following procedure:

      a. In the disk list, locate the row that contains the target disk and choose **More** > **Detach** in the **Operation** column.

         The **Detach Disk** dialog box is displayed.


         .. figure:: /_static/images/en-us_image_0000001998573101.png
            :alt: **Figure 5** Detaching a shared disk dialog box

            **Figure 5** Detaching a shared disk dialog box

      b. Click |image7| to select servers.

         Shared EVS disks support batch detachment so that you can select multiple servers at a time.

      c. Click **Yes** to detach the disk.

   In the disk list, the disk status is **Detaching**, indicating that the disk is being detached from the server.

   If a shared disk has been attached to multiple servers and you only detach it from some of the servers, the disk status will go back to **In-use** after the disk has been detached from the servers. The disk status changes to **Available** only after the disk has been detached from all the servers.

Helpful Links
-------------

To check out more detachment FAQs, see :ref:`Detachment <evs_01_0079>`.

.. |image1| image:: /_static/images/en-us_image_0237893718.png
.. |image2| image:: /_static/images/en-us_image_0237893718.png
.. |image3| image:: /_static/images/en-us_image_0000001933286285.jpg
.. |image4| image:: /_static/images/en-us_image_0000001998573081.png
.. |image5| image:: /_static/images/en-us_image_0237893718.png
.. |image6| image:: /_static/images/en-us_image_0238263087.png
.. |image7| image:: /_static/images/en-us_image_0238263087.png
