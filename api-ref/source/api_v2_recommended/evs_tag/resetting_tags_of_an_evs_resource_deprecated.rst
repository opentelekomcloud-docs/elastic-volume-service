:original_name: evs_04_2040.html

.. _evs_04_2040:

Resetting Tags of an EVS Resource (Deprecated)
==============================================

Function
--------

This API is used to reset the tags of an EVS resource, and the existing tags will be deleted.

.. important::

   This API call exists for compatibility reasons only and has been deprecated.

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

   PUT /v2/{project_id}/os-vendor-tags/{resource_type}/{resource_id}

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

Request
-------

-  Parameter description

   ========= ====== ========= ========================================
   Parameter Type   Mandatory Description
   ========= ====== ========= ========================================
   tags      Object Yes       Specifies the key-value pair of the tag.
   ========= ====== ========= ========================================

-  Description of the request header parameter

   +--------------+--------+-----------+------------------------------------------------------------+
   | Parameter    | Type   | Mandatory | Description                                                |
   +==============+========+===========+============================================================+
   | Content-Type | Object | Yes       | Specifies the type. The value can be **application/json**. |
   +--------------+--------+-----------+------------------------------------------------------------+

-  Example request

   .. code-block::

      {
          "tags": {
              "key_new": "value_new"
          }
      }

Response
--------

-  Parameter description

   ========= ====== ========================================
   Parameter Type   Description
   ========= ====== ========================================
   tags      Object Specifies the key-value pair of the tag.
   ========= ====== ========================================

-  Example response

   .. code-block::

      {
          "tags": {
              "key_new": "value_new"
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
              "message": "Invalid tags: Tags property key contains invalid characters.",
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
