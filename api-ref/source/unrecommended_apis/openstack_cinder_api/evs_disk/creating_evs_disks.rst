:original_name: evs_04_3029.html

.. _evs_04_3029:

Creating EVS Disks
==================

Function
--------

This API is used to create one or multiple EVS disks.

URI
---

-  URI format

   POST /v3/{project_id}/volumes

-  Parameter description

   ========== ========= ===============
   Parameter  Mandatory Description
   ========== ========= ===============
   project_id Yes       The project ID.
   ========== ========= ===============

Request
-------

-  Request parameters

   +-----------+--------+-----------+------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Mandatory | Description                                                                                                                              |
   +===========+========+===========+==========================================================================================================================================+
   | volume    | Object | Yes       | The information of the disk to be created. For details, see :ref:`Parameters in the volume field <evs_04_3029__evs_04_2065_li10966323>`. |
   +-----------+--------+-----------+------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_3029__evs_04_2065_li10966323:

   Parameters in the **volume** field

   +---------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter           | Type            | Mandatory       | Description                                                                                                                                                                                                                                                                     |
   +=====================+=================+=================+=================================================================================================================================================================================================================================================================================+
   | availability_zone   | String          | Yes             | The AZ where you want to create the disk. If the specified AZ does not exist, the disk will fail to be created.                                                                                                                                                                 |
   |                     |                 |                 |                                                                                                                                                                                                                                                                                 |
   |                     |                 |                 | .. note::                                                                                                                                                                                                                                                                       |
   |                     |                 |                 |                                                                                                                                                                                                                                                                                 |
   |                     |                 |                 |    For details about how to obtain the AZ, see :ref:`Querying All AZs <evs_04_2081>`.                                                                                                                                                                                           |
   +---------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | source_volid        | String          | No              | The source disk ID. If this parameter is specified, the disk will be cloned from an existing disk. This function is currently not supported.                                                                                                                                    |
   +---------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description         | String          | No              | The disk description, which can contain a maximum of 255 bytes.                                                                                                                                                                                                                 |
   +---------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | snapshot_id         | String          | No              | The snapshot ID. If this parameter is specified, the disk will be created from a snapshot.                                                                                                                                                                                      |
   |                     |                 |                 |                                                                                                                                                                                                                                                                                 |
   |                     |                 |                 | .. note::                                                                                                                                                                                                                                                                       |
   |                     |                 |                 |                                                                                                                                                                                                                                                                                 |
   |                     |                 |                 |    For details about how to obtain the snapshot ID, see :ref:`Querying Details About EVS Snapshots <evs_04_3060>`.                                                                                                                                                              |
   +---------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | size                | Integer         | Yes             | The disk size, in GB. The value can be as follows:                                                                                                                                                                                                                              |
   |                     |                 |                 |                                                                                                                                                                                                                                                                                 |
   |                     |                 |                 | -  System disk: 1 GB to 1024 GB                                                                                                                                                                                                                                                 |
   |                     |                 |                 | -  Data disk: 10 GB to 32768 GB                                                                                                                                                                                                                                                 |
   |                     |                 |                 |                                                                                                                                                                                                                                                                                 |
   |                     |                 |                 | This parameter is mandatory when you create an empty disk. You can specify the parameter value as required within the value range.                                                                                                                                              |
   |                     |                 |                 |                                                                                                                                                                                                                                                                                 |
   |                     |                 |                 | This parameter is mandatory when you create the disk from a snapshot. Ensure that the disk size is greater than or equal to the snapshot size.                                                                                                                                  |
   |                     |                 |                 |                                                                                                                                                                                                                                                                                 |
   |                     |                 |                 | This parameter is mandatory when you create the disk from an image. Ensure that the disk size is greater than or equal to the minimum disk capacity required by **min_disk** in the image attributes.                                                                           |
   +---------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                | String          | No              | The disk name, which can contain a maximum of 255 bytes.                                                                                                                                                                                                                        |
   +---------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | imageRef            | String          | No              | The image ID. If this parameter is specified, the disk will be created from an image.                                                                                                                                                                                           |
   |                     |                 |                 |                                                                                                                                                                                                                                                                                 |
   |                     |                 |                 | .. note::                                                                                                                                                                                                                                                                       |
   |                     |                 |                 |                                                                                                                                                                                                                                                                                 |
   |                     |                 |                 |    BMS system disks cannot be created from BMS images.                                                                                                                                                                                                                          |
   |                     |                 |                 |                                                                                                                                                                                                                                                                                 |
   |                     |                 |                 |    For how to obtain the image ID, see **Querying Images** in the *Image Management Service API Reference*.                                                                                                                                                                     |
   +---------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | volume_type         | String          | No              | The disk type.                                                                                                                                                                                                                                                                  |
   |                     |                 |                 |                                                                                                                                                                                                                                                                                 |
   |                     |                 |                 | The value can be **ESSD**, **GPSSD**, **SSD**, **SAS**, or **SATA**.                                                                                                                                                                                                            |
   |                     |                 |                 |                                                                                                                                                                                                                                                                                 |
   |                     |                 |                 | -  **SSD**: the ultra-high I/O type                                                                                                                                                                                                                                             |
   |                     |                 |                 | -  **SAS**: the high I/O type                                                                                                                                                                                                                                                   |
   |                     |                 |                 | -  **SATA**: the common I/O type                                                                                                                                                                                                                                                |
   |                     |                 |                 | -  **GPSSD**: the general purpose SSD type                                                                                                                                                                                                                                      |
   |                     |                 |                 | -  **ESSD**: the extreme SSD type                                                                                                                                                                                                                                               |
   |                     |                 |                 |                                                                                                                                                                                                                                                                                 |
   |                     |                 |                 | If the specified disk type is not available in the AZ, the disk will fail to be created.                                                                                                                                                                                        |
   |                     |                 |                 |                                                                                                                                                                                                                                                                                 |
   |                     |                 |                 | .. note::                                                                                                                                                                                                                                                                       |
   |                     |                 |                 |                                                                                                                                                                                                                                                                                 |
   |                     |                 |                 |    -  When the disk is created from a snapshot, the disk type of the new disk will be consistent with that of the snapshot's source disk.                                                                                                                                       |
   |                     |                 |                 |    -  For details about disk types, see **Disk Types and Performance** in the *Elastic Volume Service User Guide*.                                                                                                                                                              |
   +---------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | metadata            | Object          | No              | The disk metadata. The length of **key** and **value** under **metadata** can contain no more than 255 bytes.                                                                                                                                                                   |
   |                     |                 |                 |                                                                                                                                                                                                                                                                                 |
   |                     |                 |                 | For details about **metadata**, see :ref:`Parameters in the metadata field <evs_04_3029__evs_04_2065_li4145283210319>`. The table lists some fields. You can also specify other fields as required.                                                                             |
   |                     |                 |                 |                                                                                                                                                                                                                                                                                 |
   |                     |                 |                 | .. note::                                                                                                                                                                                                                                                                       |
   |                     |                 |                 |                                                                                                                                                                                                                                                                                 |
   |                     |                 |                 |    Parameter values under **metadata** cannot be **null**.                                                                                                                                                                                                                      |
   +---------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | source_replica      | String          | No              | The source disk ID. If this parameter is specified, the disk will be cloned from an existing disk. This function is currently not supported.                                                                                                                                    |
   +---------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | consistencygroup_id | String          | No              | The reserved field.                                                                                                                                                                                                                                                             |
   +---------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | count               | No              | Integer         | The number of disks to be created in a batch. If this parameter is not specified, only one disk will be created. You can create a maximum of 100 disks in a batch. If disks are created from backups, batch creation is not supported, and this parameter must be set to **1**. |
   |                     |                 |                 |                                                                                                                                                                                                                                                                                 |
   |                     |                 |                 | If the specified value is a decimal, the number part of the value will be used.                                                                                                                                                                                                 |
   +---------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | shareable           | String          | No              | The extended attribute that defines whether the disk will be shareable. The value can be **true** (shareable) or **false** (not shareable). This field is currently not supported.                                                                                              |
   |                     |                 |                 |                                                                                                                                                                                                                                                                                 |
   |                     |                 |                 | .. note::                                                                                                                                                                                                                                                                       |
   |                     |                 |                 |                                                                                                                                                                                                                                                                                 |
   |                     |                 |                 |    This field is no longer used. Use **multiattach**.                                                                                                                                                                                                                           |
   +---------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | multiattach         | Boolean         | No              | Whether the disk is shareable. The default value is **false**.                                                                                                                                                                                                                  |
   |                     |                 |                 |                                                                                                                                                                                                                                                                                 |
   |                     |                 |                 | -  **true**: indicates a shared disk.                                                                                                                                                                                                                                           |
   |                     |                 |                 | -  **false**: indicates a non-shared disk.                                                                                                                                                                                                                                      |
   +---------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. note::

      Specifying any two of the **source_volid**, **snapshot_id**, and **imageRef** fields together is not supported.

