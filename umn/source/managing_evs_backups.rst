:original_name: evs_01_0110.html

.. _evs_01_0110:

Managing EVS Backups
====================

Scenarios
---------

EVS backups are created using the CBR service. For details, see **Creating a Cloud Disk Backup** in the *Cloud Backup and Recovery User Guide*.

This section describes how to configure a backup policy for disks. With backup policies configured, data on EVS disks can be periodically backed up to improve data security.

a Disk Backup Vault and Configuring a Backup Policy
---------------------------------------------------

#. Log in to the CBR console.

   a. Log in to the management console.
   b. Click |image1| in the upper left corner and select the desired region and project.
   c. Choose **Storage** > **Cloud Backup and Recovery** > **Cloud Disk Backups**.

#. In the upper right corner, click **Create Disk Backup Vault**.

#. (Optional) In the disk list, select the disks you want to back up. After disks are selected, they are added to the list of selected disks.


   .. figure:: /_static/images/en-us_image_0269609232.png
      :alt: **Figure 1** Selecting disks

      **Figure 1** Selecting disks

   .. note::

      -  Only **Available** and **In-use** disks can be selected.
      -  You can associate desired disks with the vault you created later if you skip this step.

#. Specify the vault capacity. This capacity indicates the total size of the disks that you want to associate with this vault. Therefore, specify a vault capacity that is greater than or equal to the total size of the disks you want to back up. The value ranges from the total size of the disks to 10,485,760 in the unit of GiB.

#. Determine whether to configure auto backup.

   -  If you select **Configure**, you must then select an existing backup policy or create a new one. After the vault is created, the system applies this backup policy to the vault, and all disks associated with this vault will be automatically backed up based on this policy.
   -  If you select **Skip**, disks associated with this vault are not automatically backed up.

#. Specify a name for the vault.

   The name can contain 1 to 64 characters including digits, letters, underscores (_), and hyphens (-), for example, **vault-612c**.

   .. note::

      You can use the default name, which is in the format of **vault\_**\ *xxxx*.

#. Click **Next**.

#. Complete the creation as prompted.

#. Go back to the disk backup page. The vault you created is displayed in the list.

   You can associate disks to the new vault or create backups for the disks. For details, see **Vault Management** in the *Cloud Backup and Recovery User Guide*.

.. |image1| image:: /_static/images/en-us_image_0237893718.png
