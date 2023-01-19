:original_name: evs_03_0003.html

.. _evs_03_0003:

Creating EVS Disks
==================

Scenarios
---------

This API is used to create one or multiple EVS disks.

Constraints
-----------

None

Involved APIs
-------------

Query the AZs before you create EVS disks.

If you need to create system disks, query the image information and obtain the image ID.

If you need to create the disk from a data source, for example a snapshot or backup, query the snapshot or backup information and obtain the snapshot ID or backup ID.

Obtain the required information and then create the disk.

To meet the preceding requirements, call the following APIs:

-  Query AZs.
-  Query images.
-  Query EVS snapshots.
-  Query backups.
-  Create EVS disks.

Procedure
---------

#. Query the AZs.

   -  API information

      URI format: GET /v3/{project_id}/os-availability-zone

      For details, see **OpenStack Cinder API v3** > **EVS Disk** > **Querying Information About All AZs** in the *Elastic Volume Service API Reference*.

   -  Example request

      GET /v3/9c53a566cb3443ab910cf0daebca90c4/os-availability-zone

   -  Example response

      .. code-block::

          {
             "availabilityZoneInfo": [
                 {
                     "zoneState": {
                         "available": true
                     },
                     "zoneName": "az1.dc1"
                 },
                 {
                     "zoneState": {
                         "available": true
                     },
                     "zoneName": "vmware.az1"
                 }
             ]
         }

#. (Optional) Query the images if system disks are going to be created.

   -  API information

      URI format: GET /v2/images

      For details, see **API** > **Image (Native OpenStack APIs)** > **Querying Images (Native OpenStack API)** in the *Image Management Service API Reference*.

   -  Example request

      GET /v2/images

   -  Example response

      .. code-block::

         {
             "images": [
                 {
                     "status": "queued",
                     "name": "test",
                     "tags": [
                         "test",
                         "image"
                     ],
                     "container_format": "bare",
                     "created_at": "2014-12-16T01:22:05Z",
                     "disk_format": "qcow2",
                     "updated_at": "2014-12-16T01:22:05Z",
                     "visibility": "private",
                     "self": "/v2/images/4ca46bf1-5c61-48ff-b4f3-0ad4e5e3ba90",
                     "min_disk": 1,
                     "protected": false,
                     "id": "4ca46bf1-5c61-48ff-b4f3-0ad4e5e3ba90",
                     "file": "/v2/images/4ca46bf1-5c61-48ff-b4f3-0ad4e5e3ba90/file",
                     "owner": "aed2c611711548a4a9c16fb8fe166af4",
                     "min_ram": 1024,
                     "schema": "/v2/schemas/image"
                 },
                 {
                     "status": "active",
                     "name": "cirros",
                     "tags": [
                         "new"
                     ],
                     "container_format": "bare",
                     "created_at": "2014-12-11T03:53:43Z",
                     "size": 13147648,
                     "disk_format": "qcow2",
                     "updated_at": "2014-12-15T20:02:12Z",
                     "visibility": "private",
                     "self": "/v2/images/5155a22a-834e-4ffe-a95d-ed9665a8ed76",
                     "min_disk": 0,
                     "protected": false,
                     "id": "5155a22a-834e-4ffe-a95d-ed9665a8ed76",
                     "file": "/v2/images/5155a22a-834e-4ffe-a95d-ed9665a8ed76/file",
                     "checksum": "d972013792949d0d3ba628fbe8685bce",
                     "owner": "aed2c611711548a4a9c16fb8fe166af4",
                     "min_ram": 0,
                     "schema": "/v2/schemas/image"
                 }
             ],
             "schema": "/v2/schemas/images",
             "first": "/v2/images"
         }

#. (Optional) Query the EVS snapshots if the disk is going to be created from a snapshot.

   -  API information

      URI format: GET /v3/{project_id}/snapshots

      For details, see **OpenStack Cinder API v3** > **EVS Snapshot** > **Querying EVS Snapshots** in the *Elastic Volume Service API Reference*.

   -  Example request

      GET /v3/9c53a566cb3443ab910cf0daebca90c4/snapshots

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

