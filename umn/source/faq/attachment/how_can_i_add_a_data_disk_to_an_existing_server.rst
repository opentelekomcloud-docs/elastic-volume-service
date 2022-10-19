:original_name: evs_faq_0043.html

.. _evs_faq_0043:

How Can I Add a Data Disk to an Existing Server?
================================================

Data disks can be created during or after the server creation. If you create data disks during the server creation, the system will automatically attach the data disks to the server. If you create data disks after the server creation, you need to attach them manually.

-  On a Windows server:

   -  If a data disk is created along with the server, you need to log in to the server and initialize the disk. The data disk can be viewed after the initialization succeeds.
   -  If a data disk is not created along with the server, you need to create a data disk and attach it to the server. Then, you can log in to the server and initialize the disk. The data disk will be visible after the initialization succeeds.

-  On a Linux server:

   -  If a data disk is created along with the server, you need to log in to the server and initialize the disk. The data disk can be viewed after the initialization succeeds and the disk has been mounted via the **mount** command.
   -  If a data disk is not created along with the server, you need to create a data disk and attach it to the server. Then, you can log in to the server and initialize the disk. The data disk will be visible after the initialization succeeds and the disk has been mounted via the **mount** command.

For details, see :ref:`Introduction to Data Disk Initialization Scenarios and Partition Styles <evs_01_0038>`.
