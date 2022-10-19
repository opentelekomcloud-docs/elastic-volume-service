:original_name: evs_faq_0042.html

.. _evs_faq_0042:

Do I Need to Restart the Server After Expanding the Disk Capacity?
==================================================================

An EVS disk can be expanded either in the Available or In-use state. Expanding the disk capacity on the management console enlarges the disk capacity, but you still need to log in to the server and extend the disk partitions and file systems to make that additional space usable. You may need to restart the server during the partition and file system extension. The details are as follows:

-  After expanding an In-use disk on the management console, log in to the server and view the disk capacity.

   -  If the additional space can be viewed, you can extend the partition and file system and a restart is not required.
   -  If the additional space cannot be viewed, the server OS may not be included in the compatibility list. In this case, you should stop and then start the server (do not restart the server). When the additional space can be viewed, extend the partition and file system.

-  After expanding an Available disk on the management console, attach the disk to the server and extend the partition and file system on the server. In this case, a server restart is not required.
