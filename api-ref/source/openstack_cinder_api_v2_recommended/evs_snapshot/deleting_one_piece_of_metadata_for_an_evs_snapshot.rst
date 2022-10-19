:original_name: evs_04_2104.html

.. _evs_04_2104:

Deleting One Piece of Metadata for an EVS Snapshot
==================================================

Function
--------

This API is used to delete one piece of the EVS snapshot metadata.

URI
---

-  URI format

   DELETE /v2/{project_id}/snapshots/{snapshot_id}/metadata/{key}

-  Parameter description

   +-------------+-----------+-----------------------------------------------------------+
   | Parameter   | Mandatory | Description                                               |
   +=============+===========+===========================================================+
   | project_id  | Yes       | Specifies the project ID.                                 |
   +-------------+-----------+-----------------------------------------------------------+
   | snapshot_id | Yes       | Specifies the snapshot ID.                                |
   +-------------+-----------+-----------------------------------------------------------+
   | key         | Yes       | Specifies the key of the piece of metadata to be deleted. |
   +-------------+-----------+-----------------------------------------------------------+

Request
-------

-  Example request

   .. code-block:: text

      DELETE https://{endpoint}/v2/{project_id}/snapshots/f9faf7df-fdc1-4093-9ef3-5cba06eef995/metadata/value1

Response
--------

-  Parameter description

   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                                                                      |
   +===========+========+==================================================================================================================================================+
   | error     | Object | Specifies the error message returned when an error occurs. For details, see :ref:`Parameters in the error field <evs_04_2104__li0419202382514>`. |
   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_2104__li0419202382514:

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
