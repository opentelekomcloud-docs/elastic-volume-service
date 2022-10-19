:original_name: evs_04_2009.html

.. _evs_04_2009:

Updating an EVS Disk (Deprecated)
=================================

Function
--------

This API is used to update the name and description of an EVS disk.

.. important::

   This API has been deprecated. Use another API. For details, see :ref:`Updating an EVS Disk <evs_04_2067>`.

URI
---

-  URI format

   PUT /v2/{project_id}/cloudvolumes/{volume_id}

-  Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   volume_id  Yes       Specifies the disk ID.
   ========== ========= =========================

Request
-------

-  Parameter description

   +-----------+--------+-----------+----------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Mandatory | Description                                                                                                                            |
   +===========+========+===========+========================================================================================================================================+
   | volume    | Object | Yes       | Specifies the information of the disk to be updated. For details, see :ref:`Parameters in the volume field <evs_04_2009__li44975500>`. |
   +-----------+--------+-----------+----------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_2009__li44975500:

   Parameters in the **volume** field

   +-------------+--------+-----------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Type   | Mandatory | Description                                                                                                                                                |
   +=============+========+===========+============================================================================================================================================================+
   | name        | String | No        | Specifies the new name of the disk. Parameters **name** and **description** cannot be null at the same time. The value can contain a maximum of 255 bytes. |
   +-------------+--------+-----------+------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description | String | No        | Specifies the new description of the disk. **name** and **description** cannot be null at the same time. The value can contain a maximum of 255 bytes.     |
   +-------------+--------+-----------+------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   .. code-block::

      {
          "volume": {
              "name": "test_volume",
              "description": "test"
          }
      }

Response
--------

