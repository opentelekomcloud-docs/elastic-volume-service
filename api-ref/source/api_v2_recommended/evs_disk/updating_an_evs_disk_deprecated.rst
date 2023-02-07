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

   ========== ========= ===============
   Parameter  Mandatory Description
   ========== ========= ===============
   project_id Yes       The project ID.
   volume_id  Yes       The disk ID.
   ========== ========= ===============

Request
-------

-  Request parameters

   +-----------+--------+-----------+------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Mandatory | Description                                                                                                                  |
   +===========+========+===========+==============================================================================================================================+
   | volume    | Object | Yes       | The information of the disk to be updated. For details, see :ref:`Parameters in the volume field <evs_04_2009__li44975500>`. |
   +-----------+--------+-----------+------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_2009__li44975500:

   Parameters in the **volume** field

   +-------------+--------+-----------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Type   | Mandatory | Description                                                                                                                                             |
   +=============+========+===========+=========================================================================================================================================================+
   | name        | String | No        | The new name of the disk. Parameters **name** and **description** cannot be null at the same time. The value can contain a maximum of 255 bytes.        |
   +-------------+--------+-----------+---------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description | String | No        | The new description of the disk. Parameters **name** and **description** cannot be null at the same time. The value can contain a maximum of 255 bytes. |
   +-------------+--------+-----------+---------------------------------------------------------------------------------------------------------------------------------------------------------+

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

-  Response parameters

   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                             | Type                  | Description                                                                                                                                            |
   +=======================================+=======================+========================================================================================================================================================+
   | id                                    | String                | The disk ID.                                                                                                                                           |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | links                                 | Array of objects      | The disk URI. For details, see :ref:`Parameters in the links field <evs_04_2009__li949885516582>`.                                                     |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                                  | String                | The disk name.                                                                                                                                         |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status                                | String                | The disk status. For details, see :ref:`EVS Disk Status <evs_04_0040>`.                                                                                |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | attachments                           | Array of objects      | The disk attachment information. For details, see :ref:`Parameters in the attachments field <evs_04_2009__li2847936164017>`.                           |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | availability_zone                     | String                | The AZ to which the disk belongs.                                                                                                                      |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | source_volid                          | String                | The source disk ID. This parameter has a value if the disk is created from a source disk.                                                              |
   |                                       |                       |                                                                                                                                                        |
   |                                       |                       | This field is not supported currently.                                                                                                                 |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | snapshot_id                           | String                | The snapshot ID. This parameter has a value if the disk is created from a snapshot.                                                                    |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description                           | String                | The disk description.                                                                                                                                  |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | os-vol-tenant-attr:tenant_id          | String                | The ID of the tenant to which the disk belongs. The returned value is currently invalid. The tenant ID is the same as the project ID.                  |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | volume_image_metadata                 | Object                | The metadata of the disk image. The returned value is currently invalid.                                                                               |
   |                                       |                       |                                                                                                                                                        |
   |                                       |                       | .. note::                                                                                                                                              |
   |                                       |                       |                                                                                                                                                        |
   |                                       |                       |    For details about **volume_image_metadata**, see **Querying Image Details (Native OpenStack API)** in the *Image Management Service API Reference*. |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | created_at                            | String                | The time when the disk was created.                                                                                                                    |
   |                                       |                       |                                                                                                                                                        |
   |                                       |                       | Time format: UTC YYYY-MM-DDTHH:MM:SS.XXXXXX                                                                                                            |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | volume_type                           | String                | The disk type.                                                                                                                                         |
   |                                       |                       |                                                                                                                                                        |
   |                                       |                       | The value can be **ESSD**, **SSD**, **SAS**, **SATA**, **co-p1**, or **uh-l1**.                                                                        |
   |                                       |                       |                                                                                                                                                        |
   |                                       |                       | -  **SSD**: the ultra-high I/O type                                                                                                                    |
   |                                       |                       |                                                                                                                                                        |
   |                                       |                       | -  **SAS**: the high I/O type                                                                                                                          |
   |                                       |                       |                                                                                                                                                        |
   |                                       |                       | -  **SATA**: the common I/O type                                                                                                                       |
   |                                       |                       |                                                                                                                                                        |
   |                                       |                       | -  **co-p1**: the high I/O (performance-optimized I) type                                                                                              |
   |                                       |                       |                                                                                                                                                        |
   |                                       |                       | -  **uh-l1**: the ultra-high I/O (latency-optimized) type                                                                                              |
   |                                       |                       |                                                                                                                                                        |
   |                                       |                       | -  **ESSD**: the extreme SSD type                                                                                                                      |
   |                                       |                       |                                                                                                                                                        |
   |                                       |                       |    The **co-p1** and **uh-l1** types of disks are used exclusively for HPC ECSs and SAP HANA ECSs.                                                     |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | size                                  | Integer               | The disk size, in GB.                                                                                                                                  |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | bootable                              | String                | Whether the disk is bootable.                                                                                                                          |
   |                                       |                       |                                                                                                                                                        |
   |                                       |                       | -  **true**: indicates a bootable disk.                                                                                                                |
   |                                       |                       | -  **false**: indicates a non-bootable disk.                                                                                                           |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | metadata                              | Object                | The disk metadata. For details, see :ref:`Parameters in the metadata field <evs_04_2009__li6221175494947>`.                                            |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | os-vol-host-attr:host                 | String                | The reserved field.                                                                                                                                    |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | shareable                             | String                | Whether the disk is shareable.                                                                                                                         |
   |                                       |                       |                                                                                                                                                        |
   |                                       |                       | .. note::                                                                                                                                              |
   |                                       |                       |                                                                                                                                                        |
   |                                       |                       |    This field is no longer used. Use **multiattach**.                                                                                                  |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | error                                 | Object                | The error message returned if an error occurs. For details, see :ref:`Parameters in the error field <evs_04_2009__li0419202382514>`.                   |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | multiattach                           | Boolean               | Whether the disk is shareable.                                                                                                                         |
   |                                       |                       |                                                                                                                                                        |
   |                                       |                       | -  **true**: indicates a shared disk.                                                                                                                  |
   |                                       |                       | -  **false**: indicates a non-shared disk.                                                                                                             |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | os-volume-replication:extended_status | String                | The reserved field.                                                                                                                                    |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_2009__li949885516582:

   Parameters in the **links** field

   ========= ====== ================================
   Parameter Type   Description
   ========= ====== ================================
   href      String The corresponding shortcut link.
   rel       String The shortcut link marker name.
   ========= ====== ================================

