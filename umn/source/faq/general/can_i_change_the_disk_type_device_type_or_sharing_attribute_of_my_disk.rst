:original_name: evs_faq_0045.html

.. _evs_faq_0045:

Can I Change the Disk Type, Device Type, or Sharing Attribute of My Disk?
=========================================================================

The following table describes whether the disk type, device type, sharing, and encryption attributes of a disk can be changed.

.. table:: **Table 1** EVS disk change description

   +-----------------------+-----------------------+-------------------------------------------------------------------+
   | Attribute             | Allow Change          | Change Direction                                                  |
   +=======================+=======================+===================================================================+
   | Disk type             | Yes                   | For details, see :ref:`Changing the EVS Disk Type <evs_01_0062>`. |
   +-----------------------+-----------------------+-------------------------------------------------------------------+
   | Sharing               | No                    | -  From shared to non-shared                                      |
   |                       |                       | -  From non-shared to shared                                      |
   +-----------------------+-----------------------+-------------------------------------------------------------------+
   | Device type           | No                    | -  From SCSI to VBD                                               |
   |                       |                       | -  From VBD to SCSI                                               |
   +-----------------------+-----------------------+-------------------------------------------------------------------+
   | Encryption            | No                    | -  From non-encrypted to encrypted                                |
   |                       |                       | -  From encrypted to non-encrypted                                |
   +-----------------------+-----------------------+-------------------------------------------------------------------+

**However, you can:**

#. Create a backup for the disk.


   .. figure:: /_static/images/en-us_image_0000001622372417.png
      :alt: **Figure 1** Create Backup

      **Figure 1** Create Backup

#. Create a new disk from this backup. During the creation, select a new disk type and configure advanced settings (sharing, SCSI, and encryption) based on your service requirements.


   .. figure:: /_static/images/en-us_image_0000001572095150.png
      :alt: **Figure 2** Create from backup

      **Figure 2** Create from backup
