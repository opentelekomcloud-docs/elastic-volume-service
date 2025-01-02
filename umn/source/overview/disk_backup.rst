:original_name: evs_01_0021.html

.. _evs_01_0021:

Disk Backup
===========

What Is Disk Backup?
--------------------

Cloud Disk Backup provided by Cloud Backup and Recovery (CBR) allows you to create backups for your EVS disks while servers are running. If data loss or damage occurred due to virus invasions, accidental deletions, or software/hardware faults, you can use backups to restore data, guaranteeing your data integrity and security.

For more information, see the *Cloud Backup and Recovery User Guide*.

CBR Architecture
----------------

CBR involves backups, vaults, and policies.

**Backup**

A backup is a copy of a particular chunk of data and is usually stored elsewhere so that it may be used to restore the original data in the event of data loss.

There are the following types of backups:

-  Cloud disk backup: provides snapshot-based backups for EVS disks.
-  Cloud server backup: uses the consistency snapshot technology to protect data for ECSs.
-  SFS Turbo backup: backs up data of SFS Turbo file systems.

**Vault**

CBR stores backups in vaults. Before creating a backup, you need to create at least one vault and associate the resources you want to back up with the vaults. Then the resources can be backed up to the associated vaults.

Different types of resources must be backed up to different types of vaults. For example, cloud servers must be backed up to server backup vaults, not disk backup vaults or any other types of vaults.

**Policy**

There are backup policies and replication policies.

-  A backup policy defines when you want to take a backup and for how long you would retain each backup.
-  A replication policy defines when you want to replicate from backup vaults and for how long you would retain each replica. Backup replicas are stored in replication vaults.


.. figure:: /_static/images/en-us_image_0277693887.png
   :alt: **Figure 1** CBR architecture

   **Figure 1** CBR architecture

Who Can Use the Backup Function?
--------------------------------

Only users with the CBR FullAccess permissions can use the cloud disk backup function. If the user does not have the permissions, contact the account administrator to grant the permissions first.

Application Scenarios
---------------------

Create and apply backup policies to schedule periodic backups for your EVS disks. You can use the backup data to create new EVS disks or restore to source disks.