-  Parameter description

   +---------------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                             | Type                  | Description                                                                                                                                             |
   +=======================================+=======================+=========================================================================================================================================================+
   | id                                    | String                | Specifies the disk ID.                                                                                                                                  |
   +---------------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | links                                 | Array of objects      | Specifies the disk URI. For details, see :ref:`Parameters in the links field <evs_04_2009__li949885516582>`.                                            |
   +---------------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                                  | String                | Specifies the disk name.                                                                                                                                |
   +---------------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status                                | String                | Specifies the disk status. For details, see :ref:`EVS Disk Status <evs_04_0040>`.                                                                       |
   +---------------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | attachments                           | Array of objects      | Specifies the disk attachment information. For details, see :ref:`Parameters in the attachments field <evs_04_2009__li2847936164017>`.                  |
   +---------------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | availability_zone                     | String                | Specifies the AZ to which the disk belongs.                                                                                                             |
   +---------------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | source_volid                          | String                | Specifies the source disk ID. This parameter has a value if the disk is created from a source disk.                                                     |
   |                                       |                       |                                                                                                                                                         |
   |                                       |                       | Currently, this field is not supported by EVS.                                                                                                          |
   +---------------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | snapshot_id                           | String                | Specifies the snapshot ID. This parameter has a value if the disk is created from a snapshot.                                                           |
   +---------------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description                           | String                | Specifies the disk description.                                                                                                                         |
   +---------------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | os-vol-tenant-attr:tenant_id          | String                | Specifies the ID of the tenant to which the disk belongs. Currently, the returned parameter value is invalid. The tenant ID is actually the project ID. |
   +---------------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | volume_image_metadata                 | Object                | Specifies the metadata of the disk image. Currently, the returned parameter value is invalid.                                                           |
   |                                       |                       |                                                                                                                                                         |
   |                                       |                       | .. note::                                                                                                                                               |
   |                                       |                       |                                                                                                                                                         |
   |                                       |                       |    For details about **volume_image_metadata**, see **Querying Image Details (Native OpenStack API)** in the *Image Management Service API Reference*.  |
   +---------------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | created_at                            | String                | Specifies the time when the disk was created.                                                                                                           |
   |                                       |                       |                                                                                                                                                         |
   |                                       |                       | Time format: UTC YYYY-MM-DDTHH:MM:SS.XXXXXX                                                                                                             |
   +---------------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | volume_type                           | String                | Specifies the disk type.                                                                                                                                |
   |                                       |                       |                                                                                                                                                         |
   |                                       |                       | Currently, the value can be **SSD**, **SAS**, **SATA**, **co-p1**, or **uh-l1**.                                                                        |
   |                                       |                       |                                                                                                                                                         |
   |                                       |                       | -  **SSD**: specifies the ultra-high I/O disk type.                                                                                                     |
   |                                       |                       |                                                                                                                                                         |
   |                                       |                       | -  **SAS**: specifies the high I/O disk type.                                                                                                           |
   |                                       |                       |                                                                                                                                                         |
   |                                       |                       | -  **SATA**: specifies the common I/O disk type.                                                                                                        |
   |                                       |                       |                                                                                                                                                         |
   |                                       |                       | -  **co-p1**: specifies the high I/O (performance-optimized I) disk type.                                                                               |
   |                                       |                       |                                                                                                                                                         |
   |                                       |                       | -  **uh-l1**: specifies the ultra-high I/O (latency-optimized) disk type.                                                                               |
   |                                       |                       |                                                                                                                                                         |
   |                                       |                       |    Disks of the **co-p1** and **uh-l1** types are used exclusively for HPC ECSs and SAP HANA ECSs.                                                      |
   +---------------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | size                                  | Integer               | Specifies the disk size, in GB.                                                                                                                         |
   +---------------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | bootable                              | String                | Specifies whether the disk is bootable.                                                                                                                 |
   |                                       |                       |                                                                                                                                                         |
   |                                       |                       | -  **true**: specifies a bootable disk.                                                                                                                 |
   |                                       |                       | -  **false**: specifies a non-bootable disk.                                                                                                            |
   +---------------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | metadata                              | Object                | Specifies the disk metadata. For details, see :ref:`Parameters in the metadata field <evs_04_2009__li6221175494947>`.                                   |
   +---------------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | os-vol-host-attr:host                 | String                | Reserved field                                                                                                                                          |
   +---------------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | shareable                             | String                | Specifies whether the disk is shareable.                                                                                                                |
   |                                       |                       |                                                                                                                                                         |
   |                                       |                       | .. note::                                                                                                                                               |
   |                                       |                       |                                                                                                                                                         |
   |                                       |                       |    This field is no longer used. Use **multiattach**.                                                                                                   |
   +---------------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | error                                 | Object                | Specifies the error message returned when an error occurs. For details, see :ref:`Parameters in the error field <evs_04_2009__li0419202382514>`.        |
   +---------------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | multiattach                           | Boolean               | Specifies whether the disk is shareable.                                                                                                                |
   |                                       |                       |                                                                                                                                                         |
   |                                       |                       | -  **true**: specifies a shared disk.                                                                                                                   |
   |                                       |                       | -  **false**: specifies a non-shared disk.                                                                                                              |
   +---------------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | os-volume-replication:extended_status | String                | Reserved field                                                                                                                                          |
   +---------------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_2009__li949885516582:

   Parameters in the **links** field

   ========= ====== ==========================================
   Parameter Type   Description
   ========= ====== ==========================================
   href      String Specifies the corresponding shortcut link.
   rel       String Specifies the shortcut link marker name.
   ========= ====== ==========================================

-  .. _evs_04_2009__li2847936164017:

   Parameters in the **attachments** field

   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                     |
   +=======================+=======================+=================================================================================================+
   | server_id             | String                | Specifies the ID of the server to which the disk is attached.                                   |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------+
   | attachment_id         | String                | Specifies the ID of the attachment information.                                                 |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------+
   | attached_at           | String                | Specifies the time when the disk was attached.                                                  |
   |                       |                       |                                                                                                 |
   |                       |                       | Time format: UTC YYYY-MM-DDTHH:MM:SS.XXXXXX                                                     |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------+
   | host_name             | String                | Specifies the name of the physical host accommodating the server to which the disk is attached. |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------+
   | volume_id             | String                | Specifies the disk ID.                                                                          |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------+
   | device                | String                | Specifies the device name.                                                                      |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------+
   | id                    | String                | Specifies the ID of the attached resource.                                                      |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------+

