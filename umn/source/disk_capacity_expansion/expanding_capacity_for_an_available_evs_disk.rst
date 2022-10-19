:original_name: evs_01_0008.html

.. _evs_01_0008:

Expanding Capacity for an Available EVS Disk
============================================

Scenarios
---------

This section describes how to expand the capacity of an Available EVS disk on the management console. The Available status indicates that the disk has not been attached to any server.

Constraints
-----------

-  Currently, disk capacities can only be expanded, but cannot be reduced.
-  A shared disk cannot be expanded in the **In-use** state. To expand a shared In-use disk, you must detach it from all its servers, wait until its status changes to **Available**, and then expand its capacity.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Under **Storage**, click **Elastic Volume Service**.

   The disk list page is displayed.

#. In the disk list, locate the row that contains the target disk and click **Expand Capacity** in the **Operation** column.

   The expansion page is displayed.

#. Set the **Add Capacity (GB)** parameter and click **Next**.

#. On the **Details** page, check the disk information again.

   -  If you do not need to modify the specifications, click **Submit** to start the expansion.
   -  If you need to modify the specifications, click **Previous** to modify parameters.

   After the specifications are submitted, go back to the disk list page.

#. In the disk list, view the capacity of the target disk.

   When the disk status changes from **Expanding** to **Available** and the disk capacity increases, the expansion has succeeded.

   .. note::

      If the expansion fails, technical support personnel will contact you and help you handle this error. Do not perform any operations on the disk before the technical support personnel contact you. If you require that the error be handled as soon as possible, contact our technical support personnel. The disk will no longer be charged after its status changes to **Expansion failed**.

#. Attach the disk to the server. For details, see :ref:`Attach an EVS Disk <evs_01_0107>`.

#. After a disk has been expanded on the management console, only the disk storage capacity is enlarged, but its additional space cannot be used directly. You must log in to the server and extend the disk partition and file system.

   The operation method varies depending on the server OS.

   -  In Windows, see :ref:`Extending Disk Partitions and File Systems (Windows Server 2008) <en-us_topic_0017616396>`.
   -  In Linux, see :ref:`Partition and File System Extension Preparations (Linux) <evs_01_0035>`.

.. |image1| image:: /_static/images/en-us_image_0237893718.png

