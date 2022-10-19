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

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   ========== ========= =========================

Request
-------

-  Parameter description

   +-----------+--------+-----------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Mandatory | Description                                                                                                                                         |
   +===========+========+===========+=====================================================================================================================================================+
   | volume    | Object | Yes       | Specifies the information of the disks to be created. For details, see :ref:`Parameters in the volume field <evs_04_3029__evs_04_2065_li10966323>`. |
   +-----------+--------+-----------+-----------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_3029__evs_04_2065_li10966323:

   Parameters in the **volume** field

   +---------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter           | Type            | Mandatory       | Description                                                                                                                                                                                                                     |
   +=====================+=================+=================+=================================================================================================================================================================================================================================+
   | availability_zone   | String          | Yes             | Specifies the AZ where you want to create the disk. If the AZ does not exist, the disk will fail to create.                                                                                                                     |
   |                     |                 |                 |                                                                                                                                                                                                                                 |
   |                     |                 |                 | .. note::                                                                                                                                                                                                                       |
   |                     |                 |                 |                                                                                                                                                                                                                                 |
   |                     |                 |                 |    For details about how to obtain the AZ, see :ref:`Querying All AZs <evs_04_2081>`.                                                                                                                                           |
   +---------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | source_volid        | String          | No              | Specifies the source disk ID. If this parameter is specified, the disk is cloned from an existing disk. Currently, this function is not supported.                                                                              |
   +---------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description         | String          | No              | Specifies the disk description. The value can contain a maximum of 255 bytes.                                                                                                                                                   |
   +---------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | snapshot_id         | String          | No              | Specifies the snapshot ID. If this parameter is specified, the disk is created from a snapshot.                                                                                                                                 |
   |                     |                 |                 |                                                                                                                                                                                                                                 |
   |                     |                 |                 | .. note::                                                                                                                                                                                                                       |
   |                     |                 |                 |                                                                                                                                                                                                                                 |
   |                     |                 |                 |    For details about how to obtain the snapshot ID, see :ref:`Querying Details About EVS Snapshots <evs_04_2097>`.                                                                                                              |
   +---------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | size                | Integer         | Yes             | Specifies the disk size, in GB. Its value can be as follows:                                                                                                                                                                    |
   |                     |                 |                 |                                                                                                                                                                                                                                 |
   |                     |                 |                 | -  System disk: 1 GB to 1024 GB                                                                                                                                                                                                 |
   |                     |                 |                 | -  Data disk: 10 GB to 32768 GB                                                                                                                                                                                                 |
   |                     |                 |                 |                                                                                                                                                                                                                                 |
   |                     |                 |                 | This parameter is mandatory when you create an empty disk. You can specify the parameter value as required within the value range.                                                                                              |
   |                     |                 |                 |                                                                                                                                                                                                                                 |
   |                     |                 |                 | This parameter is mandatory when you create the disk from a snapshot. Ensure that the disk size is greater than or equal to the snapshot size.                                                                                  |
   |                     |                 |                 |                                                                                                                                                                                                                                 |
   |                     |                 |                 | This parameter is mandatory when you create the disk from an image. Ensure that the disk size is greater than or equal to the minimum disk capacity required by **min_disk** in the image attributes.                           |
   +---------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                | String          | No              | Specifies the disk name. The value can contain a maximum of 255 bytes.                                                                                                                                                          |
   +---------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | imageRef            | String          | No              | Specifies the image ID. If this parameter is specified, the disk is created from an image.                                                                                                                                      |
   |                     |                 |                 |                                                                                                                                                                                                                                 |
   |                     |                 |                 | .. note::                                                                                                                                                                                                                       |
   |                     |                 |                 |                                                                                                                                                                                                                                 |
   |                     |                 |                 |    BMS system disks cannot be created from BMS images.                                                                                                                                                                          |
   |                     |                 |                 |                                                                                                                                                                                                                                 |
   |                     |                 |                 |    For how to obtain the image ID, see **Querying Images** in the *Image Management Service API Reference*.                                                                                                                     |
   +---------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | volume_type         | String          | No              | Specifies the disk type.                                                                                                                                                                                                        |
   |                     |                 |                 |                                                                                                                                                                                                                                 |
   |                     |                 |                 | Currently, the value can be **SSD**, **SAS**, **SATA**, **co-p1**, or **uh-l1**.                                                                                                                                                |
   |                     |                 |                 |                                                                                                                                                                                                                                 |
   |                     |                 |                 | -  **SSD**: specifies the ultra-high I/O disk type.                                                                                                                                                                             |
   |                     |                 |                 |                                                                                                                                                                                                                                 |
   |                     |                 |                 | -  **SAS**: specifies the high I/O disk type.                                                                                                                                                                                   |
   |                     |                 |                 |                                                                                                                                                                                                                                 |
   |                     |                 |                 | -  **SATA**: specifies the common I/O disk type.                                                                                                                                                                                |
   |                     |                 |                 |                                                                                                                                                                                                                                 |
   |                     |                 |                 | -  **co-p1**: specifies the high I/O (performance-optimized I) disk type.                                                                                                                                                       |
   |                     |                 |                 |                                                                                                                                                                                                                                 |
   |                     |                 |                 | -  **uh-l1**: specifies the ultra-high I/O (latency-optimized) disk type.                                                                                                                                                       |
   |                     |                 |                 |                                                                                                                                                                                                                                 |
   |                     |                 |                 |    Disks of the **co-p1** and **uh-l1** types are used exclusively for HPC ECSs and SAP HANA ECSs.                                                                                                                              |
   |                     |                 |                 |                                                                                                                                                                                                                                 |
   |                     |                 |                 | If the specified disk type is not available in the AZ, the disk will fail to create.                                                                                                                                            |
   |                     |                 |                 |                                                                                                                                                                                                                                 |
   |                     |                 |                 | .. note::                                                                                                                                                                                                                       |
   |                     |                 |                 |                                                                                                                                                                                                                                 |
   |                     |                 |                 |    -  If the disk is created from a snapshot, the volume_type field must be the same as that of the snapshot's source disk.                                                                                                     |
   |                     |                 |                 |    -  For details about disk types, see **Disk Types and Disk Performance** in the *Elastic Volume Service User Guide*.                                                                                                         |
   +---------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | metadata            | Object          | No              | Specifies the disk metadata. The length of the key or value in the metadata cannot exceed 255 bytes.                                                                                                                            |
   |                     |                 |                 |                                                                                                                                                                                                                                 |
   |                     |                 |                 | For details about **metadata**, see :ref:`Parameters in the metadata field <evs_04_3029__evs_04_2065_li4145283210319>`. The table lists some fields. You can also specify other fields based on the disk creation requirements. |
   |                     |                 |                 |                                                                                                                                                                                                                                 |
   |                     |                 |                 | .. note::                                                                                                                                                                                                                       |
   |                     |                 |                 |                                                                                                                                                                                                                                 |
   |                     |                 |                 |    Parameter values under **metadata** cannot be **null**.                                                                                                                                                                      |
   +---------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | source_replica      | String          | No              | Specifies the source disk ID. If this parameter is specified, the disk is cloned from an existing disk. Currently, this function is not supported.                                                                              |
   +---------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | consistencygroup_id | String          | No              | Reserved field                                                                                                                                                                                                                  |
   +---------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | shareable           | String          | No              | Specifies whether the disk is shareable. The value can be **true** (sharable) or **false** (not sharable). This is an extended attribute.                                                                                       |
   |                     |                 |                 |                                                                                                                                                                                                                                 |
   |                     |                 |                 | .. note::                                                                                                                                                                                                                       |
   |                     |                 |                 |                                                                                                                                                                                                                                 |
   |                     |                 |                 |    This field is no longer used. Use **multiattach**.                                                                                                                                                                           |
   +---------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | multiattach         | Boolean         | No              | Specifies whether the disk is shareable. The default value is **false**.                                                                                                                                                        |
   |                     |                 |                 |                                                                                                                                                                                                                                 |
   |                     |                 |                 | -  **true**: specifies a shared disk.                                                                                                                                                                                           |
   |                     |                 |                 | -  **false**: specifies a non-shared disk.                                                                                                                                                                                      |
   +---------------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. note::

      Specifying either two of the **source_volid**, **snapshot_id**, and **imageRef** fields is not supported.