-  .. _evs_04_2009__li6221175494947:

   Parameters in the **metadata** field

   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                         |
   +=======================+=======================+=====================================================================================================================================================================================+
   | \__system__encrypted  | String                | Specifies the parameter that describes the encryption function in **metadata**. The value can be **0** or **1**.                                                                    |
   |                       |                       |                                                                                                                                                                                     |
   |                       |                       | -  **0**: indicates the disk is not encrypted.                                                                                                                                      |
   |                       |                       | -  **1**: indicates the disk is encrypted.                                                                                                                                          |
   |                       |                       | -  If this parameter does not appear, the disk is not encrypted by default.                                                                                                         |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | \__system__cmkid      | String                | Specifies the encryption CMK ID in **metadata**. This parameter is used together with **\__system__encrypted** for encryption. The length of **cmkid** is fixed at 36 bytes.        |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | hw:passthrough        | String                | Specifies the parameter that describes the disk device type in **metadata**. The value can be **true** or **false**.                                                                |
   |                       |                       |                                                                                                                                                                                     |
   |                       |                       | -  If this parameter is set to **true**, the disk device type is SCSI, which allows ECS OSs to directly access the underlying storage media and supports SCSI reservation commands. |
   |                       |                       | -  If this parameter is set to **false**, the disk device type is VBD (the default type), that is, Virtual Block Device (VBD), which supports only simple SCSI read/write commands. |
   |                       |                       | -  If this parameter does not appear, the disk device type is VBD.                                                                                                                  |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | full_clone            | String                | Specifies the clone method. When the disk is created from a snapshot, the parameter value is **0**, indicating the linked cloning method.                                           |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_2009__li0419202382514:

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
          "id": "36ba39af-3579-4e6e-adfc-b764349c0f77",
          "links": [
              {
                  "href": "https://volume.region.xxx.xxx-tsi.de/v2/3cfb09080bd944d0b4cdd72ef26857bd/volumes/36ba39af-3579-4e6e-adfc-b764349c0f77",
                  "rel": "self"
              },
              {
                  "href": "https://volume.region.xxx.xxx-tsi.de/3cfb09080bd944d0b4cdd72ef26857bd/volumes/36ba39af-3579-4e6e-adfc-b764349c0f77",
                  "rel": "bookmark"
              }
          ],
          "name": "newVolume",
          "status": "in-use",
          "attachments": [
              {
                  "server_id": "c3d3250c-7ce5-42cc-b620-dd2b63d19ca5",
                  "attachment_id": "011a2bdb-a033-4479-845b-50bd8ed7f4d4",
                  "attached_at": "2017-05-23T11:27:38.604815",
                  "host_name": null,
                  "volume_id": "36ba39af-3579-4e6e-adfc-b764349c0f77",
                  "device": "/dev/sdf",
                  "id": "36ba39af-3579-4e6e-adfc-b764349c0f77"
              }
          ],
          "description": "new volume",
          "multiattach": false,
          "shareable": false,
          "size": 10,
          "metadata": {
              "policy": "dc71a9c9-b3fa-429d-a070-037682d82d21",
              "attached_mode": "rw",
              "readonly": "False",
              "hw:passthrough": "false"
          },
          "bootable": "false",
          "availability_zone": "az-dc-1",
          "os-vol-host-attr:host": null,
          "source_volid": null,
          "snapshot_id": null,
          "created_at": "2017-05-23T09:49:44.481299",
          "volume_type": "SATA",
          "os-vol-tenant-attr:tenant_id": null,
          "os-volume-replication:extended_status": null,
          "volume_image_metadata": null
      }

   or

   .. code-block::

      {
          "error": {
              "message": "XXXX",
              "code": "XXX"
          }
      }

Status Codes
------------

-  Normal

   200

Error Codes
-----------

For details, see :ref:`Error Codes <evs_04_0038>`.
