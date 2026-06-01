:original_name: evs_04_3067.html

.. _evs_04_3067:

Deleting One Piece of Metadata for an EVS Snapshot
==================================================

Function
--------

This API is used to delete one piece of the EVS snapshot metadata.

URI
---

-  URI format

   DELETE /v3/{project_id}/snapshots/{snapshot_id}/metadata/{key}

-  Parameter description

   =========== ========= ======================================
   Parameter   Mandatory Description
   =========== ========= ======================================
   project_id  Yes       The project ID.
   snapshot_id Yes       The snapshot ID.
   key         Yes       The key of the metadata to be deleted.
   =========== ========= ======================================

Request
-------

-  Example request

   .. code-block:: text

      DELETE https://{endpoint}/v3/{project_id}/snapshots/f9faf7df-fdc1-4093-9ef3-5cba06eef995/metadata/value1

Response
--------

-  Parameter description

   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                                                                      |
   +===========+========+==================================================================================================================================================+
   | error     | Object | The error message returned if an error occurs. For details, see :ref:`Parameters in the error field <evs_04_3067__evs_04_2104_li0419202382514>`. |
   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_3067__evs_04_2104_li0419202382514:

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

   200

Error Codes
-----------

For details, see :ref:`Error Codes <evs_04_0038>`.