-  .. _evs_04_3029__evs_04_2065_li4145283210319:

   Parameters in the **metadata** field

   +----------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter            | Type            | Mandatory       | Description                                                                                                                                                                                                                          |
   +======================+=================+=================+======================================================================================================================================================================================================================================+
   | \__system__encrypted | String          | No              | Specifies the encryption field in **metadata**. The value can be **0** (not encrypted) or **1** (encrypted).                                                                                                                         |
   |                      |                 |                 |                                                                                                                                                                                                                                      |
   |                      |                 |                 | If this parameter does not exist, the disk will not be encrypted by default.                                                                                                                                                         |
   +----------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | \__system__cmkid     | String          | No              | Specifies the encryption CMK ID in **metadata**. This parameter is used together with **\__system__encrypted** for encryption. The length of **cmkid** is fixed at 36 bytes.                                                         |
   |                      |                 |                 |                                                                                                                                                                                                                                      |
   |                      |                 |                 | .. note::                                                                                                                                                                                                                            |
   |                      |                 |                 |                                                                                                                                                                                                                                      |
   |                      |                 |                 |    For details about how to obtain the CMK ID, see **Querying the List of CMKs** in the *Key Management Service API Reference*.                                                                                                      |
   +----------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | hw:passthrough       | String          | No              | -  If this parameter is set to **true**, the disk device type is SCSI, that is, Small Computer System Interface (SCSI), which allows ECS OSs to directly access the underlying storage media and supports SCSI reservation commands. |
   |                      |                 |                 | -  If this parameter is set to **false**, the disk device type will be VBD, which supports only simple SCSI read/write commands.                                                                                                     |
   |                      |                 |                 | -  If this parameter does not appear, the disk device type is VBD.                                                                                                                                                                   |
   |                      |                 |                 |                                                                                                                                                                                                                                      |
   |                      |                 |                 |    .. note::                                                                                                                                                                                                                         |
   |                      |                 |                 |                                                                                                                                                                                                                                      |
   |                      |                 |                 |       If parameter **shareable** is set to **true** and parameter **hw:passthrough** is not specified, shared VBD disks are created.                                                                                                 |
   +----------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | full_clone           | String          | No              | If the disk is created from a snapshot and linked cloning needs to be used, set this parameter to **0**.                                                                                                                             |
   +----------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. note::

      The preceding table provides only some parameters in **metadata** for your reference. You can also specify other fields based on the disk creation requirements.

      -  If the disk is created from a snapshot, **\__system__encrypted** and **\__system__cmkid** are not supported, and the newly created disk has the same encryption attribute as that of the snapshot's source disk.
      -  If the disk is created from an image, **\__system__encrypted** and **\__system__cmkid** are not supported, and the newly created disk has the same encryption attribute as that of the image.
      -  If the disk is created from a snapshot, **hw:passthrough** is not supported, and the newly created disk has the same device type as that of the snapshot's source disk.
      -  If the disk is created from an image, **hw:passthrough** is not supported, and the device type of newly created disk is VBD.

