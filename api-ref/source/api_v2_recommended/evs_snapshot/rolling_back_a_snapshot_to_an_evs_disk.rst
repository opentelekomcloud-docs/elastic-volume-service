:original_name: evs_04_2022.html

.. _evs_04_2022:

Rolling Back a Snapshot to an EVS Disk
======================================

Function
--------

This API is used to roll back a snapshot to an EVS disk.

Constraints
-----------

-  When you roll back a snapshot to a disk, you can only roll back the snapshot to the source disk. Rollback to a specified disk is not supported.
-  You can roll back a disk from a snapshot only when the disk is in the **available** or **error_rollbacking** state.
-  Snapshots whose names started with prefix **autobk_snapshot\_** are automatically created by the system during backup creations. Do not use these snapshots to roll back the disk data.

URI
---

-  URI format

   POST /v2/{project_id}/os-vendor-snapshots/{snapshot_id}/rollback

-  Parameter description

   =========== ========= ==========================
   Parameter   Mandatory Description
   =========== ========= ==========================
   project_id  Yes       Specifies the project ID.
   snapshot_id Yes       Specifies the snapshot ID.
   =========== ========= ==========================

Request
-------

-  Parameter description

   +-----------+--------+-----------+----------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Mandatory | Description                                                                                                                            |
   +===========+========+===========+========================================================================================================================================+
   | rollback  | Object | Yes       | Specifies the snapshot rollback information. For details, see :ref:`Parameters in the rollback field <evs_04_2022__li37311846112126>`. |
   +-----------+--------+-----------+----------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_2022__li37311846112126:

   Parameters in the **rollback** field

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Type            | Mandatory       | Description                                                                                                                  |
   +=================+=================+=================+==============================================================================================================================+
   | volume_id       | String          | Yes             | Specifies the ID of the target disk.                                                                                         |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------+
   | name            | String          | No              | Specifies the name of the target disk. The value can contain a maximum of 255 bytes.                                         |
   |                 |                 |                 |                                                                                                                              |
   |                 |                 |                 | .. note::                                                                                                                    |
   |                 |                 |                 |                                                                                                                              |
   |                 |                 |                 |    Parameter **name** cannot be used independently. When **name** is going to be used, **volume_id** must also be specified. |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   .. code-block::

      {
          "rollback": {
              "name": "test-001",
              "volume_id": "5aa119a8-d25b-45a7-8d1b-88e127885635"
          }
      }

Response
--------

-  Parameter description

   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                                                                      |
   +===========+========+==================================================================================================================================================+
   | rollback  | Object | Specifies the snapshot rollback information. For details, see :ref:`Parameter in the rollback field <evs_04_2022__li1951113011190>`.             |
   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | error     | Object | Specifies the error message returned when an error occurs. For details, see :ref:`Parameters in the error field <evs_04_2022__li0419202382514>`. |
   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_2022__li1951113011190:

   Parameter in the **rollback** field

   ========= ====== ====================================
   Parameter Type   Description
   ========= ====== ====================================
   volume_id String Specifies the ID of the target disk.
   ========= ====== ====================================

-  .. _evs_04_2022__li0419202382514:

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
          "rollback": {
              "volume_id": "5aa119a8-d25b-45a7-8d1b-88e127885635"
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

   202

Error Codes
-----------

For details, see :ref:`Error Codes <evs_04_0038>`.
