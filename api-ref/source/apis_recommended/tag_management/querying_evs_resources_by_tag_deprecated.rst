:original_name: evs_04_2042.html

.. _evs_04_2042:

Querying EVS Resources by Tag (Deprecated)
==========================================

Function
--------

This API is used to query the EVS resources by tag.

.. important::

   This API has been deprecated. Use another API. For details, see :ref:`Querying Details of EVS Disks by Tag <evs_04_3018>`.

Constraints
-----------

None

URI
---

-  URI format

   GET /v2/{project_id}/os-vendor-tags/{resource_type}/resource_instances

   Examples:

   -  https://{{evs_url}}/v2/{{project_id}}/os-vendor-tags/volumes/resource_instances?tags={'test':['test']}
   -  https://{{evs_url}}/v2/{{project_id}}/os-vendor-tags/volumes/resource_instances

-  Parameter description

   +---------------+-----------+---------------------------------------------------------------------------------+
   | Parameter     | Mandatory | Description                                                                     |
   +===============+===========+=================================================================================+
   | project_id    | Yes       | The project ID.                                                                 |
   +---------------+-----------+---------------------------------------------------------------------------------+
   | resource_type | Yes       | The resource type. The value can be **volumes**, **snapshots**, or **backups**. |
   +---------------+-----------+---------------------------------------------------------------------------------+

-  Request filter parameters

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Type            | Mandatory       | Description                                                                                                                                                                                                     |
   +=================+=================+=================+=================================================================================================================================================================================================================+
   | tags            | String          | No              | Specifies to query the EVS resources owning the tags in the filtering tag.                                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                                                                 |
   |                 |                 |                 | For example, if the filtering tag is **tags={'a':['b', 'c'], 'd':['e']}**, EVS resources owning tags (key is **a** and value is **b** or **c**) and tags (key is **d** and value is **e**) are queried.         |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tags_any        | String          | No              | Specifies to query EVS resources owing one of the tags in the filtering tag.                                                                                                                                    |
   |                 |                 |                 |                                                                                                                                                                                                                 |
   |                 |                 |                 | For example, if the filtering tag is **tags_any={'a':['b', 'c'], 'd':['e']}**, EVS resources owning tags (key is **a** and value is **b** or **c**) or tags (key is **d** and value is **e**) are queried.      |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | not_tags        | String          | No              | Specifies to query EVS resources not owning the tags in the filtering tag.                                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                                                                 |
   |                 |                 |                 | For example, if the filtering tag is **not_tags={'a':['b', 'c'], 'd':['e']}**, EVS resources not owning tags (key is **a** and value is **b** or **c**) and tags (key is **d** and value is **e**) are queried. |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | not_tags_any    | String          | No              | Specifies to query EVS resources not owning one of the tags in the filtering tag.                                                                                                                               |
   |                 |                 |                 |                                                                                                                                                                                                                 |
   |                 |                 |                 | For example, if the filtering tag is **not_tags={'a':['b', 'c'], 'd':['e']}**, EVS resources not owning tags (key is **a** and value is **b** or **c**) or tags (key is **d** and value is **e**) are queried.  |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request
-------

None

Response
--------

-  Parameter description

   =========== ======= ==================
   Parameter   Type    Description
   =========== ======= ==================
   total_count Integer The disk quantity.
   resources   list    The disk list.
   =========== ======= ==================

-  Example response

   .. code-block::

      {
          "total_count": 2,
          "resources": [
              {
                  "resource_name": null,
                  "resource_detail": {
                      "status": "available",
                      "description": null,
                      "availability_zone": "az-dc-1",
                      "updated_at": "2017-07-26T08:14:07.857625",
                      "source_volid": null,
                      "snapshot_id": null,
                      "id": "47cc4949-447a-43dc-b482-a1d7917fef69",
                      "size": 45,
                      "name": null,
                      "bootable": "true",
                      "created_at": "2017-07-26T08:09:39.787432",
                      "multiattach": false
                  },
                  "tags": {
                      "a": "c",
                      "d": "e"
                  },
                  "resource_id": "47cc4949-447a-43dc-b482-a1d7917fef69"
              },
              {
                  "resource_name": null,
                  "resource_detail": {
                      "status": "available",
                      "description": null,
                      "availability_zone": "az-dc-1",
                      "updated_at": "2017-07-26T08:02:11.250455",
                      "source_volid": null,
                      "snapshot_id": null,
                      "id": "588e94ef-eb2d-4895-a692-18163a7eeddc",
                      "size": 100,
                      "name": null,
                      "bootable": "false",
                      "created_at": "2017-07-26T08:00:51.563309",
                      "multiattach": false
                  },
                  "tags": {
                      "a": "c",
                      "d": "e"
                  },
                  "resource_id": "588e94ef-eb2d-4895-a692-18163a7eeddc"
              }
          ]
      }

   or

   .. code-block::

      {
          "error": {
              "message": "XXXX",
              "code": "XXX"
          }
      }

   In the preceding example, **error** indicates a general error, for example, **badRequest** or **itemNotFound**. An example is provided as follows:

   .. code-block::

      {
          "computeFault": {
              "message": "The server has either erred or is incapable of performing the requested operation.",
              "code": 500
          }
      }

Status Codes
------------

-  Normal

   200

Error Codes
-----------

For details, see :ref:`Error Codes <evs_04_0038>`.
