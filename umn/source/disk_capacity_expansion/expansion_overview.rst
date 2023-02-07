:original_name: evs_01_0006.html

.. _evs_01_0006:

Expansion Overview
==================

What Is Capacity Expansion?
---------------------------

If the capacity of an existing disk is insufficient, you can expand the disk capacity to increase the storage space.

Both system disks and data disks can be expanded. Disk capacity can be expanded only, but cannot be reduced.

How to Expand the Disk Capacity?
--------------------------------

A capacity expansion operation includes the following steps:

#. :ref:`Expand the disk capacity on the management console. <evs_01_0006__section87622024418>`
#. :ref:`Log in to the server and extend the disk partition and file system. <evs_01_0006__section487311389414>`


.. figure:: /_static/images/en-us_image_0228748662.png
   :alt: **Figure 1** Capacity expansion procedure

   **Figure 1** Capacity expansion procedure

.. _evs_01_0006__section87622024418:

Expand the Disk Capacity on the Management Console
--------------------------------------------------

Choose a proper expansion method based on the disk status.

-  For an In-use disk:

   The disk has been attached to a server. Check whether the disk can be expanded in the In-use state by referring to :ref:`Constraints <evs_01_0007__section158147122515>`.

   -  If yes, expand the disk capacity according to :ref:`Expanding Capacity for an In-use EVS Disk <evs_01_0007>`.
   -  If no, detach the disk. Then, expand the disk capacity according to :ref:`Expanding Capacity for an Available EVS Disk <evs_01_0008>`.

-  For an Available disk:

   The disk has not been attached to any server and can be directly expanded by referring to :ref:`Expanding Capacity for an Available EVS Disk <evs_01_0008>`.

   A shared disk can be expanded only when its status is **Available**.

.. _evs_01_0006__section487311389414:

Log In to the Server and Extend the Disk Partition and File System
------------------------------------------------------------------

After the disk has been expanded on the management console, only the disk storage capacity is enlarged, but its additional space cannot be used directly. You must log in to the server and extend the disk partition and file system. For details, see :ref:`Table 1 <evs_01_0006__table458383431811>`.

.. _evs_01_0006__table458383431811:

.. table:: **Table 1** Extending the disk partition and file system

   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Capacity After Expansion          | Extend Disk Partition and File System                                                                                                                                                                                                                                                                                                                                                                                |
   +===================================+======================================================================================================================================================================================================================================================================================================================================================================================================================+
   | Disk capacity <= 2 TiB            | -  Windows: :ref:`Extending Disk Partitions and File Systems (Windows Server 2008) <en-us_topic_0017616396>`                                                                                                                                                                                                                                                                                                         |
   |                                   | -  Linux: :ref:`Partition and File System Extension Preparations (Linux) <evs_01_0035>`                                                                                                                                                                                                                                                                                                                              |
   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Disk capacity > 2 TiB             | -  GPT partition style: :ref:`Extending Disk Partitions and File Systems (Windows Server 2008) <en-us_topic_0017616396>` or :ref:`Partition and File System Extension Preparations (Linux) <evs_01_0035>`                                                                                                                                                                                                            |
   |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                      |
   |                                   | -  MBR partition style: Not supported                                                                                                                                                                                                                                                                                                                                                                                |
   |                                   |                                                                                                                                                                                                                                                                                                                                                                                                                      |
   |                                   |    The maximum disk capacity that MBR supports is 2 TiB, and the disk space exceeding 2 TiB cannot be used. If your disk uses MBR and you need to expand the disk capacity to over 2 TiB, change the partition style from MBR to GPT. Ensure that the disk data has been backed up before changing the partition style because services will be interrupted and data on the disk will be deleted during this change. |
   +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Related Operations
------------------

For more expansion FAQs, see `Capacity Expansion <https://docs.otc.t-systems.com/en-us/usermanual/evs/evs_01_0077.html>`__.
