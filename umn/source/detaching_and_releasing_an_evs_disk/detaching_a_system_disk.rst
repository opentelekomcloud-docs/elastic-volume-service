:original_name: evs_01_0003.html

.. _evs_01_0003:

Detaching a System Disk
=======================

Scenarios
---------

If the file system on your system disk is damaged and your server cannot be started, you can detach the system disk and attach it to another server as a data disk. After the file system is fixed, you can re-attach the disk to the original server as the system disk.

If you no longer need a system disk or want to replace it with a new one, you can detach the system disk.

A system disk can only be detached offline, which means that its server must be in the **Stopped** state before the system disk is detached. To detach a system disk from a running server, you must first stop the server and then detach the disk.

.. note::

   -  For an attached system disk, the disk function is displayed as **System disk**, and the disk status is displayed as **In-use** in the disk list. After a system disk is detached from the server, the disk function changes to **Bootable disk**, and the status changes to **Available**.
   -  Bootable disks are the system disks detached from servers. A bootable disk can be re-attached to a server and be used as a system disk or data disk depending on the disk function selected.

Constraints
-----------

-  A system disk can only be detached offline, which means that its server must be in the **Stopped** state before you can detach it. To detach a system disk from a running server, you must first stop the server and then detach the disk.
-  After a system disk is detached, some operations cannot be performed on the original server and the system disk. The restricted operations are as follows:

   -  Server: starting the server, remote login, resetting the password, changing server billing mode, changing server specifications, changing the OS, reinstalling the OS, creating images, creating backups, adding disks, changing the security group, and changing the VPC

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Under **Compute**, click **Elastic Cloud Server**.

   The **Elastic Cloud Server** page is displayed.

#. In the server list, locate the row that contains the server whose system disk is to be detached, click **More** in the **Operation** column, and choose **Stop**.

   When the server status changes to **Stopped**, the server has been stopped.

#. Click the name of this server.

   The server details page is displayed.

#. Click the **Disks** tab to view the system disk attached to the server.

#. Locate the row that contains the system disk and click **Detach**.

   The **Detach Disk** dialog box is displayed, as shown in :ref:`Figure 1 <evs_01_0003__fig13846812115521>`.

   .. _evs_01_0003__fig13846812115521:

   .. figure:: /_static/images/en-us_image_0152756082.png
      :alt: **Figure 1** Detach Disk (system disk)

      **Figure 1** Detach Disk (system disk)

#. Click **Yes** to detach the disk.

   After the operation had succeeded, the detached system disk is no longer displayed under the **Disks** tab.

#. (Optional) Re-attach the bootable disk to a server. You can use it as a system disk or data disk depending on the disk function you select.

   -  To re-attach and use it as a system disk, see :ref:`Attaching an Existing System Disk <evs_01_0074>`.
   -  To re-attach and use it as a data disk, see :ref:`Attaching an Existing Non-Shared Disk <evs_01_0075>`.

Related Operations
------------------

For more detachment FAQs, see :ref:`Detachment <evs_01_0079>`.

.. |image1| image:: /_static/images/en-us_image_0237893718.png
