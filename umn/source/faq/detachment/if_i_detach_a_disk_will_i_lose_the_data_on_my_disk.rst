:original_name: evs_faq_0012.html

.. _evs_faq_0012:

If I Detach a Disk Will I Lose the Data on My Disk?
===================================================

It depends on if the disk is encrypted or not.

-  Encrypted

   -  CMK is disabled or scheduled for deletion.

      Before you detach an EVS disk encrypted by a CMK, check whether the CMK is disabled or scheduled for deletion. If the CMK is unavailable, the disk can still be used, but there is no guarantee how long it will be usable. If the disk is detached, it will not be possible to re-attach it later. In this case, do not detach the disk without a working CMK.

      The restoration method varies depending on the CMK status. For details, see :ref:`EVS Disk Encryption <evs_01_0001>`.

   -  CMK is available.

      If the CMK is available, the disk can be detached and re-attached, and data on the disk will not be lost.

      To ensure your data safety, you are advised to follow the instructions described in :ref:`Disk detachment process <evs_faq_0012__section1567714137557>`.

-  Non-encrypted

   Data on a disk will not be lost after the disk is detached, and the disk can be re-attached later if needed.

   To ensure your data safety, you are advised to follow the instructions described in :ref:`Disk detachment process <evs_faq_0012__section1567714137557>`.

.. _evs_faq_0012__section1567714137557:

Disk detachment process
-----------------------

-  For disks not supporting online detachment:

   #. Stop the server where the disk was attached.
   #. After the server has stopped, detach the disk.

-  For disks supporting online detachment:

   Detach the disk from a running ECS. For details, see **Management** > **Detaching an EVS Disk from a Running ECS** in the *Elastic Cloud Server User Guide*.
