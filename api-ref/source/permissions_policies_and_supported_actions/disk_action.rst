:original_name: evs_04_0026.html

.. _evs_04_0026:

Disk Action
===========

This topic describes only the authorization information of EVS v2 APIs. For the v3 APIs that provide the same functions as their v2 APIs, their authorization information is the same as that of the v2 APIs.

For example, the v2 API for creating disks is POST /v2/{project_id}/cloudvolumes, and the v3 API for creating disks is POST /v3/{project_id}/cloudvolumes. The authorization information of both APIs is the same.

In the following tables, Y indicates that the item is supported, and × indicates that the item is not supported.

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
