:original_name: evs_01_0007.html

.. _evs_01_0007:

Expanding Capacity for an In-use EVS Disk
=========================================

Scenarios
---------

This section describes how to expand the capacity of an **In-use** EVS disk on the management console. The **In-use** status indicates that the disk has been attached to a server. You do not need to detach the disk when expanding an **In-use** disk.

.. _evs_01_0007__en-us_topic_0077678449_section158147122515:

Notes and Constraints
---------------------

-  Disk capacity can be expanded, but cannot be reduced.

-  When expanding an **In-use** disk, the server attached with this disk must be in the **Running** or **Stopped** state.

-  A shared disk in the **In-use** state cannot be expanded. To expand such a disk, you must detach it from all its servers, wait until its status changes to **Available**, and then expand its capacity. For more information, see :ref:`Expanding Capacity for an Available EVS Disk <evs_01_0008>`.

-  Only some server OSs allow you to expand capacity while disks are **In-use**. For details, see the official document of the corresponding OS.

   For servers without such support, detach the disk and then expand its capacity. Otherwise, you may need to stop and then start the server after the expansion to make the additional space available.

Prerequisites
-------------

Disk data has been backed up using CBR or snapshots. For details about backups, see :ref:`Managing EVS Disk Backups <evs_01_0110>`. For details about snapshots, see :ref:`Creating an EVS Snapshot <evs_01_2721>`.

Procedure
---------

#. Log in to the console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Choose **Storage** > **Elastic Volume Service**.

   The **Elastic Volume Service** page is displayed.

#. Choose a way to expand the disk by determining whether you want to check server information first.

   -  If yes, perform the following procedure:

      a. In the disk list, click the name of the to-be-expanded disk.

         The disk details page is displayed.

      b. Click the **Attachments** tab to view the server where the target disk has been attached.

      c. Click **Expand Capacity** in the upper right corner of the page.

         The expansion page is displayed.

   -  If no, perform the following procedure:

      a. In the disk list, locate the row that contains the target disk and click **Expand Capacity** in the **Operation** column.

         The expansion page is displayed.

#. Set the **New Capacity** parameter and click **Next**.

#. On the **Details** page, check the disk configuration.

   -  Click **Submit** to start the expansion.
   -  Click **Previous** to change the settings.

   After the configuration is submitted, go back to the disk list page.

#. In the disk list, view the capacity of the target disk.

   When the disk status changes from **Expanding** to **In-use** and the disk capacity increases, the expansion has succeeded.

   .. note::

      When the status of the disk is **Expanding**, you are not allowed to modify the specifications of the ECS where the disk is attached.

   .. note::

      If the expansion fails, technical support personnel will contact you and help you handle this error. Do not perform any operations on the disk before the technical support personnel contact you. If you require that the error be handled as soon as possible, contact our technical support personnel. Disks whose capacities failed to be expanded are not billed.

#. Log in to the server and extend the partition and file system after the disk has been expanded on the console, because previous steps only enlarge the disk space.

   The operations vary depending on the server OS.

   -  For Windows, see :ref:`Extending Disk Partitions and File Systems (Windows Server 2008) <en-us_topic_0017616396>`.
   -  For Linux, see :ref:`Partition and File System Extension Preparations (Linux) <evs_01_0035>`.

.. |image1| image:: /_static/images/en-us_image_0237893718.png
