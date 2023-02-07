:original_name: en-us_topic_0014580744.html

.. _en-us_topic_0014580744:

Disk Types and Performance
==========================

EVS disks are classified based on the disk I/O performance. EVS disks differ in performance and price. Choose the disk type most appropriate for your applications.

Application Scenarios
---------------------

-  Common I/O: This type of EVS disks delivers a maximum of 1,000 IOPS. They are suitable for applications that require large capacity, a medium read/write speed, and fewer transactions, such as enterprise office applications and small-scale test environments.
-  High I/O: This type of EVS disks delivers a maximum of 3,000 IOPS and a minimum of 6 ms read/write latency. They are designed to meet the needs of mainstream high-performance, high-reliability applications, such as enterprise applications, large-scale development and test environments, and web server logs.
-  Ultra-high I/O: This type of EVS disks delivers a maximum of 20,000 IOPS and a minimum of 1 ms read/write latency. They are excellent for read/write-intensive applications that require super-high I/O and bandwidth, such as distributed file systems in HPC scenarios or NoSQL/relational databases in I/O-intensive scenarios.
-  High I/O (Performance optimized I): This type of EVS disks delivers a maximum of 550 MiB/s throughput, which is higher than high I/O EVS disks. They are cost-effective and provide higher performance, optimizing both IOPS and bandwidth. Such disks are particularly suitable for mixed load scenarios consisting of online analytical processing (OLAP) and online transaction processing (OLTP) or consisting of large and small HPC files.
-  Ultra-high I/O (Latency optimized): This type of EVS disks delivers a maximum of 1 GiB/s throughput and a minimum of 1 ms read/write latency. They can be used for enterprise mission-critical applications, such as SAP HANA.
-  Extreme SSD: This type of EVS disks delivers a maximum of 128,000 IOPS. They are designed for workloads demanding super-high bandwidth and super-low latency, such as Oracle databases and AI applications.

   .. note::

      -  High I/O (performance optimized I) and ultra-high I/O (latency optimized) EVS disks can only be attached to SAP HANA ECSs or HL1 ECSs.
      -  If an Extreme SSD disk is attached to a BMS, it can reach a maximum IOPS of 128,000. If it is attached to an ECS, it can reach a maximum IOPS of 100,000 due to I/O queue limitations.

EVS Performance
---------------

EVS performance metrics include:

-  IOPS: Number of read/write operations performed by an EVS disk per second
-  Throughput: Amount of data read from and written into an EVS disk per second
-  Read/write I/O latency: Minimum interval between two consecutive read/write operations on an EVS disk

.. table:: **Table 1** EVS performance data

   +-----------------------------------------------------------------------------+----------------+---------------+----------------+------------------------------------+------------------------------------+-----------------+
   | Parameter                                                                   | Common I/O     | High I/O      | Ultra-high I/O | High I/O (Performance optimized I) | Ultra-high I/O (Latency optimized) | Extreme SSD     |
   +=============================================================================+================+===============+================+====================================+====================================+=================+
   | IOPS per GiB/EVS disk                                                       | 1              | 2             | 50             | 6                                  | 50                                 | 50              |
   +-----------------------------------------------------------------------------+----------------+---------------+----------------+------------------------------------+------------------------------------+-----------------+
   | Min. IOPS/EVS disk                                                          | 100            | 100           | 100            | 1,200                              | 1,500                              | 1,800           |
   +-----------------------------------------------------------------------------+----------------+---------------+----------------+------------------------------------+------------------------------------+-----------------+
   | Max. IOPS/EVS disk                                                          | 1,000          | 3,000         | 20,000         | 5,000                              | 33,000                             | 128,000         |
   +-----------------------------------------------------------------------------+----------------+---------------+----------------+------------------------------------+------------------------------------+-----------------+
   | IOPS burst limit/EVS disk                                                   | 1,000          | 3,000         | 10,000         | 5,000                              | 16,000                             | 64,000          |
   +-----------------------------------------------------------------------------+----------------+---------------+----------------+------------------------------------+------------------------------------+-----------------+
   | Max. throughput                                                             | 90 MiB/s       | 150 MiB/s     | 350 MiB/s      | 550 MiB/s                          | 1 GiB/s                            | 1,000 MiB/s     |
   +-----------------------------------------------------------------------------+----------------+---------------+----------------+------------------------------------+------------------------------------+-----------------+
   | Read/write I/O latency                                                      | 10 ms to 15 ms | 6 ms to 10 ms | 1 ms to 3 ms   | 6 ms to 10 ms                      | 1 ms                               | Sub-millisecond |
   |                                                                             |                |               |                |                                    |                                    |                 |
   | .. note::                                                                   |                |               |                |                                    |                                    |                 |
   |                                                                             |                |               |                |                                    |                                    |                 |
   |    This parameter specifies the single-queue access latencies of EVS disks. |                |               |                |                                    |                                    |                 |
   +-----------------------------------------------------------------------------+----------------+---------------+----------------+------------------------------------+------------------------------------+-----------------+
