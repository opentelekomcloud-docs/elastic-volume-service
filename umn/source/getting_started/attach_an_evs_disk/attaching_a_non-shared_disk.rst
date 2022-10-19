:original_name: evs_01_0036.html

.. _evs_01_0036:

Attaching a Non-Shared Disk
===========================

Scenarios
---------

Independently created EVS disks are data disks. In the disk list, the function of such disks is displayed as **Data disk**, and the status is displayed as **Available**. In this case, you need to attach the data disks to servers for use.

A system disk must be created during a server creation and is automatically attached. In the disk list, the function of such disks is displayed as **System disk**, and the status is displayed as **In-use**. After a system disk is detached from a server, the disk function changes to **Bootable disk**, and the status changes to **Available**.

.. note::

   Bootable disks are the system disks detached from servers. A bootable disk can be re-attached to a server and be used as a system disk or data disk depending on the device name selected.

This section describes how to attach a non-shared disk. A non-shared disk can be attached to one server only.

Attaching the Disk on the EVS Console
-------------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Under **Storage**, click **Elastic Volume Service**.

   The disk list page is displayed.

#. Locate the target disk in the list and click **Attach**.

   The **Attach Disk** dialog box is displayed, as shown in :ref:`Figure 1 <evs_01_0036__fig15846164615421>`.

   .. _evs_01_0036__fig15846164615421:

   .. figure:: /_static/images/en-us_image_0133519241.png
      :alt: **Figure 1** Attach Disk dialog box


      **Figure 1** Attach Disk dialog box

#. Select the server and then select a device name from the drop-down list. Ensure that the disk and server are in the same AZ.

#. Click **OK** to return to the disk list page. The status of the disk is **Attaching**, indicating that the disk is being attached to the server. When the disk status changes to **In-use**, the disk is successfully attached.

#. Initialize the disk.

   After the disk has been attached to a server, the disk can be used only after you have initialized it. For details, see :ref:`Introduction to Data Disk Initialization Scenarios and Partition Styles <evs_01_0038>`.

.. |image1| image:: /_static/images/en-us_image_0237893718.png

