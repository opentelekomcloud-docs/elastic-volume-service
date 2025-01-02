:original_name: evs_faq_0028.html

.. _evs_faq_0028:

Do I Need to Detach an EVS Disk Before Expanding Its Capacity?
==============================================================

An expansion consists of two phases:

#. Expand the disk capacity on the management console.

   -  A shared, in-use disk cannot be expanded. You must detach the shared disk from all its servers and then expand its capacity.
   -  A non-shared, in-use disk can be expanded, and you can leave the disk attached during expansion as long as the following conditions are met:

      -  The disk's server is in the **Running** or **Stopped** state.
      -  The disk's server OS supports the expansion of In-use disks.

         .. note::

            Only some server OSs support capacity expansion of In-use disks. For details, see :ref:`Expanding Capacity for an In-use EVS Disk <evs_01_0007>`.

#. Log in to the server and create a new partition or allocate the additional space to one that is already there.

   The unmount operation is not required, either for Windows or Linux.
