:original_name: evs_04_3018.html

.. _evs_04_3018:

Querying Details of EVS Disks by Tag
====================================

Function
--------

This API is used to query the details of EVS disks by tag.

Constraints
-----------

None

URI
---

-  URI format

   POST /v3/{project_id}/os-vendor-volumes/resource_instances/action

-  Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   ========== ========= =========================

Request
-------

-  Parameter description

   +-----------------+------------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Type             | Mandatory       | Description                                                                                                                                                |
   +=================+==================+=================+============================================================================================================================================================+
   | tags            | Array of objects | Yes             | Specifies the key-value pairs of the tag. For details, see :ref:`Parameters in the tags field <evs_04_3018__evs_04_2034_li8528152083214>`.                 |
   |                 |                  |                 |                                                                                                                                                            |
   |                 |                  |                 | One tag list can contain a maximum of 10 keys.                                                                                                             |
   |                 |                  |                 |                                                                                                                                                            |
   |                 |                  |                 | Tag keys in a tag list must be unique.                                                                                                                     |
   |                 |                  |                 |                                                                                                                                                            |
   |                 |                  |                 | When multiple keys are specified in a tag list, only the disks having all specified keys are queried.                                                      |
   |                 |                  |                 |                                                                                                                                                            |
   |                 |                  |                 | .. note::                                                                                                                                                  |
   |                 |                  |                 |                                                                                                                                                            |
   |                 |                  |                 |    If multiple tag lists are specified in the request, only the disks that meet the requirements of the last tag list are queried.                         |
   +-----------------+------------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit           | Integer          | No              | Specifies the number of query records.                                                                                                                     |
   |                 |                  |                 |                                                                                                                                                            |
   |                 |                  |                 | The value ranges from 1 to 1000, and the default value is 1000. The returned value cannot exceed this limit.                                               |
   +-----------------+------------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | offset          | Integer          | No              | Specifies the index location.                                                                                                                              |
   |                 |                  |                 |                                                                                                                                                            |
   |                 |                  |                 | The minimum value is **0**, which is also the default value.                                                                                               |
   |                 |                  |                 |                                                                                                                                                            |
   |                 |                  |                 | The first record in the query result is the offset+1 record that meets the query criteria.                                                                 |
   +-----------------+------------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | action          | String           | Yes             | Specifies the operation identifier.                                                                                                                        |
   |                 |                  |                 |                                                                                                                                                            |
   |                 |                  |                 | Specifying **filter** queries the details of disks by tag.                                                                                                 |
   +-----------------+------------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | matches         | Array of objects | No              | Specifies the query criteria that the resource supports. For details, see :ref:`Parameters in the matches field <evs_04_3018__evs_04_2034_li15751146383>`. |
   |                 |                  |                 |                                                                                                                                                            |
   |                 |                  |                 | Tag keys in the list must be unique.                                                                                                                       |
   +-----------------+------------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_3018__evs_04_2034_li8528152083214:

   Parameters in the **tags** field

   +-----------------+------------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Type             | Mandatory       | Description                                                                                                                                                                                                     |
   +=================+==================+=================+=================================================================================================================================================================================================================+
   | key             | String           | Yes             | Specifies the tag key.                                                                                                                                                                                          |
   +-----------------+------------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | values          | Array of objects | Yes             | Specifies the tag value.                                                                                                                                                                                        |
   |                 |                  |                 |                                                                                                                                                                                                                 |
   |                 |                  |                 | -  One value list can contain a maximum of 10 values.                                                                                                                                                           |
   |                 |                  |                 | -  Tag values in a value list must be unique.                                                                                                                                                                   |
   |                 |                  |                 | -  If the value list is left empty, any tag value can be matched. When multiple values are specified in a value list and the key requirements are met, disks that have any of the specified values are queried. |
   +-----------------+------------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_3018__evs_04_2034_li15751146383:

   Parameters in the **matches** field

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------+
   | Parameter       | Type            | Mandatory       | Description                                                                                        |
   +=================+=================+=================+====================================================================================================+
   | key             | String          | Yes             | Specifies the tag key. The value is of the enumerated type.                                        |
   |                 |                 |                 |                                                                                                    |
   |                 |                 |                 | The value can be as follows:                                                                       |
   |                 |                 |                 |                                                                                                    |
   |                 |                 |                 | -  **resource_name**: disk name.                                                                   |
   |                 |                 |                 | -  **service_type**: service type.                                                                 |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------+
   | value           | String          | Yes             | Specifies the tag value.                                                                           |
   |                 |                 |                 |                                                                                                    |
   |                 |                 |                 | -  It can contain up to 255 characters.                                                            |
   |                 |                 |                 | -  If **resource_name** is specified for **key**, the tag value uses a fuzzy match.                |
   |                 |                 |                 | -  If **service_type** is specified for **key**, the value can be **EVS** and is case-insensitive. |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------+

-  Example request

   .. code-block::

      {
          "offset": "100",
          "limit": "100",
          "action": "filter",
          "tags": [
              {
                  "key": "key1",
                  "values": [
                      "value1",
                      "value2"
                  ]
              }
          ],
          "matches": [
              {
                  "key": "resource_name",
                  "value": "resource1"
              },
              {
                  "key": "service_type",
                  "value": "EVS"
              }
          ]
      }

Response
--------

