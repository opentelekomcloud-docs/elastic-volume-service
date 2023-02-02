:original_name: evs_faq_0091.html

.. _evs_faq_0091:

How Can I Export the Original Data After I Changed My Server OS from Windows to CentOS?
=======================================================================================

Solution:

#. Install the ntfsprogs software to enable Linux to access the NTFS file system.

   **yum install ntfsprogs**

#. View the data disks previously attached to Windows.

   **parted -l**

#. Mount the data disks.

   **mount -t ntfs-3g** *Data disk path Mount point*