#. (Optional) Query the backups if the disk is going to be created from a backup.

   -  API information

      URI format: GET /v3/{project_id}/backups

      For details, see **CBR APIs** > **Backups** > **Querying All Backups** in the *Cloud Backup and Recovery API Reference*.

   -  Example request

      GET /v3/{project_id}/backups

   -  Example response

      .. code-block::

         {
           "count" : 2,
           "backups" : [ {
             "provider_id" : "0daac4c5-6707-4851-97ba-169e36266b66",
             "checkpoint_id" : "1fced58b-2a31-4851-bcbb-96216f83ce99",
             "updated_at" : "2020-02-21T07:07:25.113761",
             "vault_id" : "cca85ea5-00a4-418d-9222-bd83985bc515",
             "id" : "b1c4afd9-e7a6-4888-9010-c2bac3aa7910",
             "resource_az" : "br-iaas-odin1a",
             "image_type" : "backup",
             "resource_id" : "1a503932-ee8f-4dd5-8248-8dfb57e584c5",
             "resource_size" : 40,
             "children" : [ ],
             "extend_info" : {
               "auto_trigger" : true,
               "supported_restore_mode" : "backup",
               "contain_system_disk" : true,
               "support_lld" : true,
               "system_disk" : false
             },
             "project_id" : "0605767b5780d5762fc5c0118072a564",
             "status" : "available",
             "resource_name" : "test001-02",
             "description" : "",
             "expired_at" : "2020-05-21T07:00:54.060493",
             "name" : "autobk_b629",
             "created_at" : "2020-02-21T07:00:54.065135",
             "resource_type" : "OS::Nova::Server"
           }, {
             "provider_id" : "d1603440-187d-4516-af25-121250c7cc97",
             "checkpoint_id" : "f64c351f-769f-4c04-8806-fd90a59e9b12",
             "updated_at" : "2020-02-21T07:09:37.767084",
             "vault_id" : "79bd9daa-884f-4f84-b8fe-235d58cd927d",
             "id" : "5606aab5-2dc2-4498-8144-dc848d099af5",
             "resource_az" : "br-iaas-odin1a",
             "image_type" : "backup",
             "resource_id" : "54f7ccbc-072f-4ec5-a7b7-b24dabdb4539",
             "resource_size" : 40,
             "children" : [ ],
             "extend_info" : {
               "auto_trigger" : true,
               "snapshot_id" : "e3def9a8-e4b4-4c12-b132-f4ba8ce9a34f",
               "bootable" : true,
               "support_lld" : true,
               "encrypted" : false,
               "system_disk" : false
             },
             "project_id" : "0605767b5780d5762fc5c0118072a564",
             "status" : "available",
             "resource_name" : "qsy_000",
             "description" : "",
             "expired_at" : "2020-03-22T07:00:34.877896",
             "name" : "autobk_6809",
             "created_at" : "2020-02-21T07:00:34.882174",
             "resource_type" : "OS::Cinder::Volume"
           } ]
         }

#. Create EVS disks.

   -  API information

      URI format: POST /v3/{project_id}/volumes

      For details, see **OpenStack Cinder API v3** > **EVS Disk** > **Creating EVS Disks** in the *Elastic Volume Service API Reference*.

   -  Example request

      POST /v3/9c53a566cb3443ab910cf0daebca90c4/volumes

      .. code-block::

         {
             "volume": {
                 "name": "openapi_vol01",
                 "imageRef": "027cf713-45a6-45f0-ac1b-0ccc57ac12e2",
                 "availability_zone": "xxx",
                 "description": "create for api test",
                 "volume_type": "SATA",
                 "metadata": {
                     "volume_owner": "openapi"
                 },
                 "consistencygroup_id": null,
                 "OS-SCH-HNT:scheduler_hints": {
                     "dedicated_storage_id": "eddc1a3e-4145-45be-98d7-bf6f65af9767"
                 },
                 "source_volid": null,
                 "snapshot_id": null,
                 "shareable": "false",
                 "multiattach": false,
                 "source_replica": null,
                 "size": 40
             }
         }

   -  Example response

      .. code-block::

         {
             "volume": {
                 "attachments": [ ],
                 "availability_zone": "xxx",
                 "bootable": "false",
                 "consistencygroup_id": null,
                 "created_at": "2016-05-25T02:38:40.392463",
                 "description": "create for api test",
                 "encrypted": false,
                 "id": "8dd7c486-8e9f-49fe-bceb-26aa7e312b66",
                 "links": [
                     {
                         "href": "https://volume.localdomain.com:8776/v2/5dd0b0056f3d47b6ab4121667d35621a/volumes/8dd7c486-8e9f-49fe-bceb-26aa7e312b66",
                         "rel": "self"
                     },
                     {
                         "href": "https://volume.localdomain.com:8776/5dd0b0056f3d47b6ab4121667d35621a/volumes/8dd7c486-8e9f-49fe-bceb-26aa7e312b66",
                         "rel": "bookmark"
                     }
                 ],
                 "metadata": {
                     "volume_owner": "openapi"
                 },
                 "name": "openapi_vol01",
                 "replication_status": "disabled",
                 "shareable": false,
                 "multiattach": false,
                 "size": 40,
                 "snapshot_id": null,
                 "source_volid": null,
                 "status": "creating",
                 "updated_at": null,
                 "user_id": "39f6696ae23740708d0f358a253c2637",
                 "volume_type": "SATA"
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
