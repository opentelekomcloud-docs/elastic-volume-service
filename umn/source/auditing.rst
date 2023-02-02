:original_name: evs_01_0046.html

.. _evs_01_0046:

Auditing
========

Scenarios
---------

EVS supports the recording of EVS operations through CTS. You can query EVS traces and use them for historical operation audits and backtracks.

Prerequisites
-------------

CTS has been enabled.

Key EVS Operations Recorded by CTS
----------------------------------

.. table:: **Table 1** EVS operations that can be recorded by CTS

   ==================== ======== ============
   Operation            Resource Trace
   ==================== ======== ============
   Create disk          evs      createVolume
   Update disk          evs      updateVolume
   Expand disk capacity evs      extendVolume
   Delete disk          evs      deleteVolume
   ==================== ======== ============

Viewing Traces
--------------

To view audit logs, see `Querying Traces on the CTS Console <https://docs.otc.t-systems.com/en-us/usermanual/cts/en-us_topic_0030598499.html>`__.
