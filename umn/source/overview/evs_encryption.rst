:original_name: evs_01_0001.html

.. _evs_01_0001:

EVS Encryption
==============

What Is EVS Encryption?
-----------------------

In case your services require encryption for the data stored on EVS disks, EVS provides you with the encryption function. You can encrypt newly created EVS disks.

EVS uses the industry-standard XTS-AES-256 encryption algorithm and keys to encrypt EVS disks. Keys used by encrypted EVS disks are provided by the Key Management Service (KMS), which is secure and convenient. Therefore, you do not need to establish and maintain the key management infrastructure. KMS uses the Hardware Security Module (HSM) that complies with FIPS 140-2 level 3 requirements to protect keys. All user keys are protected by the root key in HSM to prevent key exposure.

.. important::

   The encryption attribute of a disk cannot be changed after the disk is purchased.

   For details about how to create an encrypted disk, see **Getting Started** > **Purchase an EVS Disk** in the *Elastic Volume Service User Guide*.

Keys Used for EVS Encryption
----------------------------

The keys provided by KMS include a Default Master Key and Customer Master Keys (CMKs).

-  Default Master Key: A key that is automatically created by EVS through KMS and named **evs/default**.

   The Default Master Key cannot be disabled and does not support scheduled deletion.

-  CMKs: Keys created by users. You may use existing CMKs or create new CMKs to encrypt disks. For details, see **Management** > **Creating a CMK** in the *Key Management Service User Guide*.

When an encrypted disk is attached, EVS accesses KMS, and KMS sends the data key (DK) to the host memory for use. The disk uses the DK plaintext to encrypt and decrypt disk I/Os. The DK plaintext is only stored in the memory of the host housing the ECS and is not stored persistently on the media. If the CMK is disabled or deleted in KMS, the disk encrypted using this CMK can still use the DK plaintext stored in the host memory. If this disk is later detached, the DK plaintext will be deleted from the memory, and data cannot be read from or written to the disk. Before you re-attach this encrypted disk, ensure that the CMK is enabled.

If you use a CMK to encrypt disks and this CMK is then disabled or scheduled for deletion, data cannot be read from or written to these disks or may never be restored. See :ref:`Table 1 <evs_01_0001__table15423135384216>` for more information.

.. _evs_01_0001__table15423135384216:

.. table:: **Table 1** Impact of CMK unavailability

   +-----------------------+---------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | CMK Status            | Impact                                                                                                                    | How to Restore                                                                                                                                                                       |
   +=======================+===========================================================================================================================+======================================================================================================================================================================================+
   | Disabled              | -  For an encrypted disk already attached:                                                                                | Enable the CMK. For details, see **Managing CMKs** > **Enabling One or More CMKs** in the *Key Management Service User Guide*.                                                       |
   |                       |                                                                                                                           |                                                                                                                                                                                      |
   |                       |    Reads and writes to the disk are normal unless the disk is detached. Once detached, the disk cannot be attached again. |                                                                                                                                                                                      |
   |                       |                                                                                                                           |                                                                                                                                                                                      |
   |                       | -  For an encrypted disk not attached:                                                                                    |                                                                                                                                                                                      |
   |                       |                                                                                                                           |                                                                                                                                                                                      |
   |                       |    The disk cannot be attached anymore.                                                                                   |                                                                                                                                                                                      |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Scheduled deletion    |                                                                                                                           | Cancel the scheduled deletion for the CMK. For details, see **Managing CMKs** > **Canceling the Scheduled Deletion of One or More CMKs** in the *Key Management Service User Guide*. |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Deleted               |                                                                                                                           | Data on the disks can never be restored.                                                                                                                                             |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Who Can Use the Encryption Function?
------------------------------------

-  The security administrator (having Security Administrator permissions) can grant the KMS access rights to EVS for using the encryption function.
-  When a user who does not have the Security Administrator permissions needs to use the encryption function, the condition varies depending on whether the user is the first one ever in the current region or project to use this function.

   -  If the user is the first one ever in the current region or project to use this function, the user must contact a user having the Security Administrator permissions to grant the KMS access rights to EVS. Then, the user can use encryption.
   -  If the user is not the first one ever in the current region or project to use this function, the user can use encryption directly.

From the perspective of a tenant, as long as the KMS access rights have been granted to EVS in a region, all the users in the same region can directly use the encryption function.

If there are multiple projects in the current region, the KMS access rights need to be granted to each project in this region.

Application Scenarios of EVS Encryption
---------------------------------------

:ref:`Figure 1 <evs_01_0001__fig682110438439>` shows the user relationships under regions and projects from the perspective of a tenant. The following example uses region B to describe the two scenarios of using the encryption function.

.. _evs_01_0001__fig682110438439:

.. figure:: /_static/images/en-us_image_0205531351.png
   :alt: **Figure 1** User relationships

   **Figure 1** User relationships

-  If the security administrator uses the encryption function for the first time ever, the operation process is as follows:

   #. Grant the KMS access rights to EVS.

      After the KMS access rights have been granted, the system automatically creates a Default Master Key and names it **evs/default**. You can use the Default Master Key to encrypt EVS disks.

      .. note::

         EVS encryption relies on KMS. When the encryption function is used for the first time ever, the KMS access rights need to be granted to EVS. After the KMS access rights have been granted, all users in this region can use the encryption function, without requiring the KMS access rights to be granted again.

   #. Select a key.

      You can select one of the following keys:

      -  Default Master Key: **evs/default**
      -  CMKs: Existing or newly created CMKs. For details, see **Creating a CMK** in the *Key Management Service User Guide*.

   After the security administrator has used the encryption function, all users in Region B can directly use encryption.

-  If User E (common user) uses the encryption function for the first time ever, the operation process is as follows:

   #. When user E uses encryption, and the system prompts a message indicating that the KMS access rights have not been granted to EVS.
   #. Contact the security administrator to grant the KMS access rights to EVS.

   After the KMS access rights have been granted to EVS, User E as well as all users in Region B can directly use the encryption function and do not need to contact the security administrator to grant the KMS access rights to EVS again.
