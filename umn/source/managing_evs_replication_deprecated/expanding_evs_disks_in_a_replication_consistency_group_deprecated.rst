:original_name: evs_01_0043.html

.. _evs_01_0043:

Expanding EVS Disks in a Replication Consistency Group (Deprecated)
===================================================================

Scenarios
---------

Users can make an API call to expand the EVS disks in one or multiple EVS replication pairs of a replication consistency group. In such an expansion operation, two EVS disks in one EVS replication pair are expanded together.

.. note::

   The **status** and **replication_status** values of the replication consistency group remain unchanged before and after capacity expansion.

   If the expansion fails, contact customer service to locate and rectify the fault. After the fault is rectified, expand the disks again.

   EVS replication APIs have been deprecated. If you need to use the replication function, see `Storage Disaster Recovery Service User Guide <https://docs.otc.t-systems.com/en-us/usermanual/sdrs/en-us_topic_0125068221.html>`__ and `Storage Disaster Recovery Service API Reference <https://docs.otc.t-systems.com/en-us/api/sdrs/sdrs_01_0000.html>`__.

Prerequisites
-------------

-  The **status** value of replication consistency group must be **available**, which means that the group status is normal.
-  The **replication_status** value of the replication consistency group is not **error**.

Procedure
---------

#. Make an API call to expand the EVS disks in one or multiple EVS replication pairs of the replication consistency group.

   For details, see **Expanding EVS Disks a Replication Consistency Group** in the *Elastic Volume Service API Reference*.
