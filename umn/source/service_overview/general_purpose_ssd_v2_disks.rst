:original_name: evs_01_1137.html

.. _evs_01_1137:

General Purpose SSD V2 Disks
============================

General Purpose SSD V2 is a next-generation General Purpose SSD disk type. You can buy General Purpose SSD V2 disks of a given capacity with the IOPS and throughput tailored to your workloads. The disk capacity and performance are decoupled. This section describes the performance, configuration, and billing of General Purpose SSD V2 disks.

Performance
-----------

.. table:: **Table 1** General Purpose SSD V2 performance

   +--------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter                                                                                                                                        | General Purpose SSD V2                                                                                                  |
   +==================================================================================================================================================+=========================================================================================================================+
   | Max. capacity                                                                                                                                    | -  System disk: 1,024 GiB                                                                                               |
   |                                                                                                                                                  | -  Data disk: 32,768 GiB                                                                                                |
   +--------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+
   | Single-queue access latency                                                                                                                      | 1 ms                                                                                                                    |
   +--------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+
   | Burst IOPS limit                                                                                                                                 | N/A                                                                                                                     |
   +--------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+
   | Disk IOPS calculation formula                                                                                                                    | You configure an IOPS ranging from 3,000 to 128,000. This IOPS must also not exceed 500 times the capacity.             |
   +--------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+
   | Disk throughput calculation formula                                                                                                              | You configure a throughput ranging from 125 to 1,000 MiB/s. This throughput must also not exceed the IOPS divided by 4. |
   +--------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+
   | API name                                                                                                                                         | GPSSD2                                                                                                                  |
   |                                                                                                                                                  |                                                                                                                         |
   | .. note::                                                                                                                                        |                                                                                                                         |
   |                                                                                                                                                  |                                                                                                                         |
   |    This API name is the value of the **volume_type** parameter in the EVS API. It does not represent the type of the underlying hardware device. |                                                                                                                         |
   +--------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+
   | Typical use cases                                                                                                                                | Mainstream high-performance, low-latency interactive applications                                                       |
   |                                                                                                                                                  |                                                                                                                         |
   |                                                                                                                                                  | -  Enterprise OA and virtual desktops                                                                                   |
   |                                                                                                                                                  | -  Large-scale development and test environments                                                                        |
   |                                                                                                                                                  | -  Transcoding services                                                                                                 |
   |                                                                                                                                                  | -  System disks                                                                                                         |
   |                                                                                                                                                  | -  Medium- and large-sized databases (SQL Server, Oracle, NoSQL, and PostgreSQL)                                        |
   +--------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------+

Configuration
-------------

#. Go to the page for creating EVS disks.
#. Configure the disk parameters.

   -  Choose the **General Purpose SSD V2** type and enter a desired disk size.

   -  Configure a desired IOPS.

   -  Configure a desired throughput.

   -  Configure other parameters by referring to :ref:`Creating an EVS Disk <en-us_topic_0021738346>`.

      |image1|

#. After the disk is created, view it in the disk list.

.. note::

   If you do not have a clear throughput:IOPS ratio in mind, you are advised to use the ratio of 2:100 (with a throughput unit of 1 MiB/s and an IOPS unit of 100). For example, if your planned throughput is 200 MiB/s, configure 10,000 for the IOPS.

   If the preconfigured IOPS or throughput cannot meet your service requirement or is way more than what your need, you can adjust them at any time.

.. |image1| image:: /_static/images/en-us_image_0000002301560498.png