-  Example request

   .. code-block::

      {
          "volume": {
              "name": "openapi_vol01",
              "imageRef": "027cf713-45a6-45f0-ac1b-0ccc57ac12e2",
              "availability_zone": "az-dc-1",
              "description": "create for api test",
              "volume_type": "SATA",
              "metadata": {
                  "volume_owner": "openapi"
              },
              "multiattach": false,
              "size": 40
          },
      }

Response
--------

-  Parameter description

   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                                                                                  |
   +===========+========+==============================================================================================================================================================+
   | volume    | Object | Specifies the information of the created disks. For details, see :ref:`Parameters in the volumes field <evs_04_3029__evs_04_2065_li3451542201439>`.          |
   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | error     | Object | Specifies the error message returned when an error occurs. For details, see :ref:`Parameters in the error field <evs_04_3029__evs_04_2065_li0419202382514>`. |
   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_3029__evs_04_2065_li3451542201439:

   Parameters in the **volumes** field

   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                        |
   +=======================+=======================+====================================================================================================================================================+
   | id                    | String                | Specifies the disk ID.                                                                                                                             |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+
   | links                 | list                  | Specifies the disk URI. For details, see :ref:`Parameters in the links field <evs_04_3029__evs_04_2065_li1043159617124>`.                          |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                  | String                | Specifies the disk name.                                                                                                                           |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+
   | status                | String                | Specifies the disk status. For details, see :ref:`EVS Disk Status <evs_04_0040>`.                                                                  |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+
   | attachments           | list                  | Specifies the disk attachment information. For details, see :ref:`Parameters in the attachments field <evs_04_3029__evs_04_2065_li3900093617124>`. |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+
   | availability_zone     | String                | Specifies the AZ to which the disk belongs.                                                                                                        |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+
   | bootable              | String                | Specifies whether the disk is bootable.                                                                                                            |
   |                       |                       |                                                                                                                                                    |
   |                       |                       | -  **true**: specifies a bootable disk.                                                                                                            |
   |                       |                       | -  **false**: specifies a non-bootable disk.                                                                                                       |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+
   | encrypted             | Boolean               | Currently, this field is not supported by EVS.                                                                                                     |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+
   | created_at            | String                | Specifies the time when the disk was created.                                                                                                      |
   |                       |                       |                                                                                                                                                    |
   |                       |                       | Time format: UTC YYYY-MM-DDTHH:MM:SS.XXXXXX                                                                                                        |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+
   | description           | String                | Specifies the disk description.                                                                                                                    |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+
   | volume_type           | String                | Specifies the disk type.                                                                                                                           |
   |                       |                       |                                                                                                                                                    |
   |                       |                       | Currently, the value can be **SSD**, **SAS**, **SATA**, **co-p1**, or **uh-l1**.                                                                   |
   |                       |                       |                                                                                                                                                    |
   |                       |                       | -  **SSD**: specifies the ultra-high I/O disk type.                                                                                                |
   |                       |                       |                                                                                                                                                    |
   |                       |                       | -  **SAS**: specifies the high I/O disk type.                                                                                                      |
   |                       |                       |                                                                                                                                                    |
   |                       |                       | -  **SATA**: specifies the common I/O disk type.                                                                                                   |
   |                       |                       |                                                                                                                                                    |
   |                       |                       | -  **co-p1**: specifies the high I/O (performance-optimized I) disk type.                                                                          |
   |                       |                       |                                                                                                                                                    |
   |                       |                       | -  **uh-l1**: specifies the ultra-high I/O (latency-optimized) disk type.                                                                          |
   |                       |                       |                                                                                                                                                    |
   |                       |                       |    Disks of the **co-p1** and **uh-l1** types are used exclusively for HPC ECSs and SAP HANA ECSs.                                                 |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+
   | replication_status    | String                | Reserved field                                                                                                                                     |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+
   | consistencygroup_id   | String                | Specifies the ID of the consistency group where the disk belongs.                                                                                  |
   |                       |                       |                                                                                                                                                    |
   |                       |                       | Currently, this field is not supported by EVS.                                                                                                     |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+
   | source_volid          | String                | Specifies the source disk ID.                                                                                                                      |
   |                       |                       |                                                                                                                                                    |
   |                       |                       | Currently, this field is not supported by EVS.                                                                                                     |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+
   | snapshot_id           | String                | Specifies the snapshot ID.                                                                                                                         |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+
   | metadata              | Object                | Specifies the disk metadata. For details, see :ref:`Parameters in the metadata field <evs_04_3029__evs_04_2065_li29114110314>`.                    |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+
   | size                  | Integer               | Specifies the disk size, in GB.                                                                                                                    |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+
   | user_id               | String                | Reserved field                                                                                                                                     |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+
   | updated_at            | String                | Specifies the time when the disk was updated.                                                                                                      |
   |                       |                       |                                                                                                                                                    |
   |                       |                       | Time format: UTC YYYY-MM-DDTHH:MM:SS.XXXXXX                                                                                                        |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+
   | shareable             | Boolean               | Specifies whether the disk is shareable.                                                                                                           |
   |                       |                       |                                                                                                                                                    |
   |                       |                       | .. note::                                                                                                                                          |
   |                       |                       |                                                                                                                                                    |
   |                       |                       |    This field is no longer used. Use **multiattach**.                                                                                              |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+
   | multiattach           | Boolean               | Specifies whether the disk is shareable.                                                                                                           |
   |                       |                       |                                                                                                                                                    |
   |                       |                       | -  **true**: specifies a shared disk.                                                                                                              |
   |                       |                       | -  **false**: specifies a non-shared disk.                                                                                                         |
   +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_3029__evs_04_2065_li1043159617124:

   Parameters in the **links** field

   ========= ====== ==========================================
   Parameter Type   Description
   ========= ====== ==========================================
   href      String Specifies the corresponding shortcut link.
   rel       String Specifies the shortcut link marker name.
   ========= ====== ==========================================

-  .. _evs_04_3029__evs_04_2065_li3900093617124:

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

-  .. _evs_04_3029__evs_04_2065_li29114110314:

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

-  .. _evs_04_3029__evs_04_2065_li0419202382514:

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

Status Codes
------------

-  Normal

   202

Error Codes
-----------

For details, see :ref:`Error Codes <evs_04_0038>`.
