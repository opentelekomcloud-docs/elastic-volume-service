:original_name: evs_01_0037.html

.. _evs_01_0037:

Attaching a Shared Disk
=======================

Scenarios
---------

Independently created EVS disks are data disks. In the disk list, the function of such disks is displayed as **Data disk**, and the status is displayed as **Available**. In this case, you need to attach the data disks to servers for use.

This section describes how to attach a shared disk.

Constraints
-----------

-  A shared disk can be attached to a maximum of 16 servers. These servers and the shared disk must be in the same AZ within a region.

   .. important::

      If you simply attach a shared disk to multiple servers, files cannot be shared among them. Because there are no mutually agreed data read/write rules among servers, read and write operations from them may interfere with each other, or unpredictable errors may occur. To share files between servers, set up a shared file system or a clustered management system first.

-  If a shared disk is in the **In-use** state, ensure that the maximum number of servers that the disk can be attached to has not been reached.

-  All the servers attached with a shared disk must run either Windows or Linux.

   For example, if you attach a shared disk to multiple Windows servers and then detach it from these servers, the shared disk cannot be attached to Linux servers later. This is because Windows and Linux support different file systems and cannot identify the original file system on the disk. Improper operations may damage the original file system.

-  A shared disk can only be used as a data disk. It cannot be used as a system disk.
-  Cloud servers created from ISO images are only used for OS installation. They have limited functions and cannot have EVS disks attached.

Attaching the Disk on the EVS Console
-------------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Under **Storage**, click **Elastic Volume Service**.

   The disk list page is displayed.

#. Locate the target disk in the list and click **Attach**.

   The **Attach Disk** dialog box is displayed.

   Shared disks support batch attachment so that you can attach a shared disk to multiple servers. The left area in the **Attach Disk** dialog box shows the server list. After you select the target servers, the selected servers will be displayed in the right area.


   .. figure:: /_static/images/en-us_image_0152639916.png
      :alt: **Figure 1** Attach Disk

      **Figure 1** Attach Disk

#. Select the target servers and then select a device name from the drop-down list for each server you selected. Ensure that the disk and servers are in the same AZ.

#. Click **OK** to return to the disk list page. The status of the disk is **Attaching**, indicating that the disk is being attached to the servers. When the disk status changes to **In-use**, the disk is successfully attached.

Follow-Up Operations
--------------------

If you are attaching a new disk, you must then log in to the server and initialize the disk before it can be used. To learn how to initialize disks, see :ref:`Introduction to Data Disk Initialization Scenarios and Partition Styles <evs_01_0038>`.

.. |image1| image:: /_static/images/en-us_image_0237893718.png
