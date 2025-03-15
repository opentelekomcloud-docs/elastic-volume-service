:original_name: evs_02_0015.html

.. _evs_02_0015:

Resource Planning
=================

This topic describes the servers and disks planned for creating a RAID 10 array.

Servers
-------

In this example, one Elastic Cloud Server (ECS) is created, and :ref:`Table 1 <evs_02_0015__table779914155322>` shows the parameter specifications.

.. _evs_02_0015__table779914155322:

.. table:: **Table 1** ECS parameter configurations

   +--------------------------+------------------------------------------------------+
   | Parameter                | Configuration Information                            |
   +==========================+======================================================+
   | Name                     | ecs-raid10                                           |
   +--------------------------+------------------------------------------------------+
   | Image                    | CentOS Strean 9                                      |
   +--------------------------+------------------------------------------------------+
   | Specifications           | General computing, s3.medium.2 (1 vCPU, 2 GiB memory)|
   +--------------------------+------------------------------------------------------+
   | Elastic IP Address (EIP) | 80.\ 158.\ *XX*.\ *XX*                               |
   +--------------------------+------------------------------------------------------+
   | Private IP Address       | 192.168.1.189                                        |
   +--------------------------+------------------------------------------------------+

EVS Disks
---------

Setting up RAID 10 requires at least 4 disks. Therefore, 4 EVS disks are created and attached to the ECS in this example.
