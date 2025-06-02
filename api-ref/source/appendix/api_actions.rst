:original_name: evs_04_0045.html

.. _evs_04_0045:

API Actions
===========

This topic describes only the authorization information of EVS v2 APIs. For the v3 APIs that provide the same functions as their v2 APIs, their authorization information is the same as that of the v2 APIs.

For example, the v2 API for creating disks is POST /v2/{project_id}/cloudvolumes, and the v3 API for creating disks is POST /v3/{project_id}/cloudvolumes. The authorization information of both APIs is the same.

In the following tables, Y indicates that the item is supported, and x indicates that the item is not supported.

API Version Query
-----------------

+-----------------------------------------------+--------------------+-----------------+-----------------+
| Permission                                    | API                | Action          | IAM Project     |
|                                               |                    |                 |                 |
|                                               |                    |                 | (Project)       |
+===============================================+====================+=================+=================+
| Query API versions (OpenStack Cinder API).    | GET /              | None            | Y               |
+-----------------------------------------------+--------------------+-----------------+-----------------+
| Query the API version (OpenStack Cinder API). | GET /{api_version} | None            | Y               |
+-----------------------------------------------+--------------------+-----------------+-----------------+

EVS Disk
--------

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

EVS Disk Actions
----------------

+---------------------------------------------------------------------+--------------------------------------------------+-------------------------+-----------------+
| Permission                                                          | API                                              | Action                  | IAM Project     |
|                                                                     |                                                  |                         |                 |
|                                                                     |                                                  |                         | (Project)       |
+=====================================================================+==================================================+=========================+=================+
| Expand the capacity of an EVS disk (OpenStack Cinder API).          | POST /v2/{project_id}/volumes/{volume_id}/action | evs:volumes:extend      | Y               |
|                                                                     |                                                  |                         |                 |
|                                                                     | action="os-extend"                               | evs:volumes:get         |                 |
+---------------------------------------------------------------------+--------------------------------------------------+-------------------------+-----------------+
| Export the EVS disk data as an image (OpenStack Cinder API).        | POST /v2/{project_id}/volumes/{volume_id}/action | evs:volumes:uploadImage | Y               |
|                                                                     |                                                  |                         |                 |
|                                                                     | action="os-volume_upload_image"                  |                         |                 |
+---------------------------------------------------------------------+--------------------------------------------------+-------------------------+-----------------+
| Attach an EVS disk (OpenStack Cinder API).                          | POST /v2/{project_id}/volumes/{volume_id}/action | evs:volumes:attach      | Y               |
|                                                                     |                                                  |                         |                 |
|                                                                     | action="os-attach"                               | evs:volumes:get         |                 |
+---------------------------------------------------------------------+--------------------------------------------------+-------------------------+-----------------+
| Detach an EVS disk (OpenStack Cinder API).                          | POST /v2/{project_id}/volumes/{volume_id}/action | evs:volumes:detach      | Y               |
|                                                                     |                                                  |                         |                 |
|                                                                     | action="os-detach"                               | evs:volumes:get         |                 |
+---------------------------------------------------------------------+--------------------------------------------------+-------------------------+-----------------+
| Reserve an EVS disk (OpenStack Cinder API).                         | POST /v2/{project_id}/volumes/{volume_id}/action | evs:volumes:attach      | Y               |
|                                                                     |                                                  |                         |                 |
|                                                                     | action="os-reserve"                              |                         |                 |
+---------------------------------------------------------------------+--------------------------------------------------+-------------------------+-----------------+
| Cancel reservation of an EVS disk (OpenStack Cinder API).           | POST /v2/{project_id}/volumes/{volume_id}/action | evs:volumes:attach      | Y               |
|                                                                     |                                                  |                         |                 |
|                                                                     | action="os-unreserve"                            |                         |                 |
+---------------------------------------------------------------------+--------------------------------------------------+-------------------------+-----------------+
| Set the bootable flag for an EVS disk (OpenStack Cinder API).       | POST /v2/{project_id}/volumes/{volume_id}/action | evs:volumes:update      | Y               |
|                                                                     |                                                  |                         |                 |
|                                                                     | action="os-set_bootable"                         |                         |                 |
+---------------------------------------------------------------------+--------------------------------------------------+-------------------------+-----------------+
| Set the read-only attribute for an EVS disk (OpenStack Cinder API). | POST /v2/{project_id}/volumes/{volume_id}/action | evs:volumes:update      | Y               |
|                                                                     |                                                  |                         |                 |
|                                                                     | action="os-update_readonly_flag"                 |                         |                 |
+---------------------------------------------------------------------+--------------------------------------------------+-------------------------+-----------------+

EVS Snapshot
------------

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

EVS Tag
-------

