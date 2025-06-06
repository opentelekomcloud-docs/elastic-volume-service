:original_name: evs_04_2085.html

.. _evs_04_2085:

Setting Read-Only Flag for an EVS Disk
======================================

Function
--------

This API is used to set the read-only flag for the EVS disk.

URI
---

-  URI format

   POST /v2/{project_id}/volumes/{volume_id}/action

-  Parameter description

   ========== ========= ===============
   Parameter  Mandatory Description
   ========== ========= ===============
   project_id Yes       The project ID.
   volume_id  Yes       The disk ID.
   ========== ========= ===============

Request
-------

-  Parameter description

   +-------------------------+--------+-----------+----------------------------------------------------------------------------------------------------------------------------------+
   | Parameter               | Type   | Mandatory | Description                                                                                                                      |
   +=========================+========+===========+==================================================================================================================================+
   | os-update_readonly_flag | Object | Yes       | The disk read-only flag. For details, see :ref:`Parameter in the os-update_readonly_flag field <evs_04_2085__li55520608111457>`. |
   +-------------------------+--------+-----------+----------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_2085__li55520608111457:

   Parameter in the **os-update_readonly_flag** field

   +-----------------+-----------------+-----------------+------------------------------------------+
   | Parameter       | Type            | Mandatory       | Description                              |
   +=================+=================+=================+==========================================+
   | readonly        | Boolean         | Yes             | The read-only flag.                      |
   |                 |                 |                 |                                          |
   |                 |                 |                 | -  **true**: The disk is read-only.      |
   |                 |                 |                 | -  **false**: The disk is not read-only. |
   +-----------------+-----------------+-----------------+------------------------------------------+

-  Example request

   .. code-block::

      {
          "os-update_readonly_flag": {
              "readonly": true
          }
      }

Response
--------

-  Parameter description

   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                                                          |
   +===========+========+======================================================================================================================================+
   | error     | Object | The error message returned if an error occurs. For details, see :ref:`Parameters in the error field <evs_04_2085__li0419202382514>`. |
   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_2085__li0419202382514:

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

   202

Error Codes
-----------

For details, see :ref:`Error Codes <evs_04_0038>`.
