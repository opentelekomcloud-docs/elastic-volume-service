:original_name: evs_01_0076.html

.. _evs_01_0076:

Attaching an Existing Shared Disk
=================================

Scenarios
---------

This section describes how to attach an existing shared disk to a server to be used as a data disk.

You can view the disk information in the disk list. A shared disk can be attached to servers to be used as a data disk when all of the following conditions are met:

-  Disk Sharing: Enabled
-  Function: Data disk
-  Status: In-use or Available

Notes and Constraints
---------------------

.. important::

   If you simply attach a shared disk to multiple servers, files cannot be shared among them. Because there are no mutually agreed data read/write rules among them, read and write operations from them may interfere with each other, or unpredictable errors may occur. To share files between the servers, set up a shared file system or a clustered management system first.

-  A shared disk can be attached to a maximum of 16 servers. These servers and the shared disk must be in the same AZ of a region.

-  A shared, **In-use** disk can only be attached to servers when the maximum number of servers that the disk can be attached to has not been reached.

-  A shared disk can only be attached to servers running the same type of OS (either Windows or Linux).

   For example, if you attach a shared disk to multiple Windows servers and then detach it, the shared disk cannot be attached to Linux servers later. This is because Windows and Linux support different file systems. Improper operations may damage the original file system.

-  A shared disk can only be used as a data disk. It cannot be used as a system disk.
-  Cloud servers created from ISO images are only used for OS installation. They have limited functions and cannot have EVS disks attached.
-  A server must be in the **Running** or **Stopped** state before disks can be attached to it.
-  A frozen disk cannot be attached.

Procedure
---------

#. Log in to the console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click |image2| in the upper left corner and choose **Storage** > **Elastic Volume Service**.

   The **Elastic Volume Service** page is displayed.

#. In the disk list, locate the disk and click **Attach**.

   -  Shared disks support batch attachment, so you can attach a shared disk to multiple servers. In the **Attach Disk** dialog box, the left area shows the server list. After you select the target servers, they will be displayed in the right area.
   -  A shared disk can only be attached to servers when the disk status is **Available** or **In-use**.

#. Select servers to attach the disk. Ensure that the disk and servers are in the same AZ. After you select servers, the system automatically inputs **Data disk** as the disk function.

#. Click **OK** to go back to the disk list page.

   The status of the disk is **Attaching**, indicating that the disk is being attached to the server. When the disk status changes to **In-use**, the disk has been attached.

#. (Optional) Mount the existing disk partition on a mount point if you are attaching the disk to Linux servers. The mount command is as follows:

   .. code-block::

      mount Disk partition Mount point

Helpful Links
-------------

To check out more attachment FAQs, see :ref:`Attachment <evs_01_0078>`.

.. |image1| image:: /_static/images/en-us_image_0000001959981992.png
.. |image2| image:: /_static/images/en-us_image_0000001959822188.jpg
