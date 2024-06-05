:original_name: evs_01_0075.html

.. _evs_01_0075:

Attaching an Existing Non-Shared Disk
=====================================

Scenarios
---------

This section describes how to attach an existing non-shared disk to a server and use it as a data disk. A non-shared disk can be attached to one server only.

You can view the disk information in the disk list. A disk can be attached to a server and used as a data disk when all of the following conditions are met:

-  Disk Sharing: Disabled
-  Function: Bootable disk or Data disk
-  Status: Available

.. note::

   -  Bootable disks are the system disks detached from servers. A bootable disk can be re-attached to a server and be used as a system disk or data disk depending on the disk function selected.

Constraints
-----------

-  Cloud servers created from ISO images are only used for OS installation. They have limited functions and cannot have EVS disks attached.
-  A non-shared disk can be attached to one server only.
-  The disk and the server must be in the same region and AZ.
-  A shared disk can be attached only when the servers' statuses are **Running** or **Stopped**.
-  A frozen disk cannot be attached.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Under **Storage**, click **Elastic Volume Service**.

   The disk list page is displayed.

#. Locate the target disk in the list and click **Attach**.

#. Select a server to attach the disk. Ensure that the disk and server are in the same AZ. After you select a server, **Data disk** is automatically entered as the disk function for the server.

#. Click **OK** to return to the disk list page.

   The status of the disk is **Attaching**, indicating that the disk is being attached to the server. When the disk status changes to **In-use**, the disk is successfully attached.

#. (Optional) Mount the existing disk partition to a mount point if you have attached the disk to a Linux server. The mount command is as follows:

   .. code-block::

      mount Disk partition Mount point

Related Operations
------------------

For more attachment FAQs, see :ref:`Attachment <evs_01_0078>`.

.. |image1| image:: /_static/images/en-us_image_0237893718.png