+---------------------------------------------+----------------------------------------------------------------------------+---------------------------------------+-----------------+
| Permission                                  | API                                                                        | Action                                | IAM Project     |
|                                             |                                                                            |                                       |                 |
|                                             |                                                                            |                                       | (Project)       |
+=============================================+============================================================================+=======================================+=================+
| Obtain all EVS tags of a tenant.            | GET /v2/{project_id}/os-vendor-tags/{resource_type}                        | -  EVS disk: evs:volumeTags:list      | Y               |
|                                             |                                                                            | -  Backup: evs:backupTags:list        |                 |
|                                             |                                                                            | -  Snapshot: evs:snapshotTags:list    |                 |
+---------------------------------------------+----------------------------------------------------------------------------+---------------------------------------+-----------------+
| Query EVS resources by tag.                 | GET /v2/{project_id}/os-vendor-tags/{resource_type}/resource_instances     | -  EVS disk: evs:volumeTags:get       | Y               |
|                                             |                                                                            | -  Backup: evs:backupTags:get         |                 |
|                                             |                                                                            | -  Snapshot: evs:snapshotTags:get     |                 |
+---------------------------------------------+----------------------------------------------------------------------------+---------------------------------------+-----------------+
| Add or update tags for an EVS resource.     | POST /v2/{project_id}/os-vendor-tags/{resource_type}/{resource_id}         | -  EVS disk: evs:volumeTags:create    | Y               |
|                                             |                                                                            | -  Backup: evs:backupTags:create      |                 |
|                                             |                                                                            | -  Snapshot: evs:snapshotTags:create  |                 |
+---------------------------------------------+----------------------------------------------------------------------------+---------------------------------------+-----------------+
| Obtain tags of an EVS resource.             | GET /v2/{project_id}/os-vendor-tags/{resource_type}/{resource_id}          | -  EVS disk: evs:volumeTags:getById   | Y               |
|                                             |                                                                            | -  Backup: evs:backupTags:getById     |                 |
|                                             |                                                                            | -  Snapshot: evs:snapshotTags:getById |                 |
+---------------------------------------------+----------------------------------------------------------------------------+---------------------------------------+-----------------+
| Reset the tags of an EVS resource.          | PUT /v2/{project_id}/os-vendor-tags/{resource_type}/{resource_id}          | -  EVS disk: evs:volumeTags:update    | Y               |
|                                             |                                                                            | -  Backup: evs:backupTags:update      |                 |
|                                             |                                                                            | -  Snapshot: evs:snapshotTags:update  |                 |
+---------------------------------------------+----------------------------------------------------------------------------+---------------------------------------+-----------------+
| Batch delete the tags for an EVS resource.  | POST /v2/{project_id}/os-vendor-tags/{resource_type}/{resource_id}/action  | -  EVS disk: evs:volumeTags:delete    | Y               |
|                                             |                                                                            |                                       |                 |
|                                             |                                                                            |    evs:volumeTags:getById             |                 |
|                                             |                                                                            |                                       |                 |
|                                             |                                                                            | -  Backup: evs:backupTags:delete      |                 |
|                                             |                                                                            |                                       |                 |
|                                             |                                                                            |    evs:backupTags:getById             |                 |
|                                             |                                                                            |                                       |                 |
|                                             |                                                                            | -  Snapshot: evs:snapshotTags:delete  |                 |
|                                             |                                                                            |                                       |                 |
|                                             |                                                                            |    evs:snapshotTags:getById           |                 |
+---------------------------------------------+----------------------------------------------------------------------------+---------------------------------------+-----------------+
| Delete the tags of an EVS resource by key.  | DELETE /v2/{project_id}/os-vendor-tags/{resource_type}/{resource_id}/{key} | -  EVS disk: evs:volumeTags:getById   | Y               |
|                                             |                                                                            |                                       |                 |
|                                             |                                                                            |    evs:volumeTags:delete              |                 |
|                                             |                                                                            |                                       |                 |
|                                             |                                                                            | -  Backup: evs:backupTags:getById     |                 |
|                                             |                                                                            |                                       |                 |
|                                             |                                                                            |    evs:backupTags:delete              |                 |
|                                             |                                                                            |                                       |                 |
|                                             |                                                                            | -  Snapshot: evs:snapshotTags:getById |                 |
|                                             |                                                                            |                                       |                 |
|                                             |                                                                            |    evs:snapshotTags:delete            |                 |
+---------------------------------------------+----------------------------------------------------------------------------+---------------------------------------+-----------------+
| Update the tags of an EVS resource by key.  | PUT /v2/{project_id}/os-vendor-tags/{resource_type}/{resource_id}/{key}    | -  EVS disk: evs:volumeTags:update    | Y               |
|                                             |                                                                            | -  Backup: evs:backupTags:update      |                 |
|                                             |                                                                            | -  Snapshot: evs:snapshotTags:update  |                 |
+---------------------------------------------+----------------------------------------------------------------------------+---------------------------------------+-----------------+
| Batch delete tags for a specified EVS disk. | POST /v2/{project_id}/os-vendor-volumes/{volume_id}/tags/action            | evs:volumeTags:delete                 | Y               |
+---------------------------------------------+----------------------------------------------------------------------------+---------------------------------------+-----------------+
| Query the tags of an EVS disk.              | GET /v2/{project_id}/os-vendor-volumes/{volume_id}/tags                    | evs:volumeTags:getById                | Y               |
+---------------------------------------------+----------------------------------------------------------------------------+---------------------------------------+-----------------+
| Batch add tags for a specified EVS disk.    | POST /v2/{project_id}/os-vendor-volumes/{volume_id}/tags/action            | evs:volumeTags:create                 | Y               |
+---------------------------------------------+----------------------------------------------------------------------------+---------------------------------------+-----------------+
| Query details of EVS disks by tag.          | POST /v2/{project_id}/os-vendor-volumes/resource_instances/action          | evs:volumeTags:get                    | Y               |
+---------------------------------------------+----------------------------------------------------------------------------+---------------------------------------+-----------------+
| Query tags of an EVS resource by key.       | GET /v2/{project_id}/os-vendor-tags/{resource_type}/{resource_id}/{key}    | evs:volumeTags:getById                | Y               |
+---------------------------------------------+----------------------------------------------------------------------------+---------------------------------------+-----------------+
| Query the number of EVS disks by tag.       | POST /v2/{project_id}/os-vendor-volumes/resource_instances/action          | evs:volumeTags:get                    | Y               |
+---------------------------------------------+----------------------------------------------------------------------------+---------------------------------------+-----------------+

