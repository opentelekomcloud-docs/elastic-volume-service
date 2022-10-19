:original_name: evs_03_0008.html

.. _evs_03_0008:

Rolling Back a Snapshot to an EVS Disk
======================================

Scenarios
---------

If the data in an EVS disk is incorrect or damaged, you can roll back the data from a snapshot to the source EVS disk to restore the data.

Constraints
-----------

-  When you roll back a snapshot to a disk, you can only roll back the snapshot to the source disk. Rollback to a specified disk is not supported.
-  You can roll back a disk from a snapshot only when the disk is in the **available** or **error_rollbacking** state.
-  Snapshots whose names started with prefix **autobk_snapshot\_** are automatically created by the system during backup creations. Do not use these snapshots to roll back the disk data.

Involved APIs
-------------

Query the snapshot list, obtain the ID of the snapshot and the ID of the snapshot's source disk, and then roll back the snapshot to the source disk.

To meet the preceding requirements, call the following APIs:

-  Query EVS snapshots.
-  Roll back a snapshot to an EVS disk.

Procedure
---------

#. Query the EVS snapshots.

   -  API information

      URI format: GET /v3/{project_id}/snapshots

      For details, see **OpenStack Cinder API v3** > **EVS Snapshot** > **Querying EVS Snapshots** in the *Elastic Volume Service API Reference*.

   -  Example request

      GET /v3/000efdc5f9064584b718b181df137bd7/snapshots

   -  Example response

      .. code-block::

         {
             "snapshots": [
                 {
                     "created_at": "2016-02-16T16:54:14.981520",
                     "description": null,
                     "id": "b836dc3d-4e10-4ea4-a34c-8f6b0460a583",
                     "metadata": { },
                     "name": "test01",
                     "size": 1,
                     "status": "available",
                     "volume_id": "ba5730ea-8621-4ae8-b702-ff0ffc12c209",
                     "updated_at": null
                 },
                 {
                     "created_at": "2016-02-16T16:54:19.475397",
                     "description": null,
                     "id": "83be494d-329e-4a78-8ac5-9af900f48b95",
                     "metadata": { },
                     "name": "test02",
                     "size": 1,
                     "status": "available",
                     "volume_id": "ba5730ea-8621-4ae8-b702-ff0ffc12c209",
                     "updated_at": null
                 },
                 {
                     "created_at": "2016-02-16T16:54:24.367414",
                     "description": null,
                     "id": "dd360f46-7593-4d35-8f2c-5566fd0bd79e",
                     "metadata": { },
                     "name": "test03",
                     "size": 1,
                     "status": "available",
                     "volume_id": "ba5730ea-8621-4ae8-b702-ff0ffc12c209",
                     "updated_at": null
                 },
                 {
                     "created_at": "2016-02-16T16:54:29.766740",
                     "description": null,
                     "id": "4c29796a-8cf4-4482-9afc-e66da9a81240",
                     "metadata": { },
                     "name": "test04",
                     "size": 1,
                     "status": "available",
                     "volume_id": "ba5730ea-8621-4ae8-b702-ff0ffc12c209",
                     "updated_at": null
                 }
             ],
             "snapshots_links": null
         }

#. Roll back the snapshot to the source disk.

   -  API information

      URI format: POST /v3/{project_id}/os-vendor-snapshots/{snapshot_id}/rollback

      For details, see **API v3** > **EVS Snapshot** > **Rolling Back a Snapshot to an EVS Disk** in the *Elastic Volume Service API Reference*.

   -  Example request

      POST /v3/000efdc5f9064584b718b181df137bd7/os-vendor-snapshots/b836dc3d-4e10-4ea4-a34c-8f6b0460a583 /rollback

      .. code-block::

         {
             "rollback": {
                 "name": "test-001",
                 "volume_id": "5aa119a8-d25b-45a7-8d1b-88e127885635"
             }
         }

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
