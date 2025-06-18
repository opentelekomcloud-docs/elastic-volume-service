:original_name: evs_01_0009.html

.. _evs_01_0009:

Managing Encrypted EVS Disks
============================

What Is EVS Disk Encryption?
----------------------------

EVS enables you to encrypt data on newly created disks as required.

It uses the industry-standard XTS-AES-256 cryptographic algorithm and keys to encrypt EVS disks. Keys used to encrypt EVS disks are provided by the Key Management Service (KMS), which is secure and convenient. You do not need to establish and maintain the key management infrastructure. KMS uses the Hardware Security Module (HSM) that complies with FIPS 140-2 level 3 requirements to protect keys. All user keys are protected by the root key in HSM to prevent key exposure.

.. important::

   The encryption attribute of a disk cannot be changed after the disk is created.

   For details about how to create an encrypted disk, see :ref:`Creating an EVS Disk <en-us_topic_0021738346>`.

.. _evs_01_0009__en-us_topic_0077504312_section17331463223115:

Keys Used for EVS Encryption
----------------------------

Keys provided by KMS include a Default Master Key and Customer Master Keys (CMKs).

-  Default Master Key: A key that is automatically created by EVS through KMS and named **evs/default**.

   It cannot be disabled and does not support scheduled deletion.

-  CMKs: Keys created by users. You may use existing CMKs or create new CMKs to encrypt disks. For details, see section "Creating a CMK" in the *Key Management Service User Guide*.

When an encrypted disk is attached, EVS accesses KMS, and KMS sends the data key (DK) to the host memory for use. The disk uses the DK plaintext to encrypt and decrypt disk I/Os. The DK plaintext is only stored in the memory of the host housing the ECS and is not stored persistently on the media. If a CMK is disabled or deleted in KMS, the disk encrypted using this CMK can still use the DK plaintext stored in the host memory. If this disk is later detached, the DK plaintext will be deleted from the memory, and data can no longer be read from or written to the disk. Before you re-attach this encrypted disk, ensure that the CMK is enabled.

If you use a CMK to encrypt disks and this CMK is then disabled or scheduled for deletion, data cannot be read from or written to these disks or may never be restored. See :ref:`Table 1 <evs_01_0009__en-us_topic_0077504312_table15423135384216>` for more information.

.. _evs_01_0009__en-us_topic_0077504312_table15423135384216:

.. table:: **Table 1** Impact of CMK unavailability

   +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | CMK Status            | Impact                                                                                                                                    | How to Restore                                                                                                                                                                   |
   +=======================+===========================================================================================================================================+==================================================================================================================================================================================+
   | Disabled              | -  For an encrypted disk already attached: Reads and writes to the disk are normal. If the disk is detached, it cannot be attached again. | Enable the CMK. For details, see "Managing CMKs" > "Enabling One or More CMKs" in the *Key Management Service User Guide*.                                                       |
   |                       | -  For an encrypted disk not attached: The disk cannot be attached anymore.                                                               |                                                                                                                                                                                  |
   +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Scheduled deletion    |                                                                                                                                           | Cancel the scheduled deletion for the CMK. For details, see "Managing CMKs" > "Canceling the Scheduled Deletion of One or More CMKs" in the *Key Management Service User Guide*. |
   +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Deleted               |                                                                                                                                           | Data on the disks can never be restored.                                                                                                                                         |
   +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Encryption Scenarios
--------------------

-  **System disk encryption**

   System disks are created along with servers and cannot be created separately. So whether a system disk is encrypted or not depends on the image you select when creating the server.

   .. table:: **Table 2** Encryption relationship between images and system disks

      +---------------------------------------+---------------------------------------+----------------------------------------------------------------------------------------------------------------------------+
      | Creating Server Using Encrypted Image | Whether System Disk Will Be Encrypted | Description                                                                                                                |
      +=======================================+=======================================+============================================================================================================================+
      | Yes                                   | Yes                                   | For details, see **Managing Private Images** > **Creating Encrypted Images** in the *Image Management Service User Guide*. |
      +---------------------------------------+---------------------------------------+----------------------------------------------------------------------------------------------------------------------------+
      | No                                    | No                                    | ``-``                                                                                                                      |
      +---------------------------------------+---------------------------------------+----------------------------------------------------------------------------------------------------------------------------+

