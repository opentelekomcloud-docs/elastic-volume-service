:original_name: evs_faq_0039.html

.. _evs_faq_0039:

Do I Have to Deploy a Cluster to Use Shared Disks?
==================================================

Yes.

If you simply attach a shared disk to multiple servers, files cannot be shared between the servers. If the rules for reading and writing data are not mutually agreed upon, the read and write operations may interfere with each other, or other unpredictable errors may occur.

Shared EVS disks do not have cluster management capabilities. You need to build a cluster system for data sharing, such as Windows MSCS, Veritas VCS, and Veritas CFS clusters.