-  Parameter description

   +-------------+----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Type           | Description                                                                                                                                                  |
   +=============+================+==============================================================================================================================================================+
   | total_count | Integer        | Specifies the total number of disks that meet the query criteria.                                                                                            |
   +-------------+----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | resources   | List<resource> | Specifies the resources that meet the query criteria. For details, see :ref:`Parameters in the resources field <evs_04_3018__evs_04_2034_li95931326163214>`. |
   +-------------+----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | error       | Object         | Specifies the error message returned when an error occurs. For details, see :ref:`Parameters in the error field <evs_04_3018__evs_04_2034_li0419202382514>`. |
   +-------------+----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_3018__evs_04_2034_li95931326163214:

   Parameters in the **resources** field

   +-----------------+------------------+--------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Type             | Description                                                                                                              |
   +=================+==================+==========================================================================================================================+
   | resource_id     | String           | Specifies the disk ID.                                                                                                   |
   +-----------------+------------------+--------------------------------------------------------------------------------------------------------------------------+
   | resource_name   | String           | Specifies the disk name.                                                                                                 |
   +-----------------+------------------+--------------------------------------------------------------------------------------------------------------------------+
   | resource_detail | object           | Specifies the resource details.                                                                                          |
   +-----------------+------------------+--------------------------------------------------------------------------------------------------------------------------+
   | tags            | Array of objects | Specifies the tag list. For details, see :ref:`Parameters in the tags field <evs_04_3018__evs_04_2034_li3876131217349>`. |
   +-----------------+------------------+--------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_3018__evs_04_2034_li3876131217349:

   Parameters in the **tags** field

   ========= ====== ========================
   Parameter Type   Description
   ========= ====== ========================
   key       String Specifies the tag key.
   value     String Specifies the tag value.
   ========= ====== ========================

-  .. _evs_04_3018__evs_04_2034_li0419202382514:

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
          "total_count": 1,
          "resources": [{
              "resource_name": "resource1",
              "resource_detail": {
                  "attachments": [{
                      "server_id": "2080869e-ba46-4ea5-b45e-3191ac0f1d54",
                      "attachment_id": "1335f039-7a42-4d1e-be49-ac584db0ba0b",
                      "attached_at": "2019-08-06T07:00:21.842812",
                      "host_name": null,
                      "volume_id": "7fa6b592-ac75-460d-a28a-bb17429d1eb2",
                      "device": "/dev/vda",
                      "id": "7fa6b592-ac75-460d-a28a-bb17429d1eb2"
                  }],
                  "links": [{
                      "href": "https://volume.Region.dc1.domainname.com/v2/051375756c80d5eb2ff0c014498645fb/volumes/7fa6b592-ac75-460d-a28a-bb17429d1eb2",
                      "rel": "self"
                  },
                  {
                      "href": "https://volume.Region.dc1.domainname.com/051375756c80d5eb2ff0c014498645fb/volumes/7fa6b592-ac75-460d-a28a-bb17429d1eb2",
                      "rel": "bookmark"
                  }],
                  "availability_zone": "kvmxen.dc1",
                  "os-vol-host-attr:host": "az21.dc1#2",
                  "encrypted": false,
                  "updated_at": "2019-08-09T06:19:35.874737",
                  "os-volume-replication:extended_status": null,
                  "replication_status": "disabled",
                  "snapshot_id": null,
                  "id": "7fa6b592-ac75-460d-a28a-bb17429d1eb2",
                  "size": 40,
                  "user_id": "75f26e17348643bfb7718578b04635c2",
                  "os-vol-tenant-attr:tenant_id": "051375756c80d5eb2ff0c014498645fb",
                  "service_type": "EVS",
                  "os-vol-mig-status-attr:migstat": null,
                  "metadata": {

                  },
                  "status": "in-use",
                  "volume_image_metadata": {
                      "size": "0",
                      "__quick_start": "False",
                      "container_format": "bare",
                      "min_ram": "0",
                      "image_name": "test-hua-centos7.3-0725",
                      "image_id": "c6c153a6-dde8-4bac-8e40-3d7619436934",
                      "__os_type": "Linux",
                      "min_disk": "20",
                      "__support_kvm": "true",
                      "virtual_env_type": "FusionCompute",
                      "__description": "",
                      "__os_version": "CentOS 7.3 64bit",
                      "__os_bit": "64",
                      "__image_source_type": "uds",
                      "__support_xen": "true",
                      "file_format": "zvhd2",
                      "checksum": "d41d8cd98f00b204e9800998ecf8427e",
                      "__imagetype": "gold",
                      "disk_format": "zvhd2",
                      "__image_cache_type": "Not_Cache",
                      "__isregistered": "true",
                      "__image_location": "192.168.46.200:5443:pcsimsregion:c6c153a6-dde8-4bac-8e40-3d7619436934",
                      "__image_size": "911269888",
                      "__platform": "CentOS"
                  },
                  "description": "",
                  "multiattach": false,
                  "source_volid": null,
                  "consistencygroup_id": null,
                  "os-vol-mig-status-attr:name_id": null,
                  "name": "resource1",
                  "bootable": "true",
                  "created_at": "2019-08-06T06:59:03.056682",
                  "volume_type": "SAS",
                  "shareable": false,
              },
              "tags": [{
                  "key": "key1",
                  "value": "value1"
              },
              {
                  "key": "key1",
                  "value": "value2"
              }],
              "resource_id": "7fa6b592-ac75-460d-a28a-bb17429d1eb2"
          }]
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
          "computeFault": {
              "message": "The server has either erred or is incapable of performing the requested operation.",
              "code": 500
          }
      }

Status Codes
------------

-  Normal

   200

Error Codes
-----------

For details, see :ref:`Error Codes <evs_04_0038>`.
