:original_name: evs_04_0029.html

.. _evs_04_0029:

Disk Transfer
=============

This topic describes only the authorization information of EVS v2 APIs. For the v3 APIs that provide the same functions as their v2 APIs, their authorization information is the same as that of the v2 APIs.

For example, the v2 API for creating disks is POST /v2/{project_id}/cloudvolumes, and the v3 API for creating disks is POST /v3/{project_id}/cloudvolumes. The authorization information of both APIs is the same.

In the following tables, Y indicates that the item is supported, and x indicates that the item is not supported.

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