-  **Data disk encryption**

   Data disks can be created along with servers or separately. Whether data disks are encrypted depends on their data sources. See the following table for details.

   .. table:: **Table 3** Encryption relationship between backups, snapshots, images, and data disks

      +-----------------+------------------------------------------------+-------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Created On      | Method of Creation                             | Whether Data Disk Will Be Encrypted | Description                                                                                                                                                                                                                                |
      +=================+================================================+=====================================+============================================================================================================================================================================================================================================+
      | The ECS console | Created together with the server               | Yes/No                              | When a data disk is created together with a server, you can choose to encrypt the disk or not. For details, see **Getting Started** > **Creating an ECS** > **Step 1: Configure Basic Settings** in the *Elastic Cloud Server User Guide*. |
      +-----------------+------------------------------------------------+-------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | The EVS console | No data source selected                        | Yes/No                              | When an empty disk is created, you can choose whether to encrypt the disk or not. The encryption attribute of the disk cannot be changed after the disk has been created.                                                                  |
      +-----------------+------------------------------------------------+-------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      |                 | Creating from a backup                         | Yes/No                              | -  When a disk is created from a backup, you can choose whether to encrypt the disk or not. The encryption attributes of the disk and backup do not need to be the same.                                                                   |
      |                 |                                                |                                     | -  When you create a backup for a system or data disk, the encryption attribute of the backup will be the same as that of the disk.                                                                                                        |
      +-----------------+------------------------------------------------+-------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      |                 | Creating from a snapshot                       | Yes                                 | A snapshot created from an encrypted disk is also encrypted.                                                                                                                                                                               |
      |                 |                                                |                                     |                                                                                                                                                                                                                                            |
      |                 | (The snapshot's source disk is encrypted.)     |                                     |                                                                                                                                                                                                                                            |
      +-----------------+------------------------------------------------+-------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      |                 | Creating from a snapshot                       | No                                  | A snapshot created from a non-encrypted disk is not encrypted.                                                                                                                                                                             |
      |                 |                                                |                                     |                                                                                                                                                                                                                                            |
      |                 | (The snapshot's source disk is not encrypted.) |                                     |                                                                                                                                                                                                                                            |
      +-----------------+------------------------------------------------+-------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      |                 | Creating from an image                         | Yes                                 | ``-``                                                                                                                                                                                                                                      |
      |                 |                                                |                                     |                                                                                                                                                                                                                                            |
      |                 | (The image's source disk is encrypted.)        |                                     |                                                                                                                                                                                                                                            |
      +-----------------+------------------------------------------------+-------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      |                 | Creating from an image                         | No                                  | ``-``                                                                                                                                                                                                                                      |
      |                 |                                                |                                     |                                                                                                                                                                                                                                            |
      |                 | (The image's source disk is not encrypted.)    |                                     |                                                                                                                                                                                                                                            |
      +-----------------+------------------------------------------------+-------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Notes and Constraints
---------------------

.. table:: **Table 4** Constraints on disk encryption

   +--------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Item                                 | Description                                                                                                                                                                                                       |
   +======================================+===================================================================================================================================================================================================================+
   | Types of disks supporting encryption | All disk types                                                                                                                                                                                                    |
   +--------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Constraints on encrypted disks       | The encryption attribute of a disk cannot be changed after the disk is created, meaning that:                                                                                                                     |
   |                                      |                                                                                                                                                                                                                   |
   |                                      | -  An encrypted disk cannot be changed to a non-encrypted disk.                                                                                                                                                   |
   |                                      | -  A non-encrypted disk cannot be changed to an encrypted disk.                                                                                                                                                   |
   +--------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Constraints on user permissions      | When a user uses the encryption function, the condition varies depending on whether the user is the first one ever in the current region or project to use this function.                                         |
   |                                      |                                                                                                                                                                                                                   |
   |                                      | -  If the user is the first user, the user needs to follow the prompt to create an agency, which grants EVS KMSAccess permissions to EVS. Then, the user can create and obtain keys to encrypt and decrypt disks. |
   |                                      |                                                                                                                                                                                                                   |
   |                                      |    .. note::                                                                                                                                                                                                      |
   |                                      |                                                                                                                                                                                                                   |
   |                                      |       The first user must have the EVS KMSAccess permissions to create the agency. If the user does not have the permissions, contact the account administrator to grant the permissions first.                   |
   |                                      |                                                                                                                                                                                                                   |
   |                                      | -  If the user is not the first user, the user can use encryption directly.                                                                                                                                       |
   +--------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Constraints on encrypted images      | -  Encrypted images cannot be replicated across regions.                                                                                                                                                          |
   |                                      | -  Encrypted images cannot be changed to non-encrypted images.                                                                                                                                                    |
   |                                      | -  Encrypted images cannot be exported.                                                                                                                                                                           |
   +--------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Creating an Encrypted EVS Disk
------------------------------

Before you use the encryption function, KMS access rights need to be granted to EVS. If you have the Security Administrator permissions, grant the KMS access rights to EVS directly. If you do not have this permission, contact a user with the security administrator permissions to grant KMS access rights to EVS and then select the encryption option to create an encrypted disk.

For details about how to create an encrypted disk, see :ref:`Creating an EVS Disk <en-us_topic_0021738346>`.

Detaching an Encrypted EVS Disk
-------------------------------

Before you detach a disk encrypted by a CMK, check whether the CMK is disabled or scheduled for deletion.

-  If the CMK is available, the disk can be detached and re-attached, and data on the disk will not be lost.
-  If the CMK is unavailable, the disk can still be used, but there is no guarantee for how long it will be usable. If the disk is detached, it will be impossible to re-attach it later. In this case, do not detach the disk without a working CMK.

The restoration method varies depending on the CMK status. For details, see :ref:`Keys Used for EVS Encryption <evs_01_0009__en-us_topic_0077504312_section17331463223115>`.

For details about how to detach an encrypted disk, see :ref:`Detaching an EVS Disk <evs_01_0003>`.
