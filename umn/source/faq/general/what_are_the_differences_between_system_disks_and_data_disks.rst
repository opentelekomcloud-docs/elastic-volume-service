:original_name: evs_faq_0084.html

.. _evs_faq_0084:

What Are the Differences Between System Disks and Data Disks?
=============================================================

-  A system disk runs the server OS. It is like drive C in a PC.

   When a server is created, a system disk is automatically created and attached. You cannot create a system disk separately. The maximum size of a system disk is 1,024 GiB.

-  Data disks store the server data. They are like drive D, drive E, and drive F in a PC.

   Data disks can be created during or after the server creation. If you create data disks during the server creation, the system will automatically attach the data disks to the server. If you create data disks after the server creation, you need to manually attach the data disks. The maximum size of a data disk is 32,768 GiB.

If one system disk already meets your business needs, you do not need to create data disks. As your business grows, you can create data disks when needed.

If the disk paths in your service systems cannot be changed or are difficult to change, you are advised to create data disks according to your system planning.