-  .. _evs_04_2009__li2847936164017:

   Parameters in the **attachments** field

   +-----------------------+-----------------------+---------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                           |
   +=======================+=======================+=======================================================================================+
   | server_id             | String                | The ID of the server to which the disk is attached.                                   |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------+
   | attachment_id         | String                | The ID of the attachment information.                                                 |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------+
   | attached_at           | String                | The time when the disk was attached.                                                  |
   |                       |                       |                                                                                       |
   |                       |                       | Time format: UTC YYYY-MM-DDTHH:MM:SS.XXXXXX                                           |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------+
   | host_name             | String                | The name of the physical host housing the cloud server to which the disk is attached. |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------+
   | volume_id             | String                | The disk ID.                                                                          |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------+
   | device                | String                | The device name.                                                                      |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------+
   | id                    | String                | The ID of the attached disk.                                                          |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------+

-  .. _evs_04_2009__li6221175494947:

   Parameters in the **metadata** field

   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                        |
   +=======================+=======================+====================================================================================================================================================================+
   | \__system__encrypted  | String                | The encryption field in **metadata**.                                                                                                                              |
   |                       |                       |                                                                                                                                                                    |
   |                       |                       | -  **0**: indicates a non-encrypted disk.                                                                                                                          |
   |                       |                       | -  **1**: indicates an encrypted disk.                                                                                                                             |
   |                       |                       | -  If this parameter does not appear, the disk is not encrypted.                                                                                                   |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | \__system__cmkid      | String                | The encryption CMK ID in **metadata**. This parameter is used together with **\__system__encrypted** for encryption. The length of **cmkid** is fixed at 36 bytes. |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | hw:passthrough        | String                | The parameter that describes the disk device type in **metadata**. The value can be **true** or **false**.                                                         |
   |                       |                       |                                                                                                                                                                    |
   |                       |                       | -  **true** indicates the SCSI device type, which allows ECS OSs to directly access the underlying storage media. SCSI reservation commands are supported.         |
   |                       |                       | -  **false** indicates the Virtual Block Device (VBD) device type (the default type), which supports only simple SCSI read/write commands.                         |
   |                       |                       | -  If this parameter does not appear, the disk device type is VBD.                                                                                                 |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | full_clone            | String                | The clone method. If the disk is created from a snapshot, value **0** indicates the linked cloning method.                                                         |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_2009__li0419202382514:

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
          "volume_type": "SAS",
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
