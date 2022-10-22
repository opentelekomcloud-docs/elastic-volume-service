:original_name: evs_04_2101.html

.. _evs_04_2101:

Updating One Piece of Metadata for an EVS Snapshot
==================================================

Function
--------

This API is used to update one piece of the EVS snapshot metadata.

URI
---

-  URI format

   PUT /v2/{project_id}/snapshots/{snapshot_id}/metadata/{key}

-  Parameter description

   +-------------+-----------+-----------------------------------------------------------+
   | Parameter   | Mandatory | Description                                               |
   +=============+===========+===========================================================+
   | project_id  | Yes       | Specifies the project ID.                                 |
   +-------------+-----------+-----------------------------------------------------------+
   | snapshot_id | Yes       | Specifies the snapshot ID.                                |
   +-------------+-----------+-----------------------------------------------------------+
   | key         | Yes       | Specifies the key of the piece of metadata to be updated. |
   +-------------+-----------+-----------------------------------------------------------+

Request
-------

-  Parameter description

   +-----------+--------+-----------+--------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Mandatory | Description                                                                                                                    |
   +===========+========+===========+================================================================================================================================+
   | meta      | Object | Yes       | Specifies the metadata to be updated. For details, see :ref:`Parameter in the metadata field <evs_04_2101__li54973602211845>`. |
   +-----------+--------+-----------+--------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_2101__li54973602211845:

   Parameter in the **metadata** field

   +-----------+--------+-----------+----------------------------------------------------------------------+
   | Parameter | Type   | Mandatory | Description                                                          |
   +===========+========+===========+======================================================================+
   | key_val   | String | No        | Specifies a piece of metadata, which is made up of a key-value pair. |
   +-----------+--------+-----------+----------------------------------------------------------------------+

-  Example request

   .. code-block::

      {
          "meta": {
              "key1": "value1"
          }
      }

Response
--------

-  Parameter description

   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                                                                      |
   +===========+========+==================================================================================================================================================+
   | meta      | Object | Specifies a piece of snapshot metadata, which is made up of a key-value pair.                                                                    |
   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | error     | Object | Specifies the error message returned when an error occurs. For details, see :ref:`Parameters in the error field <evs_04_2101__li0419202382514>`. |
   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_2101__li0419202382514:

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

   .. code-block::

      {
          "meta": {
              "key1": "value1"
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