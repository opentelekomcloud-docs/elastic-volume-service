:original_name: evs_01_0008.html

.. _evs_01_0008:

Expanding Capacity for an Available EVS Disk
============================================

Scenarios
---------

This section describes how to expand the capacity of an Available EVS disk on the console. The Available status indicates that the disk has not been attached to any server.

Constraints
-----------

-  Disk capacity can be increased, but cannot be reduced.

-  A shared disk in the **In-use** state cannot be expanded. To expand such a disk, you must detach it from all its servers, wait until its status changes to **Available**, and then expand its capacity.

Prerequisites
-------------

Disk data has been backed up using CBR or snapshots. For details about backups, see :ref:`Managing EVS Disk Backups <evs_01_0110>`. For details about snapshots, see :ref:`Creating and Using an EVS Disk <evs_01_0057>`.

Procedure
---------

#. Log in to the console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Choose **Storage** > **Elastic Volume Service**.

   The **Elastic Volume Service** page is displayed.

#. In the disk list, locate the row that contains the target disk and click **Expand Capacity** in the **Operation** column.

   The capacity expansion page is displayed.

#. Set the **New Capacity** parameter and click **Next**.

#. On the **Details** page, check the disk settings.

   -  Click **Submit** to start the expansion.
   -  Click **Previous** to change the settings, if needed.

   After the configuration is submitted, go back to the disk list page.

#. In the disk list, view the capacity of the target disk.

   When the disk status changes from **Expanding** to **Available** and the disk capacity increases, the expansion has succeeded.

   .. note::

      If the expansion fails, technical support will contact you to resolve the issue. Do not perform any operations on the disk until technical support has contacted you. If you need a faster response, contact technical support directly. Disks with an **Expansion failed** status will not continue to be billed.

#. Attach the disk to the server. For details, see :ref:`Attaching an EVS Disk <evs_01_0107>`.

#. Log in to the server and extend the partition and file system after the disk has been expanded on the console, because previous steps only enlarge the disk space.

   The operations vary depending on the server OS.

   -  For Windows, see :ref:`Extending Disk Partitions and File Systems (Windows Server 2016) <evs_01_0126>`.
   -  For Linux, see :ref:`Extending Disk Partitions and File Systems (Linux) <evs_01_0094>`.

.. |image1| image:: /_static/images/en-us_image_0000002301561710.png
