:original_name: evs_01_0075.html

.. _evs_01_0075:

Attaching an Existing Non-Shared Disk
=====================================

Scenarios
---------

This section describes how to attach an existing non-shared disk to a server to be used as a data disk. A non-shared disk can be attached to one server only.

You can view the disk information in the disk list. A disk can be attached to a server to be used as a data disk when all of the following conditions are met:

-  Disk Sharing: Disabled
-  Function: Bootable disk or Data disk
-  Status: Available

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

#. Select a server to attach the disk. Ensure that the disk and server are in the same AZ. After you select the server, the system automatically inputs **Data disk** as the disk function.

#. Click **OK** to go back to the disk list page.

   The status of the disk is **Attaching**, indicating that the disk is being attached to the server. When the disk status changes to **In-use**, the disk has been attached.

#. (Optional) Mount the existing disk partition on a mount point if you are attaching the disk to a Linux server. The mount command is as follows:

   .. code-block::

      mount Disk partition Mount point

Helpful Links
-------------

To check out more attachment FAQs, see :ref:`Attachment <evs_01_0078>`.

.. |image1| image:: /_static/images/en-us_image_0000001959981980.png
.. |image2| image:: /_static/images/en-us_image_0000001959822180.jpg
