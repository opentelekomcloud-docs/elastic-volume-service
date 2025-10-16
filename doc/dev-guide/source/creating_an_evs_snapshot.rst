:original_name: evs_03_0006.html

.. _evs_03_0006:

Creating an EVS Snapshot
========================

Scenarios
---------

You can create an EVS snapshot on the management console to save the disk data at a specific time point.

Constraints
-----------

A maximum of 7 snapshots can be created for an EVS disk.

Involved APIs
-------------

Query the disk list, obtain the ID of the target disk, and then create the snapshot.

To meet the preceding requirements, call the following APIs:

-  Query EVS disks.
-  Create an EVS snapshot.

Procedure
---------

#. Query EVS disks.

   -  API information

      URI format: GET /v3/{project_id}/volumes

      For details, see **OpenStack Cinder API v3** > **EVS Disk** > **Querying EVS Disks** in the *Elastic Volume Service API Reference*.

   -  Example request

      GET /v3/000efdc5f9064584b718b181df137bd7/volumes

   -  Example response

      .. code-block::

         {
             "volumes": [
                 {
                     "id": "6b604cef-9bd8-4f5a-ae56-45839e6e1f0a",
                     "links": [
                         {
                             "href": "https://volume.localdomain.com:8776/v2/dd14c6ac581f40059e27f5320b60bf2f/volumes/6b604cef-9bd8-4f5a-ae56-45839e6e1f0a",
                             "rel": "self"
                         },
                         {
                             "href": "https://volume.localdomain.com:8776/dd14c6ac581f40059e27f5320b60bf2f/volumes/6b604cef-9bd8-4f5a-ae56-45839e6e1f0a",
                             "rel": "bookmark"
                         }
                     ],
                     "name": "zjb_u25_test"
                 },
                 {
                     "id": "2bce4552-9a7d-48fa-8484-abbbf64b206e",
                     "links": [
                         {
                             "href": "https://volume.localdomain.com:8776/v2/dd14c6ac581f40059e27f5320b60bf2f/volumes/2bce4552-9a7d-48fa-8484-abbbf64b206e",
                             "rel": "self"
                         },
                         {
                             "href": "https://volume.localdomain.com:8776/dd14c6ac581f40059e27f5320b60bf2f/volumes/2bce4552-9a7d-48fa-8484-abbbf64b206e",
                             "rel": "bookmark"
                         }
                     ],
                     "name": "zjb_u25_test"
                 },
                 {
                     "id": "3f1b98ec-a8b5-4e92-a727-88def62d5ad3",
                     "links": [
                         {
                             "href": "https://volume.localdomain.com:8776/v2/dd14c6ac581f40059e27f5320b60bf2f/volumes/3f1b98ec-a8b5-4e92-a727-88def62d5ad3",
                             "rel": "self"
                         },
                         {
                             "href": "https://volume.localdomain.com:8776/dd14c6ac581f40059e27f5320b60bf2f/volumes/3f1b98ec-a8b5-4e92-a727-88def62d5ad3",
                             "rel": "bookmark"
                         }
                     ],
                     "name": "zjb_u25_test"
                 }
             ],
             "volumes_links": [
                 {
                     "href": "https://volume.localdomain.com:8776/v2/dd14c6ac581f40059e27f5320b60bf2f/volumes?limit=3&marker=3f1b98ec-a8b5-4e92-a727-88def62d5ad3",
                     "rel": "next"
                 }
             ]
         }

#. Create the snapshot.

   -  API information

      URI format: POST /v3/{project_id}/snapshots

      For details, see **OpenStack Cinder API v3** > **EVS Snapshot** > **Creating an EVS Snapshot** in the *Elastic Volume Service API Reference*.

   -  Example request

      GET /v3/000efdc5f9064584b718b181df137bd7/snapshots

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
             "badRequest": {
                 "message": "XXXX",
                 "code": "XXX"
             }
         }
