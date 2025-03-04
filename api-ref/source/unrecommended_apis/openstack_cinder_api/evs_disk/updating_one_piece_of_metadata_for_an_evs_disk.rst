:original_name: evs_04_3042.html

.. _evs_04_3042:

Updating One Piece of Metadata for an EVS Disk
==============================================

Function
--------

This API is used to update one piece of the EVS disk metadata.

URI
---

-  URI format

   PUT /v3/{project_id}/volumes/{volume_id}/metadata/{key}

-  Parameter description

   ========== ========= ===============================================
   Parameter  Mandatory Description
   ========== ========= ===============================================
   project_id Yes       The project ID.
   volume_id  Yes       The disk ID.
   key        Yes       The key of the piece of metadata to be updated.
   ========== ========= ===============================================

Request
-------

-  Parameter description

   +-----------+--------+-----------+-----------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Mandatory | Description                                                                                                                       |
   +===========+========+===========+===================================================================================================================================+
   | meta      | Object | Yes       | The disk metadata to be updated. For details, see :ref:`Parameter in the meta field <evs_04_3042__evs_04_2078_li54973602211845>`. |
   +-----------+--------+-----------+-----------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_3042__evs_04_2078_li54973602211845:

   Parameter in the **meta** field

   +-----------+--------+-----------+------------------------------------------------------------+
   | Parameter | Type   | Mandatory | Description                                                |
   +===========+========+===========+============================================================+
   | key_val   | String | No        | A piece of metadata, which is made up of a key-value pair. |
   +-----------+--------+-----------+------------------------------------------------------------+

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
   | meta      | Object | The piece of the disk metadata, which is made up of a key-value pair.                                                                            |
   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | error     | Object | The error message returned if an error occurs. For details, see :ref:`Parameters in the error field <evs_04_3042__evs_04_2078_li0419202382514>`. |
   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_3042__evs_04_2078_li0419202382514:

   Parameters in the **error** field

   +-----------------------+-----------------------+-------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                             |
   +=======================+=======================+=========================================================================+
   | message               | String                | The error message returned if an error occurs.                          |
   +-----------------------+-----------------------+-------------------------------------------------------------------------+
   | code                  | String                | The error code returned if an error occurs.                             |
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
