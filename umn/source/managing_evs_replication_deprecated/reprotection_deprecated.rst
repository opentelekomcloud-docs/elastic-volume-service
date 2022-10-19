:original_name: evs_01_0032.html

.. _evs_01_0032:

Reprotection (Deprecated)
=========================

Scenarios
---------

When the production servers and disks in the primary AZ become faulty due to force majeure and a failover has been performed, enable the DR servers and disks to provide services. After the fault in the faulty AZ has been restored, users can make API calls to reprotect a replication consistency group, that is, to enable the restored resources in the faulty AZ to function as DR servers and DR disks.

.. note::

   EVS replication APIs have been deprecated. If you need to use the replication function, see `Storage Disaster Recovery Service User Guide <https://docs.otc.t-systems.com/en-us/usermanual/sdrs/en-us_topic_0125068221.html>`__ and `Storage Disaster Recovery Service API Reference <https://docs.otc.t-systems.com/en-us/api/sdrs/sdrs_01_0000.html>`__.

Prerequisites
-------------

-  A failover for the replication consistency group has been performed.
-  The faulty AZ has been restored.
-  The replication consistency group status is **available**.
-  The restored production server has been stopped.

Procedure
---------

#. Perform the reprotection for the replication consistency group to synchronize the disk data of the DR servers to the servers in the faulty AZ.

   For details, see **Reprotecting a Replication Consistency Group** in the *Elastic Volume Service API Reference*.

#. Query the details about the replication consistency group.

   For details, see **Querying Details About a Replication Consistency Group** in the *Elastic Volume Service API Reference*.

   After the request has been delivered, the replication status of the replication consistency group changes to **copying**. Once the replication status changes to **active**, the data synchronization is complete.

   .. note::

      The time required for the data synchronization within a replication consistency group varies depending on the number of EVS replication pairs in the group, EVS disk capacity, and amount of differential data generated after a primary AZ fault occurred. Normally, the data synchronization of a reprotection takes a relative long period of time. Please wait patiently.

#. (Optional) If the services need to be migrated back to the restored primary AZ, you need to perform a planned migration. For details, see :ref:`Planned Migration (Deprecated) <evs_01_0030>`.
