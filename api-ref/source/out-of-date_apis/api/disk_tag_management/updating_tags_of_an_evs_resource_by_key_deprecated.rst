:original_name: evs_04_2041.html

.. _evs_04_2041:

Updating Tags of an EVS Resource by Key (Deprecated)
====================================================

Function
--------

This API is used to update tags of an EVS resource by key.

.. important::

   This API has been deprecated. Use another API. For details, see :ref:`Batch Adding Tags for the Specified EVS Disk <evs_04_3011>`.

Constraints
-----------

-  A tag is composed of a key-value pair.

   -  Key:

      -  Must be unique for each resource.
      -  Can contain a maximum of 36 characters.
      -  Can contain only digits, letters, hyphens (-), and underscores (_).

   -  Value:

      -  Can contain a maximum of 43 characters.
      -  Can contain only digits, letters, hyphens (-), and underscores (_).

-  A maximum of 10 tags can be created for an EVS resource.

URI
---

-  URI format

   PUT /v2/{project_id}/os-vendor-tags/{resource_type}/{resource_id}/{key}

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
   | key           | Yes       | The key of the tag.                                                             |
   +---------------+-----------+---------------------------------------------------------------------------------+

Request
-------

-  Parameter description

   ========= ====== ========= ==============================
   Parameter Type   Mandatory Description
   ========= ====== ========= ==============================
   tag       Object Yes       The key-value pair of the tag.
   ========= ====== ========= ==============================

-  Description of the request header parameter

   +--------------+--------+-----------+--------------------------------------------------+
   | Parameter    | Type   | Mandatory | Description                                      |
   +==============+========+===========+==================================================+
   | Content-Type | Object | Yes       | The type. The value can be **application/json**. |
   +--------------+--------+-----------+--------------------------------------------------+

-  Example request

   .. code-block::

      {
          "tag": {
              "key_0": "value_0"
          }
      }

Response
--------

-  Parameter description

   ========= ====== ==============================
   Parameter Type   Description
   ========= ====== ==============================
   tag       Object The key-value pair of the tag.
   ========= ====== ==============================

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
            ta  "message": "XXXX",
              "code": "XXX"
          }
      }

   In the preceding example, **error** indicates a general error, for example, **badRequest** or **itemNotFound**. An example is provided as follows:

   .. code-block::

      {
          "badRequest": {
              "message": "Request body and URI mismatch",
              "code": 400
          }
      }

Status Codes
------------

-  Normal

   200

Error Codes
-----------

For details, see :ref:`Error Codes <evs_04_0038>`.
