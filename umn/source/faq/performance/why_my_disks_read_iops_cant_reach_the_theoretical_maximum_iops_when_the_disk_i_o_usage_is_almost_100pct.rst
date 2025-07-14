:original_name: evs_faq_280905.html

.. _evs_faq_280905:

Why My Disk's Read IOPS Can't Reach the Theoretical Maximum IOPS When the Disk I/O Usage Is Almost 100%?
========================================================================================================

**Symptom**

A 500 GiB ultra-high I/O disk had an I/O usage of 99.94%, but it only had 12,000 IOPS.

**Description**

-  **100% disk I/O usage does not mean that the disk IOPS reaches the maximum.**

   Disk I/O usage calculates the read or write operations performed by a disk in a measurement period. It describes how busy a disk is, not the disk I/O performance.

   EVS disks can process I/O requests concurrently, so 100% disk I/O usage does not mean that the disk encounters the performance bottleneck. For example, an EVS disk takes 0.1 second to process an I/O request and can process 10 I/O requests concurrently. If 10 I/O requests are submitted serially, the disk takes 1 second to process all I/O requests. In this 1-second measurement period, the disk I/O usage reaches 100%. However, if 10 I/O requests are submitted concurrently, the disk takes just 0.1 second to process all the requests. This way, the disk I/O usage in a 1-second measurement period is only 10%. This means that a disk can still process I/O requests even if its I/O usage reaches 100%.

-  **Why does the disk not reach the theoretical maximum IOPS?**

   The actual maximum IOPS that a disk can reach is calculated as follows: Disk IOPS = Min. (Max. IOPS, Min. IOPS + IOPS per GiB x Disk size). For a 500 GiB ultra-high I/O disk, its IOPS is calculated as follows: Disk IOPS = Min. (20,000, 100 + 50 x 500) = 20,000

   The disk read IOPS is the number of read operations performed by the disk per second. IOPS is also affected by latency. In a single-queue access scenario with 4 KiB data blocks, the access latency of an ultra-high I/O disk is 1 ms, which means the disk can process 1,000 requests (IOPS) in a second. 12,000 IOPS indicates that the queue depth is 12. To reach the theoretical maximum IOPS (20,000), the queue depth should reach 20.
