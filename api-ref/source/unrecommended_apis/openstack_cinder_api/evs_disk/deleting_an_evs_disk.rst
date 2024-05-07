:original_name: evs_04_3030.html

.. _evs_04_3030:

Deleting an EVS Disk
====================

Function
--------

This API is used to delete an EVS disk.

URI
---

-  URI format

   DELETE /v3/{project_id}/volumes/{volume_id}

-  Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   volume_id  Yes       Specifies the disk ID.
   ========== ========= =========================

-  Request filter parameters

   +-----------+---------+-----------+---------------------------------------------------------------------------------------------+
   | Parameter | Type    | Mandatory | Description                                                                                 |
   +===========+=========+===========+=============================================================================================+
   | cascade   | Boolean | No        | Specifies to delete all snapshots associated with the disk. The default value is **false**. |
   +-----------+---------+-----------+---------------------------------------------------------------------------------------------+

Request
-------

The following example shows how to delete a disk and all its snapshots.

-  Example request

   .. code-block:: text

      DELETE https://{endpoint}/v3/{project_id}/volumes/{volume_id}?cascade=true

Response
--------

-  Response parameters

   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                                                                      |
   +===========+========+==================================================================================================================================================+
   | error     | Object | The error message returned if an error occurs. For details, see :ref:`Parameters in the error field <evs_04_3030__evs_04_2066_li0419202382514>`. |
   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_3030__evs_04_2066_li0419202382514:

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

   In the preceding example, **error** indicates a general error, for example, **badrequest** or **itemNotFound**. An example is provided as follows:

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
