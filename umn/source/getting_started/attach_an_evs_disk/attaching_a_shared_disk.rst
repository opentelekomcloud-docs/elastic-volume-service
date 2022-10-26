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

-  If a shared disk is in the **In-use** state, ensure that the maximum number of servers that the disk can be attached to has not been reached.

-  All the servers of a shared disk must run either Windows or Linux no matter the disk is attached to them in a batch or individually.

   For example, if you attach a shared disk to multiple Windows servers in a batch and then detach it from all its servers, the disk cannot be attached to Linux servers later. This is because Windows and Linux support different file systems and cannot identify the original file system on the disk. Improper operations may damage the original file system.

-  A shared disk can only be used as a data disk. It cannot be used as a system disk.

Attaching the Disk on the EVS Console
-------------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Under **Storage**, click **Elastic Volume Service**.

   The disk list page is displayed.

#. Locate the target disk in the list and click **Attach**.

   The **Attach Disk** dialog box is displayed.

   Shared disks support batch attachment so that you can attach a shared disk to multiple servers at a time. The left area in the **Attach Disk** dialog box shows the server list. After you select the target servers, the selected servers will be displayed in the right area.


   .. figure:: /_static/images/en-us_image_0152639916.png
      :alt: **Figure 1** Attach Disk

      **Figure 1** Attach Disk

#. Select the target servers and then select a device name from the drop-down list for each server you selected. Ensure that the disk and servers are in the same AZ.

#. Click **OK** to return to the disk list page. The status of the disk is **Attaching**, indicating that the disk is being attached to the servers. When the disk status changes to **In-use**, the disk is successfully attached.

   .. important::

      If you simply attach a shared disk to multiple servers, files cannot be shared between the servers as shared disks do not have the cluster capability. Therefore, build a shared file system or deploy a cluster management system to share files between servers.

.. |image1| image:: /_static/images/en-us_image_0237893718.png