-  .. _evs_04_3029__evs_04_2065_li4145283210319:

   Parameters in the **metadata** field

   +----------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter            | Type            | Mandatory       | Description                                                                                                                                                                              |
   +======================+=================+=================+==========================================================================================================================================================================================+
   | \__system__encrypted | String          | No              | The encryption field in **metadata**. The value can be **0** (does not encrypt the disk) or **1** (encrypts the disk).                                                                   |
   |                      |                 |                 |                                                                                                                                                                                          |
   |                      |                 |                 | If this parameter is not specified, the disk will not be encrypted.                                                                                                                      |
   +----------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | \__system__cmkid     | String          | No              | The encryption CMK ID in **metadata**. This parameter is used together with **\__system__encrypted** for encryption. The length of **cmkid** is fixed at 36 bytes.                       |
   |                      |                 |                 |                                                                                                                                                                                          |
   |                      |                 |                 | .. note::                                                                                                                                                                                |
   |                      |                 |                 |                                                                                                                                                                                          |
   |                      |                 |                 |    For details about how to obtain the CMK ID, see **Querying the Key List** in the *Key Management Service API Reference*.                                                              |
   +----------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | hw:passthrough       | String          | No              | -  If this parameter is set to **true**, the disk device type will be SCSI, which allows ECS OSs to directly access the underlying storage media and supports SCSI reservation commands. |
   |                      |                 |                 | -  If this parameter is set to **false**, the disk device type will be VBD, which supports only simple SCSI read/write commands.                                                         |
   |                      |                 |                 | -  If this parameter is not specified, the disk device type will be VBD.                                                                                                                 |
   |                      |                 |                 |                                                                                                                                                                                          |
   |                      |                 |                 |    .. note::                                                                                                                                                                             |
   |                      |                 |                 |                                                                                                                                                                                          |
   |                      |                 |                 |       If parameter **shareable** is set to **true** and parameter **hw:passthrough** is not specified, shared VBD disks are created.                                                     |
   +----------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | full_clone           | String          | No              | If the disk is created from a snapshot and linked cloning needs to be used, set this parameter to **0**.                                                                                 |
   +----------------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. note::

      The preceding table provides only some **metadata** parameters for your reference. You can also specify other fields as required.

      -  If the disk is created from a snapshot, **\__system__encrypted** and **\__system__cmkid** are not supported, and the new disk will have the same encryption attribute as that of the snapshot's source disk.
      -  If the disk is created from an image, **\__system__encrypted** and **\__system__cmkid** are not supported, and the new disk will have the same encryption attribute as that of the image.
      -  If the disk is created from a snapshot, **hw:passthrough** is not supported, and the new disk will have the same device type as that of the snapshot's source disk.
      -  If the disk is created from an image, **hw:passthrough** is not supported, and the device type of the new disk will be VBD.

