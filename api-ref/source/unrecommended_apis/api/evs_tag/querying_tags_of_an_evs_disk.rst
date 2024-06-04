:original_name: evs_04_3015.html

.. _evs_04_3015:

Querying Tags of an EVS Disk
============================

Function
--------

This API is used to query the tags of the specified EVS disk.

Constraints
-----------

None

URI
---

-  URI format

   GET /v3/{project_id}/os-vendor-volumes/{volume_id}/tags

-  Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   volume_id  Yes       Specifies the disk ID.
   ========== ========= =========================

Request
-------

None

Response
--------

-  Parameter description

   +-----------+--------------------+--------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type               | Description                                                                                                              |
   +===========+====================+==========================================================================================================================+
   | tags      | List<resource_tag> | Specifies the tag list. For details, see :ref:`Parameters in the tags field <evs_04_3015__evs_04_2031_li8528152083214>`. |
   +-----------+--------------------+--------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_3015__evs_04_2031_li8528152083214:

   Parameters in the **tags** field

   ========= ====== ========================
   Parameter Type   Description
   ========= ====== ========================
   key       String Specifies the tag key.
   value     String Specifies the tag value.
   ========= ====== ========================

-  Example response

   .. code-block::

      {
          "tags": [
              {
                  "value": "value1",
                  "key": "key1"
              },
              {
                  "value": "value2",
                  "key": "key2"
              }
          ]
      }

Status Codes
------------

-  Normal

   200

Error Codes
-----------

For details, see :ref:`Error Codes <evs_04_0038>`.
