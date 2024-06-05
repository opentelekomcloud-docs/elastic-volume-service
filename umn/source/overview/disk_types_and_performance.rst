:original_name: en-us_topic_0014580744.html

.. _en-us_topic_0014580744:

Disk Types and Performance
==========================

EVS disks are classified based on the disk I/O performance. EVS disks differ in performance and price. Choose the disk type most appropriate for your applications.

Application Scenarios
---------------------

-  Common I/O: This type of EVS disks delivers a maximum IOPS of 1,000. They are suitable for applications that require large capacity, a medium read/write speed, and fewer transactions, such as enterprise office applications and small-scale test environments.
-  High I/O: This type of EVS disks delivers a maximum IOPS of 3,000 and a minimum read/write latency of 6 ms. They are designed to meet the needs of mainstream high-performance, high-reliability applications, such as enterprise applications, large-scale development and test environments, and web server logs.
-  Ultra-high I/O: This type of EVS disks delivers a maximum IOPS of 20,000 and a minimum read/write latency of 1 ms. They are excellent for read/write-intensive applications that require super-high I/O and bandwidth, such as distributed file systems in HPC scenarios or NoSQL/relational databases in I/O-intensive scenarios.
-  Extreme SSD: This type of EVS disks delivers a maximum IOPS of 128,000. They are designed for workloads demanding super-high bandwidth and super-low latency, such as Oracle databases and AI applications.
-  General Purpose SSD: This type of EVS disks delivers a maximum IOPS of 20,000. They are suitable for workloads requiring high throughput and low latency, such as enterprise OA, development and testing, web server logging, containers, and high-performance system disks.

.. note::

   -  If an Extreme SSD disk is attached to a BMS, it can reach a maximum IOPS of 128,000. If it is attached to an ECS, it can reach a maximum IOPS of 100,000 due to I/O queue limitations.

EVS Performance
---------------

EVS performance metrics include:

-  IOPS: Number of read/write operations performed by an EVS disk per second
-  Throughput: Amount of data read from and written into an EVS disk per second
-  Read/write I/O latency: Minimum interval between two consecutive read/write operations on an EVS disk

.. table:: **Table 1** EVS performance data

   +---------------------------------------+----------------------------------+-----------------------------------+--------------------------------------+------------------------------------+---------------------------------------+
   | Parameter                             | Common I/O                       | High I/O                          | General Purpose SSD                  | Ultra-high I/O                     | Extreme SSD                           |
   +=======================================+==================================+===================================+======================================+====================================+=======================================+
   | IOPS per GiB/EVS disk                 | 1                                | 2                                 | 12                                   | 50                                 | 50                                    |
   +---------------------------------------+----------------------------------+-----------------------------------+--------------------------------------+------------------------------------+---------------------------------------+
   | Min. IOPS/EVS disk                    | 100                              | 100                               | 1,800                                | 100                                | 1,800                                 |
   +---------------------------------------+----------------------------------+-----------------------------------+--------------------------------------+------------------------------------+---------------------------------------+
   | Max. IOPS/EVS disk                    | 1,000                            | 3,000                             | 20,000                               | 20,000                             | 128,000                               |
   +---------------------------------------+----------------------------------+-----------------------------------+--------------------------------------+------------------------------------+---------------------------------------+
   | Disk IOPS                             | Min. (1,000, 100 + 1 x Capacity) | Min. (3,000, 100 + 2 x Capacity)  | Min. (20,000, 1,800 + 12 x Capacity) | Min. (20,000, 100 + 50 x Capacity) | Min. (128,000, 1,800 + 50 x Capacity) |
   +---------------------------------------+----------------------------------+-----------------------------------+--------------------------------------+------------------------------------+---------------------------------------+
   | IOPS burst limit/EVS disk             | 1,000                            | 3,000                             | 8,000                                | 10,000                             | 64,000                                |
   +---------------------------------------+----------------------------------+-----------------------------------+--------------------------------------+------------------------------------+---------------------------------------+
   | Max. throughput                       | 90 MiB/s                         | 150 MiB/s                         | 250 MiB/s                            | 350 MiB/s                          | 1,000 MiB/s                           |
   +---------------------------------------+----------------------------------+-----------------------------------+--------------------------------------+------------------------------------+---------------------------------------+
   | Disk throughput (MiB/s)               | 50                               | Min. (150, 100 + 0.15 x Capacity) | Min. (250, 100 + 0.5 x Capacity)     | Min. (350, 120 + 0.5 x Capacity)   | Min. (1,000, 120 + 0.5 x Capacity)    |
   +---------------------------------------+----------------------------------+-----------------------------------+--------------------------------------+------------------------------------+---------------------------------------+
   | I/O read/write latency (single-queue) | 10 ms to 15 ms                   | 6 ms to 10 ms                     | 1 ms                                 | 1 ms to 3 ms                       | Sub-millisecond                       |
   +---------------------------------------+----------------------------------+-----------------------------------+--------------------------------------+------------------------------------+---------------------------------------+

EVS disk performance is closely related with the data block size:

