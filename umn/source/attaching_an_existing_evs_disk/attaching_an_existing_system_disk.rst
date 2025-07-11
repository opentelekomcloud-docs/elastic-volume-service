:original_name: evs_01_0074.html

.. _evs_01_0074:

Attaching an Existing System Disk
=================================

Scenarios
---------

This section describes how to attach an existing system disk.

System disks can only be attached offline, which means that the server must be in the **Stopped** state.

You can view the disk function in the disk list. A disk can be attached to a server to be used as the system disk only when its function is **Bootable disk** and its status is **Available**.

.. note::

   -  Bootable disks are the system disks detached from servers. A bootable disk can be re-attached to a server to be used as a system disk or data disk depending on the disk function selected.

Notes and Constraints
---------------------

-  Cloud servers created from ISO images are only used for OS installation. They have limited functions and cannot have EVS disks attached.
-  A non-shared disk can be attached to one server only.
-  The disk and server must be in the same region and AZ.
-  A server must be in the **Running** or **Stopped** state before disks can be attached to it.
-  A frozen disk cannot be attached.

Procedure
---------

#. Log in to the console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click |image2| in the upper left corner and choose **Storage** > **Elastic Volume Service**.

   The **Elastic Volume Service** page is displayed.

#. In the disk list, locate the disk and click **Attach**.

#. Select a server to attach the disk. Ensure that the disk and server are in the same AZ and that the server is in the **Stopped** state. After you select the server, the system automatically inputs **System disk** as the disk function.

   One device name can be used for one disk only. For how to obtain the disk name in the OS, see FAQ "How Do I Obtain My Disk Name in the ECS OS Using the Device Identifier Provided on the Console?" in the *Elastic Cloud Server FAQs*.

#. Click **OK** to go back to the disk list page.

   The status of the disk is **Attaching**, indicating that the disk is being attached to the server. When the function of the disk changes from **Bootable disk** to **System disk** and the disk status changes to **In-use**, the disk has been attached.

Related Links
-------------

To check out more attachment FAQs, see :ref:`Attachment <evs_01_0078>`.

.. |image1| image:: /_static/images/en-us_image_0000002335562397.png
.. |image2| image:: /_static/images/en-us_image_0000002301563082.jpg
