:original_name: evs_04_3056.html

.. _evs_04_3056:

Creating an EVS Snapshot
========================

Function
--------

This API is used to create an EVS snapshot.

URI
---

-  URI format

   POST /v2/{project_id}/snapshots

-  Parameter description

   ========== ========= ===============
   Parameter  Mandatory Description
   ========== ========= ===============
   project_id Yes       The project ID.
   ========== ========= ===============

Request
-------

-  Parameter description

   +-----------+--------+-----------+------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Mandatory | Description                                                                                                                              |
   +===========+========+===========+==========================================================================================================================================+
   | snapshot  | Object | Yes       | The information of the snapshot to be created. For details, see :ref:`Parameters in the snapshot field <evs_04_3056__li39126135104128>`. |
   +-----------+--------+-----------+------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_3056__li39126135104128:

   Parameters in the **snapshot** field

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Type            | Mandatory       | Description                                                                                                                                                                                                                                                                                                                                                                      |
   +=================+=================+=================+==================================================================================================================================================================================================================================================================================================================================================================================+
   | volume_id       | String          | Yes             | The ID of the snapshot's source disk.                                                                                                                                                                                                                                                                                                                                            |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | force           | Boolean         | No              | The flag for forcibly creating a snapshot. The default value is **false**.                                                                                                                                                                                                                                                                                                       |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                 | -  If this parameter is set to **false** and the disk is in the **attaching** state, the snapshot cannot be forcibly created.                                                                                                                                                                                                                                                    |
   |                 |                 |                 | -  If this parameter is set to **true** and the disk is in the **attaching** state, the snapshot can be forcibly created.                                                                                                                                                                                                                                                        |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | metadata        | Object          | No              | The snapshot metadata.                                                                                                                                                                                                                                                                                                                                                           |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description     | String          | No              | The snapshot description. The value can be **null**. The value can contain a maximum of 255 bytes.                                                                                                                                                                                                                                                                               |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name            | String          | No              | The snapshot name. The value can contain a maximum of 255 bytes.                                                                                                                                                                                                                                                                                                                 |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                 | .. note::                                                                                                                                                                                                                                                                                                                                                                        |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                 |    When creating a backup for a disk, a snapshot will be created and named with prefix **autobk_snapshot\_**. The EVS console has imposed operation restrictions on snapshots with prefix **autobk_snapshot\_**. Therefore, you are advised not to use **autobk_snapshot\_** as the name prefix for the snapshots you created. Otherwise, the snapshots cannot be used normally. |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   .. code-block::

      {
          "snapshot": {
              "name": "snap-001",
              "description": "Daily backup",
              "volume_id": "5aa119a8-d25b-45a7-8d1b-88e127885635",
              "force": false,
              "metadata": { }
          }
      }

Response
--------

-  Parameter description

   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                                                          |
   +===========+========+======================================================================================================================================+
   | snapshot  | Object | The snapshot information. For details, see :ref:`Parameters in the snapshot field <evs_04_3056__li52620487104128>`.                  |
   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------+
   | error     | Object | The error message returned if an error occurs. For details, see :ref:`Parameters in the error field <evs_04_3056__li0419202382514>`. |
   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_3056__li52620487104128:

   Parameters in the **snapshot** field

   +--------------------------------------------+-----------------------+---------------------------------------------------------------------------------+
   | Parameter                                  | Type                  | Description                                                                     |
   +============================================+=======================+=================================================================================+
   | id                                         | String                | The snapshot ID.                                                                |
   +--------------------------------------------+-----------------------+---------------------------------------------------------------------------------+
   | status                                     | String                | The snapshot status. For details, see :ref:`EVS Snapshot Status <evs_04_0041>`. |
   +--------------------------------------------+-----------------------+---------------------------------------------------------------------------------+
   | name                                       | String                | The snapshot name.                                                              |
   +--------------------------------------------+-----------------------+---------------------------------------------------------------------------------+
   | description                                | String                | The snapshot description.                                                       |
   +--------------------------------------------+-----------------------+---------------------------------------------------------------------------------+
   | created_at                                 | String                | The time when the snapshot was created.                                         |
   |                                            |                       |                                                                                 |
   |                                            |                       | Time format: UTC YYYY-MM-DDTHH:MM:SS.XXXXXX                                     |
   +--------------------------------------------+-----------------------+---------------------------------------------------------------------------------+
   | metadata                                   | Object                | The snapshot metadata.                                                          |
   +--------------------------------------------+-----------------------+---------------------------------------------------------------------------------+
   | volume_id                                  | String                | The ID of the snapshot's source disk.                                           |
   +--------------------------------------------+-----------------------+---------------------------------------------------------------------------------+
   | size                                       | Integer               | The snapshot size, in GB.                                                       |
   +--------------------------------------------+-----------------------+---------------------------------------------------------------------------------+
   | updated_at                                 | String                | The time when the snapshot was updated.                                         |
   |                                            |                       |                                                                                 |
   |                                            |                       | Time format: UTC YYYY-MM-DDTHH:MM:SS.XXXXXX                                     |
   +--------------------------------------------+-----------------------+---------------------------------------------------------------------------------+
   | os-extended-snapshot-attributes:progress   | String                | The reserved field.                                                             |
   +--------------------------------------------+-----------------------+---------------------------------------------------------------------------------+
   | os-extended-snapshot-attributes:project_id | String                | The reserved field.                                                             |
   +--------------------------------------------+-----------------------+---------------------------------------------------------------------------------+

-  .. _evs_04_3056__li0419202382514:

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
          "snapshot": {
              "status": "creating",
              "description": "Daily backup",
              "created_at": "2013-02-25T03:56:53.081642",
              "metadata": { },
              "volume_id": "5aa119a8-d25b-45a7-8d1b-88e127885635",
              "size": 1,
              "id": "ffa9bc5e-1172-4021-acaf-cdcd78a9584d",
              "name": "snap-001",
              "updated_at": "2013-02-25T03:56:53.081642"
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
