:original_name: evs_01_0074.html

.. _evs_01_0074:

Attaching an Existing System Disk
=================================

Scenarios
---------

This section describes how to attach an existing system disk.

System disks can only be attached offline, which means that the server must be in the **Stopped** state.

You can view the disk function in the disk list. A disk can be attached to a server and used as the system disk only when its function is **Bootable disk** and its status is **Available**.

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

#. Select a server to attach the disk. Ensure that the disk and server are in the same AZ and that the server is in the **Stopped** state. After you select a server, **System disk** is automatically entered as the disk function for the server.

   One device name can be used for one disk only. For how to obtain the disk name in the OS, see section "How Do I Obtain My Disk Name in the ECS OS Using the Device Identifier Provided on the Console?" in the *Elastic Cloud Server User Guide*.

#. Click **OK** to return to the disk list page.

   The status of the disk is **Attaching**, indicating that the disk is being attached to the server. When the function of the disk changes from **Bootable disk** to **System disk** and the disk status changes to **In-use**, the disk is successfully attached.

Related Operations
------------------

For more attachment FAQs, see :ref:`Attachment <evs_01_0078>`.

.. |image1| image:: /_static/images/en-us_image_0237893718.png
