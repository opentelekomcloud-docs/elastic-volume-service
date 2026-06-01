:original_name: evs_04_2037.html

.. _evs_04_2037:

Batch Deleting Tags for an EVS Resource (Deprecated)
====================================================

Function
--------

This API is used to batch delete tags for an EVS resource.

.. important::

   This API has been deprecated. Use another API. For details, see :ref:`Batch Deleting Tags for the Specified EVS Disk <evs_04_3013>`.

Constraints
-----------

None

URI
---

-  URI format

   POST /v2/{project_id}/os-vendor-tags/{resource_type}/{resource_id}/action

-  Parameter description

   +---------------+-----------+---------------------------------------------------------------------------------+
   | Parameter     | Mandatory | Description                                                                     |
   +===============+===========+=================================================================================+
   | project_id    | Yes       | The project ID.                                                                 |
   +---------------+-----------+---------------------------------------------------------------------------------+
   | resource_type | Yes       | The resource type. The value can be **volumes**, **snapshots**, or **backups**. |
   +---------------+-----------+---------------------------------------------------------------------------------+
   | resource_id   | Yes       | The resource ID.                                                                |
   +---------------+-----------+---------------------------------------------------------------------------------+

Request
-------

-  Parameter description

   ============== ====== ========= ==============================
   Parameter      Type   Mandatory Description
   ============== ====== ========= ==============================
   os-delete_tags Object Yes       The key-value pair of the tag.
   ============== ====== ========= ==============================

-  Description of the request header parameter

   +--------------+--------+-----------+--------------------------------------------------+
   | Parameter    | Type   | Mandatory | Description                                      |
   +==============+========+===========+==================================================+
   | Content-Type | Object | Yes       | The type. The value can be **application/json**. |
   +--------------+--------+-----------+--------------------------------------------------+

-  Example request

   .. code-block::

      {
          "os-delete_tags": {
              "key_0": "value_0",
              "key_1": "value_1"
          }
      }

Response
--------

None

Status Codes
------------

-  Normal

   200

Error Codes
-----------

For details, see :ref:`Error Codes <evs_04_0038>`.
