:original_name: evs_01_0001.html

.. _evs_01_0001:

Disk Encryption
===============

What Is Disk Encryption?
------------------------

EVS enables you to encrypt data on newly created disks as required.

It uses the industry-standard XTS-AES-256 cryptographic algorithm and keys to encrypt EVS disks. Keys used to encrypt EVS disks are provided by the Key Management Service (KMS), which is secure and convenient. You do not need to establish and maintain the key management infrastructure. KMS uses the Hardware Security Module (HSM) that complies with FIPS 140-2 level 3 requirements to protect keys. All user keys are protected by the root key in HSM to prevent key exposure.

.. important::

   The encryption attribute of a disk cannot be changed after the disk is created.

Keys Used for EVS Encryption
----------------------------

Keys provided by KMS include a Default Master Key and Customer Master Keys (CMKs).

-  Default Master Key: A key that is automatically created by EVS through KMS and named **evs/default**.

   It cannot be disabled and does not support scheduled deletion.

-  CMKs: Keys created by users. You may use existing CMKs or create new CMKs to encrypt disks. For details, see section "Creating a CMK" in the *Key Management Service User Guide*.

When an encrypted disk is attached, EVS accesses KMS, and KMS sends the data key (DK) to the host memory for use. The disk uses the DK plaintext to encrypt and decrypt disk I/Os. The DK plaintext is only stored in the memory of the host housing the ECS and is not stored persistently on the media. If a CMK is disabled or deleted in KMS, the disk encrypted using this CMK can still use the DK plaintext stored in the host memory. If this disk is later detached, the DK plaintext will be deleted from the memory, and data can no longer be read from or written to the disk. Before you re-attach this encrypted disk, ensure that the CMK is enabled.

If you use a CMK to encrypt disks and this CMK is then disabled or scheduled for deletion, data cannot be read from or written to these disks or may never be restored. See :ref:`Table 1 <evs_01_0001__en-us_topic_0077470126_table15423135384216>` for more information.

.. _evs_01_0001__en-us_topic_0077470126_table15423135384216:

.. table:: **Table 1** Impact of CMK unavailability

   +-----------------------+---------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | CMK Status            | Impact                                                                                            | How to Restore                                                                                                                                                                   |
   +=======================+===================================================================================================+==================================================================================================================================================================================+
   | Disabled              | -  For an encrypted disk already attached:                                                        | Enable the CMK. For details, see "Managing CMKs" > "Enabling One or More CMKs" in the *Key Management Service User Guide*.                                                       |
   |                       |                                                                                                   |                                                                                                                                                                                  |
   |                       |    Reads and writes to the disk are normal. If the disk is detached, it cannot be attached again. |                                                                                                                                                                                  |
   |                       |                                                                                                   |                                                                                                                                                                                  |
   |                       | -  For an encrypted disk not attached:                                                            |                                                                                                                                                                                  |
   |                       |                                                                                                   |                                                                                                                                                                                  |
   |                       |    The disk cannot be attached anymore.                                                           |                                                                                                                                                                                  |
   +-----------------------+---------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Scheduled deletion    |                                                                                                   | Cancel the scheduled deletion for the CMK. For details, see "Managing CMKs" > "Canceling the Scheduled Deletion of One or More CMKs" in the *Key Management Service User Guide*. |
   +-----------------------+---------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Deleted               |                                                                                                   | Data on the disks can never be restored.                                                                                                                                         |
   +-----------------------+---------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Who Can Use the Encryption Function?
------------------------------------

When a user uses the encryption function, the condition varies depending on whether the user is the first one ever in the current region or project to use this function.

-  If the user is the first user, the user needs to follow the prompt to create an agency, which grants EVS KMSAccess permissions to EVS. Then, the user can create and obtain keys to encrypt and decrypt disks.

   .. note::

      The first user must have the EVS KMSAccess permissions to create the agency. If the user does not have the permissions, contact the account administrator to grant the permissions first.

-  If the user is not the first user, the user can use encryption directly.
