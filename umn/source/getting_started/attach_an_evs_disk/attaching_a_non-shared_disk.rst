:original_name: evs_01_0036.html

.. _evs_01_0036:

Attaching a Non-Shared Disk
===========================

Scenarios
---------

Separately created EVS disks are data disks. In the disk list, the function of such disks is displayed as **Data disk**, and the status is displayed as **Available**. In this case, you need to attach the data disks to servers for use.

A system disk must be created together with a server and is automatically attached. In the disk list, the function of such disks is displayed as **System disk**, and the status is displayed as **In-use**. After a system disk is detached, the disk function changes to **Bootable disk**, and the status changes to **Available**.

.. note::

   Bootable disks are the system disks detached from servers. A bootable disk can be re-attached to a server to be used as a system disk or data disk depending on the disk function selected. For details, see :ref:`Attaching an Existing System Disk <evs_01_0074>`.

This section describes how to attach a non-shared disk.

Prerequisites
-------------

-  The non-shared disk status is **Available**.

Notes and Constraints
---------------------

-  ECSs created from ISO images are only used for OS installation. They have limited functions and cannot have EVS disks attached.
-  A non-shared disk can only be attached to one server.
-  The disk and the server must be in the same region and AZ.
-  A disk can only be attached when the ECS status is **Running** or **Stopped**.
-  A frozen EVS disk cannot be attached.

Attaching the Disk on the EVS Console
-------------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select a desired region and project.

#. Choose **Storage** > **Elastic Volume Service**.

   The **Elastic Volume Service** page is displayed.

#. In the disk list, locate the disk and click **Attach**.

   The **Attach Disk** dialog box is displayed.


   .. figure:: /_static/images/en-us_image_0000001949357721.png
      :alt: **Figure 1** Attach Disk dialog box

      **Figure 1** Attach Disk dialog box

#. Select a server and then select the disk function from the drop-down list. Ensure that the disk and the server are in the same AZ.

   One device name can be used for one disk only. For how to obtain the disk name in the OS, see FAQ "How Do I Obtain My Disk Name in the ECS OS Using the Device Identifier Provided on the Console?" in the *Elastic Cloud Server FAQs*.

#. Click **OK** to go back to the disk list page. The status of the disk is **Attaching**, indicating that the disk is being attached to the server. When the disk status changes to **In-use**, the disk is successfully attached.

#. Initialize the disk.

   After the disk has been attached, the disk can only be used after you have initialized it on the server. For details, see :ref:`Initialize an EVS Data Disk <evs_01_0058>`.

Attaching the Disk on the ECS Console
-------------------------------------

#. Log in to the management console.

#. Click |image2| in the upper left corner and select a desired region and project.

#. Choose **Compute** > **Elastic Cloud Server**.

#. In the search box above the upper right corner of the ECS list, enter the ECS name, IP address, or ID to search for the ECS.

#. Click the name of the ECS.

   The ECS details page is displayed.

#. Click the **Disks** tab. Then, click **Attach Disk**.

   The **Attach Disk** page is displayed.


   .. figure:: /_static/images/en-us_image_0000002032981318.png
      :alt: **Figure 2** Attach Disk

      **Figure 2** Attach Disk

#. Select the target disk and specify it as the system disk or a data disk.

   .. note::

      -  If no disks are available, click **Create Disk** in the lower part of the list.
      -  For the restrictions on attaching disks, see FAQ "What Are the Requirements for Attaching an EVS Disk to an ECS?" in the *Elastic Cloud Server User Guide*.
      -  The device names for the local disks and EVS disks attached to a disk-intensive ECS comply with the following rules:

         -  System disk: sda or vda
         -  Local disk: the device names in alphabetical order following sda or vda
         -  EVS disk: the device names in alphabetical order following those used by local disks

#. Click **OK**.

   After the disk is attached, you can view information about it on the **Disks** tab.


   .. figure:: /_static/images/en-us_image_0000002077234357.png
      :alt: **Figure 3** Viewing the newly attached disk

      **Figure 3** Viewing the newly attached disk

Follow-Up Operations
--------------------

If you are attaching a new disk, you must then log in to the server and initialize the disk before it can be used. To learn how to initialize disks, see :ref:`Initialize an EVS Data Disk <evs_01_0058>`.

Helpful Links
-------------

If your disk cannot be attached to a server, see :ref:`Why Can't I Attach My Disk to a Server? <evs_faq_0025>`.

If the disk you are going to attach contains data, see :ref:`Attaching an Existing EVS Disk <evs_01_0073>`.

If the attached data disk is not showing up, see :ref:`Why Can't I View the Attached Data Disk on the Server? <evs_faq_0022>`.

.. |image1| image:: /_static/images/en-us_image_0000002032822906.png
.. |image2| image:: /_static/images/en-us_image_0000002068902269.png
