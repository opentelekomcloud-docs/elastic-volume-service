:original_name: evs_01_0076.html

.. _evs_01_0076:

Attaching an Existing Shared Disk
=================================

Scenarios
---------

This section describes how to attach an existing shared disk to a server and use it as a data disk.

You can view the disk information in the disk list. A shared disk can be attached to servers and used as a data disk when all of the following conditions are met:

-  Disk Sharing: Enabled
-  Function: Data disk
-  Status: In-use or Available

Constraints
-----------

.. important::

   If you simply attach a shared disk to multiple servers, files cannot be shared among them. Because there are no mutually agreed data read/write rules among servers, read and write operations from them may interfere with each other, or unpredictable errors may occur. To share files between servers, set up a shared file system or a clustered management system first.

-  A shared disk can be attached to a maximum of 16 servers. These servers and the shared disk must be in the same AZ within a region.

-  A shared, **In-use** disk can be attached to other servers only when the maximum number of servers that the disk can be attached to has not been reached.

-  All the servers attached with a shared disk must run either Windows or Linux.

   For example, if you attach a shared disk to multiple Windows servers and then detach it from these servers, the shared disk cannot be attached to Linux servers later. This is because Windows and Linux support different file systems and cannot identify the original file system on the disk. Improper operations may damage the original file system.

-  A shared disk can only be used as a data disk. It cannot be used as a system disk.
-  Cloud servers created from ISO images are only used for OS installation. They have limited functions and cannot have EVS disks attached.
-  A shared disk can be attached only when the servers' statuses are **Running** or **Stopped**.
-  A frozen disk cannot be attached.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Under **Storage**, click **Elastic Volume Service**.

   The disk list page is displayed.

#. Locate the target disk in the list and click **Attach**.

   -  Shared disks support batch attachment so that you can attach a shared disk to multiple servers. The left area in the **Attach Disk** dialog box shows the server list. After you select the target servers, the selected servers will be displayed in the right area.
   -  A shared disk can be attached to servers only when the disk status is **Available** or **In-use**.

#. Select the target servers you want to attach the shared disk. Ensure that the disk and servers are in the same AZ. After you select the servers, **Data disk** is automatically entered as the disk function for each server.

#. Click **OK** to return to the disk list page.

   The status of the disk is **Attaching**, indicating that the disk is being attached to the servers. When the disk status changes to **In-use**, the disk is successfully attached.

#. (Optional) Mount the existing disk partition to a mount point if you have attached the disk to a Linux server. The mount command is as follows:

   .. code-block::

      mount Disk partition Mount point

Related Operations
------------------

For more attachment FAQs, see :ref:`Attachment <evs_01_0078>`.

.. |image1| image:: /_static/images/en-us_image_0237893718.png
