:original_name: evs_01_0046.html

.. _evs_01_0046:

Recording EVS Operations Using CTS
==================================

Scenarios
---------

EVS supports the recording of EVS operations through CTS. You can query EVS traces and use them for historical operation audits and backtracks.

Prerequisites
-------------

CTS has been enabled.

Key EVS Operations Recorded by CTS
----------------------------------

.. table:: **Table 1** EVS operations that can be recorded by CTS

   +----------------------------------------------+----------+-----------------------------+
   | Operation                                    | Resource | Trace                       |
   +==============================================+==========+=============================+
   | Create disk                                  | evs      | createVolume                |
   +----------------------------------------------+----------+-----------------------------+
   | Update disk                                  | evs      | updateVolume                |
   +----------------------------------------------+----------+-----------------------------+
   | Expand disk capacity                         | evs      | extendVolume                |
   +----------------------------------------------+----------+-----------------------------+
   | Delete disk                                  | evs      | deleteVolume                |
   +----------------------------------------------+----------+-----------------------------+
   | Batch create disks                           | evs      | batchCreateVolume           |
   +----------------------------------------------+----------+-----------------------------+
   | Modify disk specifications                   | evs      | retypeVolume                |
   +----------------------------------------------+----------+-----------------------------+
   | Prepare for server stop                      | evs      | prepareForStopServer        |
   +----------------------------------------------+----------+-----------------------------+
   | Batch delete disks                           | evs      | bulkDeleteVolume            |
   +----------------------------------------------+----------+-----------------------------+
   | Clear EVS resources                          | evs      | cleanupEvsResources         |
   +----------------------------------------------+----------+-----------------------------+
   | Clear a single EVS resource                  | evs      | cleanupSingleEvsResource    |
   +----------------------------------------------+----------+-----------------------------+
   | Update disk status                           | evs      | updateVolumesBusinessStatus |
   +----------------------------------------------+----------+-----------------------------+
   | Unfreeze disk                                | evs      | unfreezeVolume              |
   +----------------------------------------------+----------+-----------------------------+
   | Freeze disk                                  | evs      | freezeVolume                |
   +----------------------------------------------+----------+-----------------------------+
   | Release disk                                 | evs      | releaseVolume               |
   +----------------------------------------------+----------+-----------------------------+
   | Delete a single metadata item of an EVS disk | volume   | deleteVolumeSingleMetadata  |
   +----------------------------------------------+----------+-----------------------------+
   | Create disk metadata                         | volume   | createVolumeMetadata        |
   +----------------------------------------------+----------+-----------------------------+

Viewing Traces
--------------

To view audit logs, see section "Querying Real-Time Traces" in the *Cloud Trace Service User Guide*.
