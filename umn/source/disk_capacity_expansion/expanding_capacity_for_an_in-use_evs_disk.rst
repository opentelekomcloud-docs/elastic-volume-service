:original_name: evs_01_0007.html

.. _evs_01_0007:

Expanding Capacity for an In-use EVS Disk
=========================================

Scenarios
---------

This section describes how to expand the capacity of an In-use EVS disk on the management console. The In-use status indicates that the disk has been attached to a server. You do not need to detach the disk when expanding an In-use disk.

.. _evs_01_0007__section158147122515:

Constraints
-----------

-  Currently, disk capacities can only be expanded, but cannot be reduced.

-  When expanding an In-use disk, the server containing this disk must be in the **Running** or **Stopped** state.

-  A shared disk cannot be expanded in the **In-use** state. To expand a shared In-use disk, you must detach it from all its servers, wait until its status changes to **Available**, and then expand its capacity. For more information, see :ref:`Expanding Capacity for an Available EVS Disk <evs_01_0008>`.

-  Only some server OSs support capacity expansion of In-use disks. For details, see the official document of the corresponding OS.

   If the server OS does not support capacity expansion of In-use disks, detach the disk and then expand its capacity. Otherwise, you may need to stop and then start the server after the expansion to make the additional space available.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Under **Storage**, click **Elastic Volume Service**.

   The disk list page is displayed.

#. Determine whether to view the server information before expanding the disk.

   -  If you need to view the server information, perform the following procedure:

      a. In the disk list, click the name of the to-be-expanded disk.

         The disk details page is displayed.

      b. Click the **Attachments** tab to view the server where the target disk has been attached.

      c. Click **Expand Capacity** in the upper right corner of the page.

         The expansion page is displayed.

   -  If you do not need to view the server information, perform the following procedure:

      a. In the disk list, locate the row that contains the target disk and click **Expand Capacity** in the **Operation** column.

         The expansion page is displayed.

#. Set the **Add Capacity (GB)** parameter and click **Next**.

#. On the **Details** page, check the disk information again.

   -  If you do not need to modify the specifications, click **Submit** to start the expansion.
   -  If you need to modify the specifications, click **Previous** to modify parameters.

   After the specifications are submitted, go back to the disk list page.

#. In the disk list, view the capacity of the target disk.

   When the disk status changes from **Expanding** to **In-use** and the disk capacity increases, the expansion has succeeded.

   .. note::

      If the expansion fails, technical support personnel will contact you and help you handle this error. Do not perform any operations on the disk before the technical support personnel contact you. If you require that the error be handled as soon as possible, contact our technical support personnel. The disk will no longer be charged after its status changes to **Expansion failed**.

#. After a disk has been expanded on the management console, only the disk storage capacity is enlarged, but its additional space cannot be used directly. You must log in to the server and extend the disk partition and file system.

   The operation method varies depending on the server OS.

   -  In Windows, see :ref:`Extending Disk Partitions and File Systems (Windows Server 2008) <en-us_topic_0017616396>`.
   -  In Linux, see :ref:`Partition and File System Extension Preparations (Linux) <evs_01_0035>`.

.. |image1| image:: /_static/images/en-us_image_0237893718.png

