:original_name: evs_04_0027.html

.. _evs_04_0027:

Snapshot
========

This topic describes only the authorization information of EVS v2 APIs. For the v3 APIs that provide the same functions as their v2 APIs, their authorization information is the same as that of the v2 APIs.

For example, the v2 API for creating disks is POST /v2/{project_id}/cloudvolumes, and the v3 API for creating disks is POST /v3/{project_id}/cloudvolumes. The authorization information of both APIs is the same.

In the following tables, Y indicates that the item is supported, and × indicates that the item is not supported.

+-------------------------------------------------------------------+------------------------------------------------------------------+------------------------+-----------------+
| Permission                                                        | API                                                              | Action                 | IAM Project     |
|                                                                   |                                                                  |                        |                 |
|                                                                   |                                                                  |                        | (Project)       |
+===================================================================+==================================================================+========================+=================+
| Create an EVS snapshot (OpenStack Cinder API).                    | POST /v2/{project_id}/snapshots                                  | evs:snapshots:create   | Y               |
|                                                                   |                                                                  |                        |                 |
|                                                                   |                                                                  | evs:volumes:get        |                 |
+-------------------------------------------------------------------+------------------------------------------------------------------+------------------------+-----------------+
| Create an EVS snapshot.                                           | POST /v2/{project_id}/cloudsnapshots                             | evs:snapshots:create   | Y               |
+-------------------------------------------------------------------+------------------------------------------------------------------+------------------------+-----------------+
| Query EVS snapshots (OpenStack Cinder API).                       | GET /v2/{project_id}/snapshots                                   | evs:snapshots:list     | Y               |
+-------------------------------------------------------------------+------------------------------------------------------------------+------------------------+-----------------+
| Query details of EVS snapshots (OpenStack Cinder API).            | GET /v2/{project_id}/snapshots/detail                            | evs:snapshots:list     | Y               |
+-------------------------------------------------------------------+------------------------------------------------------------------+------------------------+-----------------+
| Query details about EVS snapshots.                                | GET /v2/{project_id}/cloudsnapshots/detail                       | evs:snapshots:list     | Y               |
+-------------------------------------------------------------------+------------------------------------------------------------------+------------------------+-----------------+
| Update an EVS snapshot (OpenStack Cinder API).                    | PUT /v2/{project_id}/snapshots/{snapshot_id}                     | evs:snapshots:update   | Y               |
|                                                                   |                                                                  |                        |                 |
|                                                                   |                                                                  | evs:snapshots:get      |                 |
+-------------------------------------------------------------------+------------------------------------------------------------------+------------------------+-----------------+
| Update an EVS snapshot.                                           | PUT /v2/{project_id}/cloudsnapshots/{snapshot_id}                | evs:snapshots:update   | Y               |
+-------------------------------------------------------------------+------------------------------------------------------------------+------------------------+-----------------+
| Query details about a single EVS snapshot (OpenStack Cinder API). | GET /v2/{project_id}/snapshots/{snapshot_id}                     | evs:snapshots:get      | Y               |
+-------------------------------------------------------------------+------------------------------------------------------------------+------------------------+-----------------+
| Querying details about an EVS snapshot.                           | GET /v2/{project_id}/cloudsnapshots/{snapshot_id}                | evs:snapshots:get      | Y               |
+-------------------------------------------------------------------+------------------------------------------------------------------+------------------------+-----------------+
| Delete an EVS snapshot (OpenStack Cinder API).                    | DELETE /v2/{project_id}/snapshots/{snapshot_id}                  | evs:snapshots:delete   | Y               |
|                                                                   |                                                                  |                        |                 |
|                                                                   |                                                                  | evs:snapshots:get      |                 |
|                                                                   |                                                                  |                        |                 |
|                                                                   |                                                                  | evs:volumes:get        |                 |
+-------------------------------------------------------------------+------------------------------------------------------------------+------------------------+-----------------+
| Deleting an EVS snapshot.                                         | DELETE /v2/{project_id}/cloudsnapshots/{snapshot_id}             | evs:snapshots:delete   | Y               |
+-------------------------------------------------------------------+------------------------------------------------------------------+------------------------+-----------------+
| Roll back a snapshot to an EVS disk.                              | POST /v2/{project_id}/cloudsnapshots/{snapshot_id}/rollback      | evs:snapshots:rollback | Y               |
+-------------------------------------------------------------------+------------------------------------------------------------------+------------------------+-----------------+
| Roll back a snapshot to an EVS disk.                              | POST /v2/{project_id}/os-vendor-snapshots/{snapshot_id}/rollback | evs:snapshots:rollback | Y               |
|                                                                   |                                                                  |                        |                 |
|                                                                   |                                                                  | evs:snapshots:get      |                 |
|                                                                   |                                                                  |                        |                 |
|                                                                   |                                                                  | evs:volumes:get        |                 |
+-------------------------------------------------------------------+------------------------------------------------------------------+------------------------+-----------------+
| Add the metadata of an EVS snapshot (OpenStack Cinder API).       | POST /v2/{project_id}/snapshots/{snapshot_id}/metadata           | evs:snapshots:update   | Y               |
|                                                                   |                                                                  |                        |                 |
|                                                                   |                                                                  | evs:snapshots:get      |                 |
+-------------------------------------------------------------------+------------------------------------------------------------------+------------------------+-----------------+
| Query the metadata of an EVS snapshot (OpenStack Cinder API).     | GET /v2/{project_id}/snapshots/{snapshot_id}/metadata            | evs:snapshots:get      | Y               |
+-------------------------------------------------------------------+------------------------------------------------------------------+------------------------+-----------------+
| Update one piece of EVS snapshot metadata (OpenStack Cinder API). | PUT /v2/{project_id}/snapshots/{snapshot_id}/metadata/{key}      | evs:snapshots:update   | Y               |
|                                                                   |                                                                  |                        |                 |
|                                                                   |                                                                  | evs:snapshots:get      |                 |
+-------------------------------------------------------------------+------------------------------------------------------------------+------------------------+-----------------+
| Update the metadata of an EVS snapshot (OpenStack Cinder API).    | PUT /v2/{project_id}/snapshots/{snapshot_id}/metadata            | evs:snapshots:update   | Y               |
|                                                                   |                                                                  |                        |                 |
|                                                                   |                                                                  | evs:snapshots:get      |                 |
+-------------------------------------------------------------------+------------------------------------------------------------------+------------------------+-----------------+
| Query one piece of EVS snapshot metadata (OpenStack Cinder API).  | GET /v2/{project_id}/snapshots/{snapshot_id}/metadata/{key}      | evs:snapshots:get      | Y               |
+-------------------------------------------------------------------+------------------------------------------------------------------+------------------------+-----------------+
| Delete one piece of EVS snapshot metadata (OpenStack Cinder API). | DELETE /v2/{project_id}/snapshots/{snapshot_id}/metadata/{key}   | evs:snapshots:delete   | Y               |
|                                                                   |                                                                  |                        |                 |
|                                                                   |                                                                  | evs:snapshots:get      |                 |
+-------------------------------------------------------------------+------------------------------------------------------------------+------------------------+-----------------+
