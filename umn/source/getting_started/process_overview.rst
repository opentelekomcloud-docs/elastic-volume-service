:original_name: evs_01_0057.html

.. _evs_01_0057:

Process Overview
================

:ref:`Figure 1 <evs_01_0057__evs_01_0120_fig609407314853>` shows the EVS process overview.

.. _evs_01_0057__evs_01_0120_fig609407314853:

.. figure:: /_static/images/en-us_image_0129867556.png
   :alt: **Figure 1** Process overview

   **Figure 1** Process overview

EVS disks can be attached to servers and be used as system disks or data disks. For details, see :ref:`Table 1 <evs_01_0057__table83721247165012>`.

.. _evs_01_0057__table83721247165012:

.. table:: **Table 1** Method of creation

   +-----------------------+-------------------------------------------------------------------------------+----------------------------------------------------------------------------+
   | Disk                  | Description                                                                   | Method                                                                     |
   +=======================+===============================================================================+============================================================================+
   | System disk           | System disks are created along with servers and cannot be created separately. | -  See section "Creating an ECS" in the *Elastic Cloud Server User Guide*. |
   |                       |                                                                               | -  See section "Creating a BMS" in the *Bare Metal Server User Guide*.     |
   +-----------------------+-------------------------------------------------------------------------------+----------------------------------------------------------------------------+
   | Data disk             | Data disks can be created along with servers or separately.                   | -  See section "Creating an ECS" in the *Elastic Cloud Server User Guide*. |
   |                       |                                                                               | -  See section "Creating a BMS" in the *Bare Metal Server User Guide*.     |
   |                       |                                                                               | -  :ref:`Create an EVS Disk <en-us_topic_0021738346>`                      |
   +-----------------------+-------------------------------------------------------------------------------+----------------------------------------------------------------------------+

:ref:`Figure 2 <evs_01_0057__fig246782441513>` shows how to purchase a data disk separately.

.. _evs_01_0057__fig246782441513:

.. figure:: /_static/images/en-us_image_0000001487224722.png
   :alt: **Figure 2** Process overview

   **Figure 2** Process overview

#. **Preparations**: Register an account on the console and obtain the permissions required to create servers and disks.
#. **Create a disk.** Configure the disk parameters, including the disk type, size, name, and other information. For details, see :ref:`Create an EVS Disk <en-us_topic_0021738346>`.
#. **Attach the data disk.** Attach the separately created disk to a server. For details, see the following sections:

   -  :ref:`Attaching a Non-Shared Disk <evs_01_0036>`
   -  :ref:`Attaching a Shared Disk <evs_01_0037>`

#. **Initialize the data disk.** Log in to the server and initialize the data disk before using it. For details about how to initialize the disk, see the following sections:

   -  :ref:`Introduction to Data Disk Initialization Scenarios and Partition Styles <evs_01_0038>`
   -  Windows

      -  :ref:`Initializing a Windows Data Disk (Windows Server 2008) <evs_01_0108>`
      -  :ref:`Initializing a Windows Data Disk (Windows Server 2019) <evs_01_0045>`

   -  Linux

      -  :ref:`Initializing a Linux Data Disk (fdisk) <evs_01_0033>`
      -  :ref:`Initializing a Linux Data Disk (parted) <evs_01_0034>`
