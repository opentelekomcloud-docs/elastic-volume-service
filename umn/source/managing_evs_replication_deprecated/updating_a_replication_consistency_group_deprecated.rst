:original_name: evs_01_0029.html

.. _evs_01_0029:

Updating a Replication Consistency Group (Deprecated)
=====================================================

Scenarios
---------

Currently, EVS replication pairs can be added to or removed from replication consistency groups through APIs only. For details, see **Updating a Replication Consistency Group** in the *Elastic Volume Service API Reference*.

If an EVS replication pair needs to be deleted after it has been added to a replication consistency group, remove this EVS replication pair from the group first, delete this EVS replication pair, and then delete the production disk and DR disk. For details, see **Deleting an EVS Replication Pair** and **Deleting a Replication Consistency Group** in the *Elastic Volume Service API Reference*.

.. note::

   EVS replication APIs have been deprecated. If you need to use the replication function, see `Storage Disaster Recovery Service User Guide <https://docs.otc.t-systems.com/en-us/usermanual/sdrs/en-us_topic_0125068221.html>`__ and `Storage Disaster Recovery Service API Reference <https://docs.otc.t-systems.com/en-us/api/sdrs/sdrs_01_0000.html>`__.

Prerequisites
-------------

The replication consistency group status is **available**.

Procedure
---------

#. Pause the replication consistency group you need to update.

   For details, see **Pausing a Replication Consistency Group** in the *Elastic Volume Service API Reference*.

   .. note::

      Pausing a replication consistency group means that the data synchronization within the group is paused. Therefore, the data between production disks and DR disks will be temporarily inconsistent and needs to be synchronized after the replication consistency group update is complete.

#. Update the replication consistency group, that is, add EVS replication pairs to or remove EVS replication pairs from the group.

   For details, see **Updating a Replication Consistency Group** in the *Elastic Volume Service API Reference*.

#. Synchronize the data of a replication consistency group, which means that the data of all EVS replication pairs within the group is synchronized.

   For details, see **Synchronizing a Replication Consistency Group** in the *Elastic Volume Service API Reference*.

#. Query the data synchronization status of the replication consistency group.

   For details, see **Querying Details About a Replication Consistency Group** in the *Elastic Volume Service API Reference*.

   When the replication status of the replication consistency group changes to **active**, the data in all EVS replication pairs of this group has been synchronized.
