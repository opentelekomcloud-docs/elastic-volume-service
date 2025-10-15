:original_name: en-us_topic_0052554220.html

.. _en-us_topic_0052554220:

Device Types
============

What Device Types Are Available?
--------------------------------

There are two EVS device types: Virtual Block Device (VBD) and Small Computer System Interface (SCSI).

-  VBD is the default EVS device type. VBD EVS disks support only basic read/write SCSI commands.
-  SCSI EVS disks support transparent SCSI command transmission and allow the server OS to directly access the underlying storage media. Besides basic read/write SCSI commands, SCSI disks support advanced SCSI commands.

Device type is configured during creation. It cannot be changed after the disk has been created.

Common Application Scenarios and Usage Instructions of SCSI EVS Disks
---------------------------------------------------------------------

-  BMSs support only SCSI EVS disks.

-  Shared SCSI EVS disks: Shared SCSI EVS disks must be used together with a distributed file system or cluster software. Because most cluster applications, such as Windows MSCS, Veritas VCS, and Veritas CFS, require SCSI reservations, you are advised to use shared EVS disks with SCSI.

   SCSI reservations take effect only when shared SCSI EVS disks are attached to ECSs in the same ECS group.

Do I Need to Install a Driver for SCSI EVS Disks?
-------------------------------------------------

To use SCSI EVS disks, a cloud server must have a SCSI driver installed. If the SCSI driver is not pre-installed, you need to install it manually.

Check whether you need to manually install the driver based on the server type.

-  Bare Metal Server (BMS)

   Both the Windows and Linux images for BMSs are pre-installed with the required SDI card driver. Therefore, no driver needs to be installed.

-  KVM ECS

   You are advised to use SCSI EVS disks with KVM ECSs. Linux images and Windows images for KVM ECSs already have the required driver. Therefore, no driver needs to be installed for KVM ECSs.

   .. note::

      ECS virtualization types are categorized into KVM and Xen. For details, see `ECS Types <https://docs.otc.t-systems.com/en-us/usermanual/ecs/en-us_topic_0035470096.html>`__.

-  Xen ECS

   Due to driver limitations, you are advised not to use SCSI EVS disk with Xen ECSs.

   However, a few Windows and Linux images support SCSI EVS disks on Xen ECSs. For the supported images, see :ref:`Table 1 <en-us_topic_0052554220__en-us_topic_0078247521_table36381951181116>`.

   .. note::

      After confirming that the OS images of Xen ECSs support SCSI EVS disks, determine whether you need to install the driver:

      -  Public Windows images are preinstalled with the Paravirtual SCSI (PVSCSI) driver. Therefore, no driver needs to be installed.

      -  Private Windows images are not preinstalled with the PVSCSI driver. You need to download and install it explicitly.

         For details, see section "(Optional) Optimizing Windows Private Images" in the *Image Management Service User Guide*.

      -  Linux images are not preinstalled with the PVSCSI driver. You need to obtain the source code of the open-source Linux driver at https://github.com/UVP-Tools/SAP-HANA-Tools, compile the code, and then install the driver.

         Note that this driver is different from the PVSCSI drivers attached to some Linux distributions.

   .. _en-us_topic_0052554220__en-us_topic_0078247521_table36381951181116:

   .. table:: **Table 1** OSs supporting SCSI EVS disks

      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Virtualization Type   | OS                    | _                                                                                                                                                                             |
      +=======================+=======================+===============================================================================================================================================================================+
      | Xen                   | Windows               | See the Windows images listed on the **Public Images** page.                                                                                                                  |
      |                       |                       |                                                                                                                                                                               |
      |                       |                       | Log in to the console, choose **Image Management Service**, click the **Public Images** tab, and select **ECS image** and **Windows** from the drop-down lists, respectively. |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      |                       | Linux                 | -  SUSE Linux Enterprise Server 11 SP4 64bit (The kernel version is 3.0.101-68-default or 3.0.101-80-default.)                                                                |
      |                       |                       | -  SUSE Linux Enterprise Server 12 64bit (The kernel version is 3.12.51-52.31-default.)                                                                                       |
      |                       |                       | -  SUSE Linux Enterprise Server 12 SP1 64bit (The kernel version is 3.12.67-60.64.24-default.)                                                                                |
      |                       |                       | -  SUSE Linux Enterprise Server 12 SP2 64bit (The kernel version is 4.4.74-92.35.1-default.)                                                                                  |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
