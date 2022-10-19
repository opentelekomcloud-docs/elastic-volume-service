:original_name: evs_04_0028.html

.. _evs_04_0028:

Tag
===

This topic describes only the authorization information of EVS v2 APIs. For the v3 APIs that provide the same functions as their v2 APIs, their authorization information is the same as that of the v2 APIs.

For example, the v2 API for creating disks is POST /v2/{project_id}/cloudvolumes, and the v3 API for creating disks is POST /v3/{project_id}/cloudvolumes. The authorization information of both APIs is the same.

In the following tables, Y indicates that the item is supported, and × indicates that the item is not supported.

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
