:original_name: evs_03_0007.html

.. _evs_03_0007:

Deleting an EVS Snapshot
========================

Scenarios
---------

If an EVS snapshot is no longer used, you can delete it to release virtual resources.

Constraints
-----------

-  A snapshot can be deleted only when it is in the **available** or **error** state.

Involved APIs
-------------

Query the snapshot list, obtain the ID of the target snapshot, and then delete the snapshot.

To meet the preceding requirements, call the following APIs:

-  Query EVS snapshots.
-  Delete an EVS snapshot.

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

#. Delete the snapshot.

   -  API information

      URI format: DELETE /v3/{project_id}/snapshots/{snapshot_id}

      For details, see **OpenStack Cinder API v3** > **EVS Snapshot** > **Deleting an EVS Snapshot** in the *Elastic Volume Service API Reference*.

   -  Example request

      DELETE /v3/000efdc5f9064584b718b181df137bd7/snapshots/b836dc3d-4e10-4ea4-a34c-8f6b0460a583

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
             "badRequest": {
                 "message": "XXXX",
                 "code": "XXX"
             }
         }
