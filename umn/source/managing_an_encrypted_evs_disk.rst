:original_name: evs_01_0009.html

.. _evs_01_0009:

Managing an Encrypted EVS Disk
==============================

Relationships Between Encrypted Disks, Backups and Snapshots
------------------------------------------------------------

The encryption function can be used to encrypt system disks, data disks, backups and snapshots. The details are as follows:

-  System disk encryption relates to the image that is used to create the server.

   -  If an encrypted image is used to create the server, encryption is enabled for the system disk by default, and the system disk and image share the same encryption method. For details, see **Managing Private Images** > **Encrypting Images** in the *Image Management Service User Guide*.
   -  If a non-encrypted image is used to create the server, determine whether to encrypt the system disk during the server creation. For details, see **Getting Started** > **Creating an ECS** > **Step 1: Configure Basic Settings** in the *Elastic Cloud Server User Guide*.

-  If an empty disk is created, you can determine whether to encrypt the disk or not. The encryption attribute of the disk cannot be changed after the disk has been created.
-  If a disk is created from a snapshot, the encryption attribute of the disk will be the same as that of the snapshot's source disk.
-  If a disk is created from a backup, the encryption attribute of the disk does not need to be the same as that of the backup.
-  If a snapshot is created for a disk, the encryption attribute of the snapshot is the same as that of the disk.

Creating an Encrypted EVS Disk
------------------------------

Before you use the disk encryption function, KMS access rights need to be granted to EVS. If you have the Security Administrator rights, grant the KMS access rights to EVS directly. If you do not have this permission, contact a user with the security administrator rights to grant KMS access rights to EVS, then repeat the preceding operations.

For details about how to create an encrypted disk, see :ref:`Create an EVS Disk <en-us_topic_0021738346>`.

Detaching an Encrypted EVS Disk
-------------------------------

Before you detach an EVS disk encrypted by a CMK, check whether the CMK is disabled or scheduled for deletion. If the CMK is unavailable, the disk can still be used, but there is no guarantee how long it will be usable. If the disk is detached, it will not be possible to re-attach it later. In this case, do not detach the disk without a working CMK.

The restoration method varies depending on the current CMK status. For details, see :ref:`EVS Disk Encryption <evs_01_0001>`.

If the CMK is available, the disk can be detached and re-attached, and data on the disk will not be lost.

For details about how to detach an encrypted disk, see :ref:`Detaching a Data Disk <evs_01_0004>`.
