:original_name: evs_01_0110.html

.. _evs_01_0110:

Managing EVS Disk Backups
=========================

Scenarios
---------

EVS disk backups are created using the CBR service. For details, see section "Creating a Cloud Disk Backup" in the *Cloud Backup and Recovery User Guide*.

You can configure a backup policy for disks. With backup policies configured, data on EVS disks can be periodically backed up to improve data security.

Notes and Constraints
---------------------

-  Backups can be created only when the disks are in the **Available** or **In-use** state.
-  Only users with the CBR FullAccess permissions can use the cloud disk backup function. If the user does not have the permissions, contact the account administrator to grant the permissions first.

a Disk Backup Vault and Applying a Backup Policy
------------------------------------------------

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
      -  You can also associate disks with the vault you are creating later if you skip this step.

#. Specify a vault capacity ranging from the total sizes of disks to 10,485,760 GiB.

#. Configure auto backup.

   -  If you select **Configure**, you must then select an existing backup policy or create a new policy. After the vault is created, CBR will apply the policy to this vault, and all disks associated with this vault will be automatically backed up based on this policy.
   -  If you select **Skip**, disks associated with this vault are not automatically backed up.

#. Specify a name for the vault.

   The name can contain 1 to 64 characters including digits, letters, underscores (_), and hyphens (-), for example, **vault-612c**.

   .. note::

      You can use the default name, which is in the format of **vault\_**\ *xxxx*.

#. Click **Next**.

#. Complete the creation as prompted.

#. Go back to the disk backup page and view the created vault in the vault list.

   You can associate disks to the new vault or create backups for the disks. For details, see section "Vault Management" in the *Cloud Backup and Recovery User Guide*.

.. |image1| image:: /_static/images/en-us_image_0237893718.png
