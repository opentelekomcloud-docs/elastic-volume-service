:original_name: evs_04_0025.html

.. _evs_04_0025:

Disk
====

This topic describes only the authorization information of EVS v2 APIs. For the v3 APIs that provide the same functions as their v2 APIs, their authorization information is the same as that of the v2 APIs.

For example, the v2 API for creating disks is POST /v2/{project_id}/cloudvolumes, and the v3 API for creating disks is POST /v3/{project_id}/cloudvolumes. The authorization information of both APIs is the same.

In the following tables, Y indicates that the item is supported, and x indicates that the item is not supported.

+---------------------------------------------------------------+------------------------------------------------------------------+-------------------------------------+-----------------+
| Permission                                                    | API                                                              | Action                              | IAM Project     |
|                                                               |                                                                  |                                     |                 |
|                                                               |                                                                  |                                     | (Project)       |
+===============================================================+==================================================================+=====================================+=================+
| Create EVS disks.                                             | POST /v2/{project_id}/cloudvolumes                               | evs:volumes:create                  | Y               |
+---------------------------------------------------------------+------------------------------------------------------------------+-------------------------------------+-----------------+
| Create EVS disks (OpenStack Cinder API).                      | POST /v2/{project_id}/volumes                                    | -  Create empty EVS disks.          | Y               |
|                                                               |                                                                  |                                     |                 |
|                                                               |                                                                  |    evs:volumes:create               |                 |
|                                                               |                                                                  |                                     |                 |
|                                                               |                                                                  |    evs:volumes:get                  |                 |
|                                                               |                                                                  |                                     |                 |
|                                                               |                                                                  | -  Create EVS disks from images.    |                 |
|                                                               |                                                                  |                                     |                 |
|                                                               |                                                                  |    evs:volumes:create               |                 |
|                                                               |                                                                  |                                     |                 |
|                                                               |                                                                  |    ims:images:get                   |                 |
|                                                               |                                                                  |                                     |                 |
|                                                               |                                                                  |    evs:volumes:get                  |                 |
|                                                               |                                                                  |                                     |                 |
|                                                               |                                                                  | -  Create EVS disks from snapshots. |                 |
|                                                               |                                                                  |                                     |                 |
|                                                               |                                                                  |    evs:volumes:create               |                 |
|                                                               |                                                                  |                                     |                 |
|                                                               |                                                                  |    evs:snapshots:get                |                 |
|                                                               |                                                                  |                                     |                 |
|                                                               |                                                                  |    evs:volumes:get                  |                 |
+---------------------------------------------------------------+------------------------------------------------------------------+-------------------------------------+-----------------+
| Expand the capacity of an EVS disk.                           | POST /v2/{project_id}/cloudvolumes/{volume_id}/action            | evs:volumes:extend                  | Y               |
+---------------------------------------------------------------+------------------------------------------------------------------+-------------------------------------+-----------------+
| Query EVS disks.                                              | GET /v2/{project_id}/cloudvolumes                                | evs:volumes:list                    | Y               |
+---------------------------------------------------------------+------------------------------------------------------------------+-------------------------------------+-----------------+
| Query EVS disks (OpenStack Cinder API).                       | GET /v2/{project_id}/volumes                                     | evs:volumes:list                    | Y               |
+---------------------------------------------------------------+------------------------------------------------------------------+-------------------------------------+-----------------+
| Query details of all EVS disks.                               | GET /v2/{project_id}/cloudvolumes/detail                         | evs:volumes:list                    | Y               |
+---------------------------------------------------------------+------------------------------------------------------------------+-------------------------------------+-----------------+
| Querying Details About All Disks                              | GET /v2/{project_id}/os-vendor-volumes/detail                    | evs:volumes:list                    | Y               |
+---------------------------------------------------------------+------------------------------------------------------------------+-------------------------------------+-----------------+
| Query details of all EVS disks (OpenStack Cinder API).        | GET /v2/{project_id}/volumes/detail                              | evs:volumes:list                    | Y               |
+---------------------------------------------------------------+------------------------------------------------------------------+-------------------------------------+-----------------+
| Query details of an EVS disk.                                 | GET /v2/{project_id}/os-vendor-volumes/{volume_id}               | evs:volumes:get                     | Y               |
+---------------------------------------------------------------+------------------------------------------------------------------+-------------------------------------+-----------------+
| Query details of an EVS disk (OpenStack Cinder API).          | GET /v2/{project_id}/volumes/{volume_id}                         | evs:volumes:get                     | Y               |
+---------------------------------------------------------------+------------------------------------------------------------------+-------------------------------------+-----------------+
| Query details of an EVS disk.                                 | GET /v2/{project_id}/cloudvolumes/{volume_id}                    | evs:volumes:get                     | Y               |
+---------------------------------------------------------------+------------------------------------------------------------------+-------------------------------------+-----------------+
| Delete an EVS disk.                                           | DELETE /v2/{project_id}/cloudvolumes/{volume_id}                 | evs:volumes:delete                  | Y               |
+---------------------------------------------------------------+------------------------------------------------------------------+-------------------------------------+-----------------+
| Delete an EVS disk (OpenStack Cinder API).                    | DELETE /v2/{project_id}/volumes/{volume_id}                      | evs:volumes:delete                  | Y               |
|                                                               |                                                                  |                                     |                 |
|                                                               |                                                                  | evs:volumes:get                     |                 |
+---------------------------------------------------------------+------------------------------------------------------------------+-------------------------------------+-----------------+
| Update EVS disk information.                                  | PUT /v2/{project_id}/cloudvolumes/{volume_id}                    | evs:volumes:update                  | Y               |
+---------------------------------------------------------------+------------------------------------------------------------------+-------------------------------------+-----------------+
| Update EVS disk information (OpenStack Cinder API).           | PUT /v2/{project_id}/volumes/{volume_id}                         | evs:volumes:update                  | Y               |
|                                                               |                                                                  |                                     |                 |
|                                                               |                                                                  | evs:volumes:get                     |                 |
+---------------------------------------------------------------+------------------------------------------------------------------+-------------------------------------+-----------------+
| Update one piece of EVS disk metadata (OpenStack Cinder API). | PUT /v2/{project_id}/volumes/{volume_id}/metadata/{key}          | evs:volumes:update                  | Y               |
|                                                               |                                                                  |                                     |                 |
|                                                               |                                                                  | evs:volumes:get                     |                 |
+---------------------------------------------------------------+------------------------------------------------------------------+-------------------------------------+-----------------+
| Update the metadata of an EVS disk (OpenStack Cinder API).    | PUT /v2/{project_id}/volumes/{volume_id}/metadata                | evs:volumes:update                  | Y               |
|                                                               |                                                                  |                                     |                 |
|                                                               |                                                                  | evs:volumes:get                     |                 |
+---------------------------------------------------------------+------------------------------------------------------------------+-------------------------------------+-----------------+
| Query one piece of EVS disk metadata (OpenStack Cinder API).  | GET /v2/{project_id}/volumes/{volume_id}/metadata/{key}          | evs:volumes:get                     | Y               |
+---------------------------------------------------------------+------------------------------------------------------------------+-------------------------------------+-----------------+
| Delete one piece of EVS disk metadata (OpenStack Cinder API). | DELETE /v2/{project_id}/volumes/{volume_id}/metadata/{key}       | evs:volumes:delete                  | Y               |
|                                                               |                                                                  |                                     |                 |
|                                                               |                                                                  | evs:volumes:get                     |                 |
+---------------------------------------------------------------+------------------------------------------------------------------+-------------------------------------+-----------------+
| Query the metadata of an EVS disk (OpenStack Cinder API).     | GET /v2/{project_id}/volumes/{volume_id}/metadata                | evs:volumes:get                     | Y               |
+---------------------------------------------------------------+------------------------------------------------------------------+-------------------------------------+-----------------+
| Add the metadata of an EVS disk (OpenStack Cinder API).       | POST /v2/{project_id}/volumes/{volume_id}/metadata               | evs:volumes:update                  | Y               |
|                                                               |                                                                  |                                     |                 |
|                                                               |                                                                  | evs:volumes:get                     |                 |
+---------------------------------------------------------------+------------------------------------------------------------------+-------------------------------------+-----------------+
| Query EVS disk types (OpenStack Cinder API).                  | GET /v2/{project_id}/types                                       | evs:types:get                       | Y               |
+---------------------------------------------------------------+------------------------------------------------------------------+-------------------------------------+-----------------+
| Query details of an EVS disk type (OpenStack Cinder API).     | GET /v2/{project_id}/types/{type_id}                             | evs:types:get                       | Y               |
+---------------------------------------------------------------+------------------------------------------------------------------+-------------------------------------+-----------------+
| Query tenant quotas (OpenStack Cinder API).                   | GET /v2/{project_id}/os-quota-sets/{project_id}                  | evs:quotas:get                      | Y               |
+---------------------------------------------------------------+------------------------------------------------------------------+-------------------------------------+-----------------+
| Query extension APIs (OpenStack Cinder API).                  | GET /v2/{project_id}/extensions                                  | None                                | Y               |
+---------------------------------------------------------------+------------------------------------------------------------------+-------------------------------------+-----------------+
| Query information of all AZs (OpenStack Cinder API).          | GET /v2/{project_id}/os-availability-zone                        | None                                | Y               |
+---------------------------------------------------------------+------------------------------------------------------------------+-------------------------------------+-----------------+
| Query loading progress of a lazyloading disk.                 | GET /v3/{project_id}/os-vendor-volumes/{volume_id}/internal-info | evs:volumes:get                     | Y               |
+---------------------------------------------------------------+------------------------------------------------------------------+-------------------------------------+-----------------+
| Query EVS disks (OpenStack Cinder API).                       | GET /v3/{project_id}/volumes/summary                             | evs:volumes:get                     | Y               |
|                                                               |                                                                  |                                     |                 |
|                                                               |                                                                  | evs:volumes:list                    |                 |
+---------------------------------------------------------------+------------------------------------------------------------------+-------------------------------------+-----------------+

.. note::

   If **Action** is **None**, no authorization is required.
