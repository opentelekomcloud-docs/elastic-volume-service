:original_name: en-us_topic_0014580744.html

.. _en-us_topic_0014580744:

Disk Types and Performance
==========================

EVS disks are classified based on the disk I/O performance. EVS disks differ in performance and price. Choose the disk type most appropriate for your applications.

Application Scenarios
---------------------

-  Common I/O: EVS disks of this type deliver a maximum of 1,000 IOPS. This disk type is suitable for application scenarios that require large capacity, a medium read/write speed, and fewer transactions, such as enterprise office applications and small-scale testing.
-  High I/O: EVS disks of this type deliver a maximum of 3,000 IOPS and a minimum of 6 ms read/write latency. This disk type is designed to meet the needs of mainstream high-performance, high-reliability application scenarios, such as enterprise applications, large-scale development and testing, and web server logs.
-  Ultra-high I/O: EVS disks of this type deliver a maximum of 20,000 IOPS and a minimum of 1 ms read/write latency. This disk type is excellent for ultra-high I/O, ultra-high bandwidth, and read/write-intensive application scenarios, such as distributed file systems in HPC scenarios or NoSQL/relational databases in I/O-intensive scenarios.
-  High I/O (Performance optimized I): EVS disks of this type deliver a maximum of 550 MB/s throughput, which is higher than high I/O EVS disks. They are cost-effective and provide higher performance, optimizing both IOPS and bandwidth. Such disks are particularly suitable for hybrid load scenarios consisting of online analytical processing (OLAP) and online transaction processing (OLTP) or consisting of large and small HPC files.
-  Ultra-high I/O (Latency optimized): EVS disks of this type deliver a maximum of 1 GB/s throughput and a minimum of 1 ms read/write latency. They can be used for enterprise key services, such as SAP HANA.

   .. note::

      Currently, high I/O (performance optimized I) and ultra-high I/O (latency optimized) EVS disks can be attached to SAP HANA ECSs or HL1 ECSs only.

EVS Disk Performance
--------------------

EVS disk performance metrics include:

-  IOPS: Number of read/write operations performed by an EVS disk per second
-  Throughput: Amount of data read from and written into an EVS disk per second
-  Read/write I/O latency: Minimum interval between two consecutive read/write operations on an EVS disk

.. table:: **Table 1** EVS disk performance data

   +-----------------------------------------------------------------------------+----------------+---------------+----------------+------------------------------------+------------------------------------+
   | Parameter                                                                   | Common I/O     | High I/O      | Ultra-high I/O | High I/O (Performance optimized I) | Ultra-high I/O (Latency optimized) |
   +=============================================================================+================+===============+================+====================================+====================================+
   | IOPS per GB/EVS disk                                                        | 1              | 3             | 50             | 3                                  | 50                                 |
   +-----------------------------------------------------------------------------+----------------+---------------+----------------+------------------------------------+------------------------------------+
   | Min. IOPS/EVS disk                                                          | 100            | 100           | 100            | 100                                | 100                                |
   +-----------------------------------------------------------------------------+----------------+---------------+----------------+------------------------------------+------------------------------------+
   | Max. IOPS/EVS disk                                                          | 1,000          | 3,000         | 20,000         | 3,000                              | 30,000                             |
   +-----------------------------------------------------------------------------+----------------+---------------+----------------+------------------------------------+------------------------------------+
   | IOPS burst limit/EVS disk                                                   | 1,000          | 3,000         | 10,000         | 3,000                              | 15,000                             |
   +-----------------------------------------------------------------------------+----------------+---------------+----------------+------------------------------------+------------------------------------+
   | Max. throughput                                                             | 40 MB/s        | 120 MB/s      | 320 MB/s       | 550 MB/s                           | 1 GB/s                             |
   +-----------------------------------------------------------------------------+----------------+---------------+----------------+------------------------------------+------------------------------------+
   | Read/write I/O latency                                                      | 10 ms to 15 ms | 6 ms to 10 ms | 1 ms to 3 ms   | 6 ms to 10 ms                      | 1 ms                               |
   |                                                                             |                |               |                |                                    |                                    |
   | .. note::                                                                   |                |               |                |                                    |                                    |
   |                                                                             |                |               |                |                                    |                                    |
   |    This parameter specifies the single-queue access latencies of EVS disks. |                |               |                |                                    |                                    |
   +-----------------------------------------------------------------------------+----------------+---------------+----------------+------------------------------------+------------------------------------+