+---------------------------------------------+--------------------------------------------------------------+----------------------------------+-----------------+
| Permission                                  | API                                                          | Action                           | IAM Project     |
|                                             |                                                              |                                  |                 |
|                                             |                                                              |                                  | (Project)       |
+=============================================+==============================================================+==================================+=================+
| Obtain all EVS tags of a tenant.            | GET /v2/{project_id}/cloudvolumes/tags                       | -  EVS disk: evs:volumeTags:list | Y               |
|                                             |                                                              | -  Backup: evs:backupTags:list   |                 |
+---------------------------------------------+--------------------------------------------------------------+----------------------------------+-----------------+
| Batch add tags for a specified EVS disk.    | POST /v2/{project_id}/cloudvolumes/{volume_id}/tags/action   | evs:volumeTags:create            | Y               |
+---------------------------------------------+--------------------------------------------------------------+----------------------------------+-----------------+
| Batch delete tags for a specified EVS disk. | POST /v2/{project_id}/cloudvolumes/{volume_id}/tags/action   | evs:volumeTags:delete            | Y               |
+---------------------------------------------+--------------------------------------------------------------+----------------------------------+-----------------+
| Query the tags of an EVS disk.              | GET /v2/{project_id}/cloudvolumes/{volume_id}/tags           | evs:volumeTags:getById           | Y               |
+---------------------------------------------+--------------------------------------------------------------+----------------------------------+-----------------+
| Query details of EVS disks by tag.          | POST /v2/{project_id}/cloudvolumes/resource_instances/action | evs:volumeTags:get               | Y               |
+---------------------------------------------+--------------------------------------------------------------+----------------------------------+-----------------+

EVS Disk Transfer
-----------------

+-----------------------------------------------------------------------------+---------------------------------------------------------------+----------------------+-----------------+
| Permission                                                                  | API                                                           | Action               | IAM Project     |
|                                                                             |                                                               |                      |                 |
|                                                                             |                                                               |                      | (Project)       |
+=============================================================================+===============================================================+======================+=================+
| Create an EVS disk transfer (OpenStack Cinder API).                         | POST /v2/{project_id}/os-volume-transfer                      | evs:transfers:create | Y               |
+-----------------------------------------------------------------------------+---------------------------------------------------------------+----------------------+-----------------+
| Query all EVS disk transfers of a tenant (OpenStack Cinder API).            | GET /v2/{project_id}/os-volume-transfer                       | evs:transfers:list   | Y               |
+-----------------------------------------------------------------------------+---------------------------------------------------------------+----------------------+-----------------+
| Query details of all EVS disk transfers of a tenant (OpenStack Cinder API). | GET /v2/{project_id}/os-volume-transfer/detail                | evs:transfers:list   | Y               |
+-----------------------------------------------------------------------------+---------------------------------------------------------------+----------------------+-----------------+
| Query details of an EVS disk transfer (OpenStack Cinder API).               | GET /v2/{project_id}/os-volume-transfer/{transfer_id}         | evs:transfers:get    | Y               |
+-----------------------------------------------------------------------------+---------------------------------------------------------------+----------------------+-----------------+
| Accept an EVS disk transfer (OpenStack Cinder API).                         | POST /v2/{project_id}/os-volume-transfer/{transfer_id}/accept | evs:transfers:accept | Y               |
+-----------------------------------------------------------------------------+---------------------------------------------------------------+----------------------+-----------------+
| Delete an EVS disk transfer (OpenStack Cinder API).                         | DELETE /v2/{project_id}/os-volume-transfer/{transfer_id}      | evs:transfers:delete | Y               |
+-----------------------------------------------------------------------------+---------------------------------------------------------------+----------------------+-----------------+
