:original_name: evs_01_0057.html

.. _evs_01_0057:

Creating and Using an EVS Disk
==============================

:ref:`Figure 1 <evs_01_0057__en-us_topic_0000001955729926_en-us_topic_0129833436_en-us_topic_0044524685_fig609407314853>` shows the process for using EVS.

.. _evs_01_0057__en-us_topic_0000001955729926_en-us_topic_0129833436_en-us_topic_0044524685_fig609407314853:

.. figure:: /_static/images/en-us_image_0000002051547313.png
   :alt: **Figure 1** Process of using EVS

   **Figure 1** Process of using EVS

EVS disks can be attached to servers to be used as system disks or data disks. For details, see :ref:`Table 1 <evs_01_0057__en-us_topic_0000001955729926_en-us_topic_0129833436_table83721247165012>`.

.. _evs_01_0057__en-us_topic_0000001955729926_en-us_topic_0129833436_table83721247165012:

.. table:: **Table 1** Method for creating disks

   +-----------------------+------------------------------------------------------------------------------------+----------------------------------------------------------------------------+
   | Function              | Description                                                                        | Method                                                                     |
   +=======================+====================================================================================+============================================================================+
   | System disk           | System disks are created together with servers. You cannot create them separately. | -  See section "Creating an ECS" in the *Elastic Cloud Server User Guide*. |
   |                       |                                                                                    | -  See section "Creating a BMS" in the *Bare Metal Server User Guide*.     |
   +-----------------------+------------------------------------------------------------------------------------+----------------------------------------------------------------------------+
   | Data disk             | You can create data disks together with servers or separately.                     | -  See section "Creating an ECS" in the *Elastic Cloud Server User Guide*. |
   |                       |                                                                                    | -  See section "Creating a BMS" in the *Bare Metal Server User Guide*.     |
   |                       |                                                                                    | -  :ref:`Creating an EVS Disk <en-us_topic_0021738346>`                    |
   +-----------------------+------------------------------------------------------------------------------------+----------------------------------------------------------------------------+

:ref:`Figure 2 <evs_01_0057__en-us_topic_0000001955729926_en-us_topic_0129833436_fig246782441513>` shows the process of creating and using a data disk.

.. _evs_01_0057__en-us_topic_0000001955729926_en-us_topic_0129833436_fig246782441513:

.. figure:: /_static/images/en-us_image_0000002015229526.png
   :alt: **Figure 2** Process of using EVS

   **Figure 2** Process of using EVS

#. **Make preparations**: Register an account on the console and obtain permissions required for creating ECSs and EVS disks.
#. **Create an EVS disk**: Configure the disk parameters, including the disk type, capacity, name, and other information by referring to :ref:`Creating an EVS Disk <en-us_topic_0021738346>`.
#. **Attach the data disk.** Attach the separately created disk to an ECS. For details, see the following sections:

   -  :ref:`Attaching a Non-Shared Disk <evs_01_0036>`
   -  :ref:`Attaching a Shared Disk <evs_01_0037>`

#. **Initialize the data disk**: After the data disk is attached, log in to the ECS and initialize the disk before using it. For details about the initialization scenarios and how to initialize the disk, see the following sections:

   -  :ref:`Introduction to Data Disk Initialization Scenarios and Partition Styles <evs_01_0038>`
   -  Windows

      -  :ref:`Initializing a Windows Data Disk (Windows Server 2008) <evs_01_0108>`
      -  :ref:`Initializing a Windows Data Disk (Windows Server 2019) <evs_01_0045>`

   -  Linux

      -  :ref:`Initializing a Linux Data Disk (fdisk) <evs_01_0033>`
      -  :ref:`Initializing a Linux Data Disk (parted) <evs_01_0034>`
