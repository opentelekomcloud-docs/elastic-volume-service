:original_name: evs_04_2026.html

.. _evs_04_2026:

Obtaining All Tags of an EVS Resource Type
==========================================

Function
--------

This API is used to obtain all tags of an EVS resource type.

Constraints
-----------

None

URI
---

-  URI format

   GET /v2/{project_id}/os-vendor-tags/{resource_type}

-  Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   ========== ========= =========================

Request
-------

None

Response
--------

-  Parameter description

   ========= ====== ==================================================
   Parameter Type   Description
   ========= ====== ==================================================
   tags      Object Specifies the tag information about all EVS disks.
   ========= ====== ==================================================

-  Example response

   .. code-block::

      {
          "tags": {
              "key_0": [
                  "value_0"
              ],
              "key_1": [
                  "value_1",
                  "value_2",
                  "value_3",
                  "value_4"
              ]
          }
      }

Status Codes
------------

-  Normal

   200

Error Codes
-----------

For details, see :ref:`Error Codes <evs_04_0038>`.
