:original_name: evs_04_0024.html

.. _evs_04_0024:

API Version Query
=================

This topic describes only the authorization information of EVS v2 APIs. For the v3 APIs that provide the same functions as their v2 APIs, their authorization information is the same as that of the v2 APIs.

For example, the v2 API for creating disks is POST /v2/{project_id}/cloudvolumes, and the v3 API for creating disks is POST /v3/{project_id}/cloudvolumes. The authorization information of both APIs is the same.

In the following tables, Y indicates that the item is supported, and x indicates that the item is not supported.

+-----------------------------------------------+--------------------+-----------------+-----------------+
| Permission                                    | API                | Action          | IAM Project     |
|                                               |                    |                 |                 |
|                                               |                    |                 | (Project)       |
+===============================================+====================+=================+=================+
| Query API versions (OpenStack Cinder API).    | GET /              | None            | Y               |
+-----------------------------------------------+--------------------+-----------------+-----------------+
| Query the API version (OpenStack Cinder API). | GET /{api_version} | None            | Y               |
+-----------------------------------------------+--------------------+-----------------+-----------------+

.. note::

   If **Action** is **None**, no authorization is required.
