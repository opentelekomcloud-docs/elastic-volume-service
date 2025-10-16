:original_name: evs_03_0004.html

.. _evs_03_0004:

Expanding the Capacity of an EVS Disk
=====================================

Scenarios
---------

For an EVS disk that has been created, you can call this API to expand the disk capacity if the disk space is insufficient.

Constraints
-----------

-  If the status of the to-be-expanded disk is **available**, there are no restrictions.
-  If the status of the to-be-expanded disk is **in-use**, the restrictions are as follows:

   -  A shared disk cannot be expanded, that is, the value of parameter **multiattach** must be **false**.
   -  The status of the server to which the disk attached must be **ACTIVE**, **PAUSED**, **SUSPENDED**, or **SHUTOFF**.

Involved APIs
-------------

Query the disk list, obtain the ID of the target disk, and then expand the disk capacity.

To meet the preceding requirements, call the following APIs:

-  Query EVS disks.
-  Expand the capacity of a disk.

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

#. Expand the capacity of an EVS disk.

   -  API information

      URI format: POST /v3/{project_id}/volumes/{volume_id}/action

      For details, see **OpenStack Cinder API v3** > **EVS Disk Actions** > **Expanding the Capacity of an EVS Disk** in the *Elastic Volume Service API Reference*.

   -  Example request

      POST /v3/000efdc5f9064584b718b181df137bd7/ volumes/9ab74d89-61e7-4259-8546-465fdebe4944/ action

      .. code-block::

         {
             "os-extend": {
                 "new_size": 100
             }
         }

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
