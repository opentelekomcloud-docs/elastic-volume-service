:original_name: evs_04_2039.html

.. _evs_04_2039:

Querying Tags of an EVS Resource by Key (Deprecated)
====================================================

Function
--------

This API is used to query tags of an EVS resource by key.

.. important::

   This API has been deprecated. Use another API. For details, see :ref:`Querying Tags of an EVS Disk <evs_04_3015>`.

Constraints
-----------

None

URI
---

-  URI format

   GET /v2/{project_id}/os-vendor-tags/{resource_type}/{resource_id}/{key}

-  Parameter description

   +---------------+-----------+-------------------------------------------------------------------------------------------+
   | Parameter     | Mandatory | Description                                                                               |
   +===============+===========+===========================================================================================+
   | project_id    | Yes       | Specifies the project ID.                                                                 |
   +---------------+-----------+-------------------------------------------------------------------------------------------+
   | resource_type | Yes       | Specifies the resource type. The value can be **volumes**, **snapshots**, or **backups**. |
   +---------------+-----------+-------------------------------------------------------------------------------------------+
   | resource_id   | Yes       | Specifies the resource ID.                                                                |
   +---------------+-----------+-------------------------------------------------------------------------------------------+
   | key           | Yes       | Specifies the key of the tag.                                                             |
   +---------------+-----------+-------------------------------------------------------------------------------------------+

Request
-------

None

Response
--------

-  Parameter description

   ========= ====== ========================================
   Parameter Type   Description
   ========= ====== ========================================
   tag       Object Specifies the key-value pair of the tag.
   ========= ====== ========================================

-  Example response

   .. code-block::

      {
          "tag": {
              "key_0": "value_0"
          }
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
          "itemNotFound": {
              "message": "Tags item was not found",
              "code": 404
          }
      }

Status Codes
------------

-  Normal

   200

Error Codes
-----------

For details, see :ref:`Error Codes <evs_04_0038>`.
