:original_name: evs_04_2100.html

.. _evs_04_2100:

Querying Metadata of an EVS Snapshot
====================================

Function
--------

This API is used to query the metadata of an EVS snapshot.

URI
---

-  URI format

   GET /v2/{project_id}/snapshots/{snapshot_id}/metadata

-  Parameter description

   =========== ========= ==========================
   Parameter   Mandatory Description
   =========== ========= ==========================
   project_id  Yes       Specifies the project ID.
   snapshot_id Yes       Specifies the snapshot ID.
   =========== ========= ==========================

Request
-------

-  Example request

   .. code-block:: text

      GET https://{endpoint}/v2/{project_id}/snapshots/f9faf7df-fdc1-4093-9ef3-5cba06eef995/metadata

Response
--------

-  Parameter description

   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                      |
   +=======================+=======================+==================================================================================================================================================+
   | metadata              | Object                | Specifies the snapshot metadata, which is made up of key-value pairs.                                                                            |
   |                       |                       |                                                                                                                                                  |
   |                       |                       | If **metadata** contains the **\__system__enableActive** field, the snapshot is automatically created during the backup of a server.             |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | error                 | Object                | Specifies the error message returned when an error occurs. For details, see :ref:`Parameters in the error field <evs_04_2100__li0419202382514>`. |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_2100__li0419202382514:

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
          "metadata": {
              "key1": "value1",
              "key2": "value2"
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
