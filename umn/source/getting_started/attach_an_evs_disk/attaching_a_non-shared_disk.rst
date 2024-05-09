:original_name: evs_01_0036.html

.. _evs_01_0036:

Attaching a Non-Shared Disk
===========================

Scenarios
---------

Separately created EVS disks are data disks. In the disk list, the function of such disks is displayed as **Data disk**, and the status is displayed as **Available**. In this case, you need to attach the data disks to servers for use.

A system disk must be created together with an ECS and is automatically attached. In the disk list, the function of such disks is displayed as **System disk**, and the status is displayed as **In-use**. After a system disk is detached from an ECS, the disk function changes to **Bootable disk**, and the status changes to **Available**.

.. note::

   Bootable disks are the system disks detached from servers. A bootable disk can be re-attached to a server and be used as a system disk or data disk depending on the disk function selected. For details, see :ref:`Attaching an Existing System Disk <evs_01_0074>`.

This section describes how to attach a non-shared disk.

Prerequisites
-------------

-  The non-shared disk status is **Available**.

Constraints
-----------

-  Cloud servers created from ISO images are only used for OS installation. They have limited functions and cannot have EVS disks attached.
-  A non-shared disk can be attached to one server only.
-  The disk and the server must be in the same region and AZ.
-  A shared disk can be attached only when the servers' statuses are **Running** or **Stopped**.
-  A frozen disk cannot be attached.

Attaching the Disk on the EVS Console
-------------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Under **Storage**, click **Elastic Volume Service**.

   The disk list page is displayed.

#. Locate the target disk in the list and click **Attach**.

   The **Attach Disk** dialog box is displayed.


   .. figure:: /_static/images/en-us_image_0133519241.png
      :alt: **Figure 1** Attach Disk dialog box

      **Figure 1** Attach Disk dialog box

#. Select the server and then select the disk function from the drop-down list. Ensure that the disk and server are in the same AZ.

   One device name can be used for one disk only. For how to obtain the disk name in the OS, see section "How Do I Obtain My Disk Name in the ECS OS Using the Device Identifier Provided on the Console?" in the *Elastic Cloud Server User Guide*.

#. Click **OK** to return to the disk list page.

   The status of the disk is **Attaching**, indicating that the disk is being attached to the server. When the disk status changes to **In-use**, the disk is successfully attached.

#. Initialize the disk.

   After the disk has been attached to a server, the disk can be used only after you have initialized it. For details, see :ref:`Introduction to Data Disk Initialization Scenarios and Partition Styles <evs_01_0038>`.

Attaching the Disk on the ECS Console
-------------------------------------

#. Log in to the management console.

#. Click |image2| in the upper left corner and select your region and project.

#. Under **Computing**, choose **Elastic Cloud Server**.

#. In the search box above the upper right corner of the ECS list, enter the ECS name, IP address, or ID for search.

#. Click the name of the target ECS.

   The page providing details about the ECS is displayed.

#. Click the **Disks** tab. Then, click **Attach Disk**.

   The **Attach Disk** dialog box is displayed.


   .. figure:: /_static/images/en-us_image_0218677657.png
      :alt: **Figure 2** Attach Disk

      **Figure 2** Attach Disk

#. Select the target disk and specify it as the system disk or a data disk.

   .. note::

      -  If no disks are available, click **Create Disk** in the lower part of the list.
      -  For the restrictions on attaching disks, see FAQ "What Are the Requirements for Attaching an EVS Disk to an ECS?" in the *Elastic Cloud Server User Guide*.
      -  The device names for the local disks and EVS disks attached to a disk-intensive ECS comply with the following rules:

         -  System disk: sda or vda
         -  Local disk: the device name following sda or vda in alphabetical order
         -  EVS disk: the device name in alphabetical order following those used by local disks

#. Click **OK**.

   After the disk is attached, you can view the information about it on the **Disks** tab.


   .. figure:: /_static/images/en-us_image_0162733605.png
      :alt: **Figure 3** Viewing the newly attached disk

      **Figure 3** Viewing the newly attached disk

Follow-Up Operations
--------------------

If you are attaching a new disk, you must then log in to the server and initialize the disk before it can be used. To learn how to initialize disks, see :ref:`Introduction to Data Disk Initialization Scenarios and Partition Styles <evs_01_0038>`.

Related Operations
------------------

If your disk cannot be attached to a server, see :ref:`Why Can't I Attach My Disk to a Server? <evs_faq_0025>`.

If the disk you are going to attach contains data, see :ref:`Attaching an Existing Disk <evs_01_0073>`.

If the attached data disk is not showing up, see :ref:`Why Can't I View the Attached Data Disk on the Server? <evs_faq_0022>`.

.. |image1| image:: /_static/images/en-us_image_0237893718.png
.. |image2| image:: /_static/images/en-us_image_0210779229.png
