:original_name: evs_01_0031.html

.. _evs_01_0031:

Failover (Deprecated)
=====================

Scenarios
---------

When the production servers and disks in the primary AZ become faulty due to force majeure, users can make API calls to perform a failover for the replication consistency group and enable the DR servers and disks in the secondary AZ to ensure the service continuity.

.. note::

   EVS replication APIs have been deprecated. If you need to use the replication function, see `Storage Disaster Recovery Service User Guide <https://docs.otc.t-systems.com/en-us/usermanual/sdrs/en-us_topic_0125068221.html>`__ and `Storage Disaster Recovery Service API Reference <https://docs.otc.t-systems.com/en-us/api/sdrs/sdrs_01_0000.html>`__.

Prerequisites
-------------

Confirm with the customer service that servers and disks in the production AZ are faulty, and the deployed services are unavailable.

Procedure
---------

#. Perform a failover for the replication consistency group.

   For details, see **Performing a Failover for a Replication Consistency Group** in the *Elastic Volume Service API Reference*.

#. If Elastic Load Balancing (ELB) or EIPs are used, unbind the ELB or EIPs with the production servers and bind them to the DR servers.

   -  For details about ELB, see **Backend Server (Enhanced Load Balancer)** in the *Elastic Load Balancing User Guide*.
   -  For details about EIPs, see **Elastic IP Address** in the *Virtual Private Cloud User Guide*.

#. Verify that the DR server OSs can be normally started, deployed services are available, and the data is complete.
