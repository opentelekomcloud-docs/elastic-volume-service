:original_name: evs_04_2025.html

.. _evs_04_2025:

Deleting Tags of an EVS Resource by Key
=======================================

Function
--------

This API is used to delete tags of an EVS resource by key.

Constraints
-----------

None

URI
---

-  URI format

   DELETE /v2/{project_id}/os-vendor-tags/{resource_type}/{resource_id}/{key}

-  Parameter description

   +---------------+-----------+-------------------------------------------------------------------------------------------+
   | Parameter     | Mandatory | Description                                                                               |
   +===============+===========+===========================================================================================+
   | project_id    | Yes       | Specifies the project ID.                                                                 |
   +---------------+-----------+-------------------------------------------------------------------------------------------+
   | resource_type | Yes       | Specifies the resource type. The value can be **volumes**, **snapshots**, or **backups**. |
   +---------------+-----------+-------------------------------------------------------------------------------------------+
   | resource_id   | Yes       | Specifies the resource ID. The value can be the ID of a disk, snapshot, or backup.        |
   +---------------+-----------+-------------------------------------------------------------------------------------------+
   | key           | Yes       | Specifies the key of the tag.                                                             |
   +---------------+-----------+-------------------------------------------------------------------------------------------+

Request
-------

None

Response
--------

-  Parameter description

   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                                                                      |
   +===========+========+==================================================================================================================================================+
   | error     | Object | Specifies the error message returned when an error occurs. For details, see :ref:`Parameters in the error field <evs_04_2025__li0419202382514>`. |
   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_2025__li0419202382514:

   Parameters in the **error** field

   +-----------------------+-----------------------+-------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                             |
   +=======================+=======================+=========================================================================+
   | message               | String                | Specifies the error message returned when an error occurs.              |
   +-----------------------+-----------------------+-------------------------------------------------------------------------+
   | code                  | String                | Specifies the error code returned when an error occurs.                 |
   |                       |                       |                                                                         |
   |                       |                       | For details about the error code, see :ref:`Error Codes <evs_04_0038>`. |
   +-----------------------+-----------------------+-------------------------------------------------------------------------+

-  Example response

   None

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
              "message": "XXXX",
              "code": "XXX"
          }
      }

Status Codes
------------

-  Normal

   200

Error Codes
-----------

For details, see :ref:`Error Codes <evs_04_0038>`.