-  If data blocks are of the same size, a disk can achieve either the maximum IOPS or maximum throughput depending on which one is reached first.
-  If data blocks are of different sizes, the maximum performance metric that a disk can achieve varies:

   -  For small data blocks, such as 4 KiB or 8 KiB, a disk can reach the maximum IOPS.
   -  For data blocks greater than or equal to 16 KiB, a disk can reach the maximum throughput.

The following uses an ultra-high I/O disk as an example. According to the formula, when the size of an ultra-high I/O disk is greater than or equal to 460 GiB, the disk theoretically can reach either the maximum IOPS 20,000 or the maximum throughput 350 MiB/s. However, this is not the case in practice. The maximum IOPS and maximum throughput that a disk can reach also vary with the data block size. For details, see :ref:`Table 2 <en-us_topic_0014580744__table721615248300>`.

.. _en-us_topic_0014580744__table721615248300:

.. table:: **Table 2** Maximum performance of an ultra-high I/O EVS disk

   =============== ============ =======================
   Data Block Size Max. IOPS    Max. Throughput (MiB/s)
   =============== ============ =======================
   4 KiB           About 20,000 About 78
   8 KiB           About 20,000 About 156
   16 KiB          About 20,000 About 312
   32 KiB          About 11,200 About 350
   =============== ============ =======================

Disk IOPS Calculation Formula
-----------------------------

Disk IOPS = Min. (Maximum IOPS, Minimum IOPS + IOPS per GiB x Capacity)

The following example uses an ultra-high I/O EVS disk with a maximum IOPS of 20,000.

-  If the disk capacity is 100 GiB, the disk IOPS is calculated as follows: Disk IOPS = Min. (20,000, 100 + 50 x 100)

   The disk IOPS is 5,100, the smaller value between 20,000 and 5,100.

-  If the disk capacity is 1,000 GiB, the disk IOPS is calculated as follows: Disk IOPS = Min. (20,000, 100 + 50 x 1,000)

   The disk IOPS is 20,000, the smaller value between 20,000 and 50,100.

Disk Burst Capability and Principles
------------------------------------

EVS disks have burst capability, which allows a small-capacity disk to surpass its maximum IOPS within a certain period of time. This IOPS applies to individual disks.

Disks with burst capability are well-suited for speeding up server startup. In most cases, system disks have small capacities. For example, the IOPS of a 50-GiB ultra-high I/O disk without burst capability can only reach up to 2,600, calculated as follows: IOPS = Min. (20,000, 100 + 50 x Capacity). If the disk has burst capability, its IOPS can burst up to 10,000.

The following example uses an ultra-high I/O EVS disk with the IOPS burst limit of 10,000.

-  If the disk capacity is 100 GiB, the disk has a maximum IOPS of 5,100, but it can burst to 10,000 IOPS in a certain duration.
-  If the disk capacity is 1,000 GiB, the disk has a maximum IOPS of 20,000. The disk maximum IOPS already exceeds its burst IOPS 10,000, and the disk does not use the burst capability.

The following describes the burst IOPS consumption and reservation.

A token bucket is used to handle burst I/O operations. The number of initial tokens in the bucket is calculated as follows:

Number of initial tokens = Burst duration x IOPS burst limit

In the following example, a 100-GiB ultra-high I/O EVS disk is used, and the fixed burst duration is 1800s. Therefore, the number of initial tokens is 18,000,000 (1,800 x 10,000).

-  Token production rate: This rate equals the disk maximum IOPS, which is 5,100 tokens/s.
-  Token consumption rate: This rate is calculated based on the I/O usage. Each I/O request consumes a token. The maximum consumption rate is 10,000 tokens/s, which is the larger value between the disk burst IOPS and maximum IOPS.

Consumption principles

When the token consumption rate is greater than the production rate, the number of tokens decreases accordingly, and eventually the disk IOPS will be consistent with the token production rate (the maximum IOPS). In this example, the disk can burst for approximately 3,673 seconds [18,000,000/(10,000 - 5,100)].

Reservation principles

When the token consumption rate is smaller than the production rate, the number of tokens increases accordingly, enabling the disk to regain the burst capability. In this example, if the disk is suspended for approximately 3,529 seconds (18,000,000/5,100), the token bucket will be filled up with tokens.

.. note::

   As long as there are tokens in the token bucket, the disk has the burst capability.

:ref:`Figure 1 <en-us_topic_0014580744__fig10343858185721>` shows the token consumption and reservation principles. The blue bars indicate the disk IOPS usage, the green dashed line represents the maximum IOPS, the red dashed line indicates the IOPS burst limit, and the black curve indicates the changes of the number of tokens.

-  When the number of tokens is greater than zero, the disk IOPS can exceed 5,100 and has the capability to reach 10,000, the IOPS burst limit.
-  When the number of tokens is zero, the disk does not have the burst capability, and the maximum IOPS is 5,100.
-  When the disk IOPS is less than 5,100, the number of tokens starts to increase, and the disk can regain the burst capability.

.. _en-us_topic_0014580744__fig10343858185721:

.. figure:: /_static/images/en-us_image_0113597958.png
   :alt: **Figure 1** Burst capability diagram

   **Figure 1** Burst capability diagram

Performance Test Method
-----------------------

For details about how to test the EVS disk performance parameters, see :ref:`How Can I Test My Disk Performance? <evs_faq_0019>`.
