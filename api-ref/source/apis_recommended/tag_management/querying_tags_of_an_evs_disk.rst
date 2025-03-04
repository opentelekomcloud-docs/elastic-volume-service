:original_name: evs_04_2031.html

.. _evs_04_2031:

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

   GET /v2/{project_id}/os-vendor-volumes/{volume_id}/tags

-  Parameter description

   ========== ========= ===============
   Parameter  Mandatory Description
   ========== ========= ===============
   project_id Yes       The project ID.
   volume_id  Yes       The disk ID.
   ========== ========= ===============

Request
-------

None

Response
--------

-  Parameter description

   +-----------+--------------------+------------------------------------------------------------------------------------------------------------+
   | Parameter | Type               | Description                                                                                                |
   +===========+====================+============================================================================================================+
   | tags      | List<resource_tag> | The tag list. For details, see :ref:`Parameters in the resource_tag field <evs_04_2031__li8528152083214>`. |
   +-----------+--------------------+------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_2031__li8528152083214:

   Parameters in the **resource_tag** field

   ========= ====== ==============
   Parameter Type   Description
   ========= ====== ==============
   key       String The tag key.
   value     String The tag value.
   ========= ====== ==============

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
