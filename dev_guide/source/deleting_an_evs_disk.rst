:original_name: evs_03_0005.html

.. _evs_03_0005:

Deleting an EVS Disk
====================

Scenarios
---------

If an EVS disk is no longer used, you can delete it to release virtual resources.

Constraints
-----------

-  An EVS disk can be deleted only when its status is **available**, **error**, **error_extending**, **error_restoring**, or **error_rollbacking**.
-  Before deleting a shared EVS disk, ensure that the disk has been detached from all its servers.

.. important::

   -  When you delete an EVS disk, all the disk data including the snapshots created for this disk will be deleted. Exercise caution when performing this operation.
   -  Deleted EVS disks cannot be recovered. Exercise caution when performing this operation.

Involved APIs
-------------

Query the disk list, obtain the ID of the target disk, and then delete the disk.

To meet the preceding requirements, call the following APIs:

-  Query EVS disks.
-  Delete an EVS disk.

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

#. Delete the disk.

   -  API information

      URI format: DELETE /v3/{project_id}/volumes/{volume_id}

      For details, see **OpenStack Cinder API v3** > **EVS Disk** > **Deleting an EVS Disk** in the *Elastic Volume Service API Reference*.

   -  Example request

      DELETE /v3/000efdc5f9064584b718b181df137bd7/baremetalservers/5850a7e7-88dd-4d99-8439-347de8cc0dd7/volume/50ef9435-ca68-4b9b-a837-73377b9fdaa3?cascade=true

      .. note::

         **cascade=true** indicates that the snapshots created for the disk will also be deleted.

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
