:original_name: evs_04_2008.html

.. _evs_04_2008:

Deleting an EVS Disk
====================

Function
--------

This API is used to delete an EVS disk.

URI
---

-  URI format

   DELETE /v2/{project_id}/cloudvolumes/{volume_id}

-  Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   volume_id  Yes       Specifies the disk ID.
   ========== ========= =========================

Request
-------

-  Example request

   .. code-block:: text

      DELETE https://{endpoint}/v2/{project_id}/cloudvolumes/b104b8db-170d-441b-897a-3c8ba9c5a214

Response
--------

-  Parameter description

   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                      |
   +=======================+=======================+==================================================================================================================================================+
   | job_id                | String                | Specifies the task ID.                                                                                                                           |
   |                       |                       |                                                                                                                                                  |
   |                       |                       | .. note::                                                                                                                                        |
   |                       |                       |                                                                                                                                                  |
   |                       |                       |    For details about how to query the task status, see :ref:`Querying Task Status <evs_04_0054>`.                                                |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | error                 | Object                | Specifies the error message returned when an error occurs. For details, see :ref:`Parameters in the error field <evs_04_2008__li0419202382514>`. |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_2008__li0419202382514:

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
          "job_id": "70a599e0-31e7-49b7-b260-868f441e862b"
      }

   or

   .. code-block::

      {
          "error": {
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