-  Example request

   .. code-block::

      {
          "volume": {
              "name": "openapi_vol01",
              "imageRef": "027cf713-45a6-45f0-ac1b-0ccc57ac12e2",
              "availability_zone": "az-dc-1",
              "description": "create for api test",
              "volume_type": "SAS",
              "metadata": {
                  "volume_owner": "openapi"
              },
              "multiattach": false,
              "size": 40
          },
      }

Response
--------

-  Response parameters

   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                                                                      |
   +===========+========+==================================================================================================================================================+
   | volume    | Object | The information of the created disks. For details, see :ref:`Parameters in the volume field <evs_04_3029__evs_04_2065_li3451542201439>`.         |
   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | error     | Object | The error message returned if an error occurs. For details, see :ref:`Parameters in the error field <evs_04_3029__evs_04_2065_li0419202382514>`. |
   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_3029__evs_04_2065_li3451542201439:

   Parameters in the **volume** field

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                              |
   +=======================+=======================+==========================================================================================================================================+
   | id                    | String                | The disk ID.                                                                                                                             |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | links                 | list                  | The disk URI. For details, see :ref:`Parameters in the links field <evs_04_3029__evs_04_2065_li1043159617124>`.                          |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | name                  | String                | The disk name.                                                                                                                           |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | status                | String                | The disk status. For details, see :ref:`EVS Disk Status <evs_04_0040>`.                                                                  |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | attachments           | list                  | The disk attachment information. For details, see :ref:`Parameters in the attachments field <evs_04_3029__evs_04_2065_li3900093617124>`. |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | availability_zone     | String                | The AZ to which the disk belongs.                                                                                                        |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | bootable              | String                | Whether the disk is bootable.                                                                                                            |
   |                       |                       |                                                                                                                                          |
   |                       |                       | -  **true**: indicates a bootable disk.                                                                                                  |
   |                       |                       | -  **false**: indicates a non-bootable disk.                                                                                             |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | encrypted             | Boolean               | This field is currently not supported.                                                                                                   |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | created_at            | String                | The time when the disk was created.                                                                                                      |
   |                       |                       |                                                                                                                                          |
   |                       |                       | Time format: UTC YYYY-MM-DDTHH:MM:SS.XXXXXX                                                                                              |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | description           | String                | The disk description.                                                                                                                    |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | volume_type           | String                | The disk type.                                                                                                                           |
   |                       |                       |                                                                                                                                          |
   |                       |                       | The value can be **ESSD**, **GPSSD**, **SSD**, **SAS**, or **SATA**.                                                                     |
   |                       |                       |                                                                                                                                          |
   |                       |                       | -  **SSD**: the ultra-high I/O type                                                                                                      |
   |                       |                       | -  **SAS**: the high I/O type                                                                                                            |
   |                       |                       | -  **SATA**: the common I/O type                                                                                                         |
   |                       |                       | -  **GPSSD**: the general purpose SSD type                                                                                               |
   |                       |                       | -  **ESSD**: the extreme SSD type                                                                                                        |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | replication_status    | String                | The reserved field.                                                                                                                      |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | consistencygroup_id   | String                | The ID of the consistency group where the disk belongs.                                                                                  |
   |                       |                       |                                                                                                                                          |
   |                       |                       | This field is currently not supported.                                                                                                   |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | source_volid          | String                | The source disk ID.                                                                                                                      |
   |                       |                       |                                                                                                                                          |
   |                       |                       | This field is currently not supported.                                                                                                   |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | snapshot_id           | String                | The snapshot ID.                                                                                                                         |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | metadata              | Object                | The disk metadata. For details, see :ref:`Parameters in the metadata field <evs_04_3029__evs_04_2065_li29114110314>`.                    |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | size                  | Integer               | The disk size, in GB.                                                                                                                    |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | user_id               | String                | The reserved field.                                                                                                                      |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | updated_at            | String                | The time when the disk was updated.                                                                                                      |
   |                       |                       |                                                                                                                                          |
   |                       |                       | Time format: UTC YYYY-MM-DDTHH:MM:SS.XXXXXX                                                                                              |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | shareable             | Boolean               | Whether the disk is shareable.                                                                                                           |
   |                       |                       |                                                                                                                                          |
   |                       |                       | .. note::                                                                                                                                |
   |                       |                       |                                                                                                                                          |
   |                       |                       |    This field is no longer used. Use **multiattach**.                                                                                    |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | multiattach           | Boolean               | Whether the disk is shareable.                                                                                                           |
   |                       |                       |                                                                                                                                          |
   |                       |                       | -  **true**: indicates a shared disk.                                                                                                    |
   |                       |                       | -  **false**: indicates a non-shared disk.                                                                                               |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+
   | storage_cluster_id    | String                | The reserved field.                                                                                                                      |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_3029__evs_04_2065_li1043159617124:

   Parameters in the **links** field

   ========= ====== ================================
   Parameter Type   Description
   ========= ====== ================================
   href      String The corresponding shortcut link.
   rel       String The shortcut link marker name.
   ========= ====== ================================

-  .. _evs_04_3029__evs_04_2065_li3900093617124:

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

-  .. _evs_04_3029__evs_04_2065_li29114110314:

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
   |                       |                       | -  **false** indicates the VBD device type (the default type), which supports only simple SCSI read/write commands.                                                |
   |                       |                       | -  If this parameter does not appear, the disk device type is VBD.                                                                                                 |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | full_clone            | String                | The clone method. If the disk is created from a snapshot, value **0** indicates the linked cloning method.                                                         |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_3029__evs_04_2065_li0419202382514:

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
          "volume": {
              "attachments": [ ],
              "availability_zone": "az-dc-1",
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
              "multiattach": false,
              "size": 40,
              "snapshot_id": null,
              "source_volid": null,
              "status": "creating",
              "updated_at": null,
              "user_id": "39f6696ae23740708d0f358a253c2637",
              "volume_type": "SAS"
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

Status Codes
------------

-  Normal

   202

Error Codes
-----------

For details, see :ref:`Error Codes <evs_04_0038>`.
