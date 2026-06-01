:original_name: evs_04_3062.html

.. _evs_04_3062:

Adding Metadata of an EVS Snapshot
==================================

Function
--------

This API is used to add the metadata of an EVS snapshot.

URI
---

-  URI format

   POST /v3/{project_id}/snapshots/{snapshot_id}/metadata

-  Parameter description

   =========== ========= ================
   Parameter   Mandatory Description
   =========== ========= ================
   project_id  Yes       The project ID.
   snapshot_id Yes       The snapshot ID.
   =========== ========= ================

Request
-------

-  Parameter description

   +-----------+--------+-----------+--------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Mandatory | Description                                                                                                                    |
   +===========+========+===========+================================================================================================================================+
   | metadata  | Object | Yes       | The metadata to be added. For details, see :ref:`Parameter in the metadata field <evs_04_3062__evs_04_2099_li39191951112814>`. |
   +-----------+--------+-----------+--------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_3062__evs_04_2099_li39191951112814:

   Parameter in the **metadata** field

   +-----------+--------+-----------+--------------------------------------------------------------------------------+
   | Parameter | Type   | Mandatory | Description                                                                    |
   +===========+========+===========+================================================================================+
   | key_val   | String | No        | The metadata information, which is made up of one or multiple key-value pairs. |
   +-----------+--------+-----------+--------------------------------------------------------------------------------+

-  Example request

   .. code-block::

      {
          "metadata": {
              "key1": "value1",
              "key2": "value2"
          }
      }

Response
--------

-  Parameter description

   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                                                                      |
   +===========+========+==================================================================================================================================================+
   | metadata  | Object | The snapshot metadata, which is made up of key-value pairs.                                                                                      |
   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | error     | Object | The error message returned if an error occurs. For details, see :ref:`Parameters in the error field <evs_04_3062__evs_04_2099_li0419202382514>`. |
   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_3062__evs_04_2099_li0419202382514:

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
