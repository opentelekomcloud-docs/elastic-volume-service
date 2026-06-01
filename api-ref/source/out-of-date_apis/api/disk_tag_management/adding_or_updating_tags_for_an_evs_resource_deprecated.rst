:original_name: evs_04_2036.html

.. _evs_04_2036:

Adding or Updating Tags for an EVS Resource (Deprecated)
========================================================

Function
--------

This API is used to add or update tags for an EVS resource.

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

   POST /v2/{project_id}/os-vendor-tags/{resource_type}/{resource_id}

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

   ========= ====== ========= ==============================
   Parameter Type   Mandatory Description
   ========= ====== ========= ==============================
   tags      Object Yes       The key-value pair of the tag.
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
           "tags" : {
              "key_0" : "value_0",
              "key_1" : "value_1"
           }
      }

.. note::

   If the request body contains an existing key of the resource, the original tag containing this key will be overwritten. For example, **"key_1":"val_1"** is an existing tag of the resource. If the request body contains **"key_1":"val_11"**, the tag of **key_1** for this resource is **"key_1":"val_11"**.

Response
--------

-  Parameter description

   ========= ====== ==============================
   Parameter Type   Description
   ========= ====== ==============================
   tags      Object The key-value pair of the tag.
   ========= ====== ==============================

-  Example response

   .. code-block::

      {
           "tags" : {
              "key_0" : "value_0",
              "key_1" : "value_1"
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
          "badRequest": {
              "message": "Invalid tags: Tags property value contains invalid characters.",
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
