:original_name: evs_04_2005.html

.. _evs_04_2005:

Querying Details About All Disks
================================

Function
--------

This API is used to query details about all disks.

URI
---

-  URI format

   GET /v2/{project_id}/cloudvolumes/detail

-  Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   ========== ========= =========================

-  Request filter parameters

   +-------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter         | Type            | Mandatory       | Description                                                                                                                                                                      |
   +===================+=================+=================+==================================================================================================================================================================================+
   | marker            | String          | No              | Specifies the ID of the last record on the previous page. The returned value is the value of the item after this one.                                                            |
   +-------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name              | String          | No              | Specifies the disk name. The value can contain a maximum of 255 bytes.                                                                                                           |
   +-------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status            | String          | No              | Specifies the disk status. For details, see :ref:`EVS Disk Status <evs_04_0040>`.                                                                                                |
   +-------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit             | Integer         | No              | Specifies the maximum number of query results that can be returned.                                                                                                              |
   |                   |                 |                 |                                                                                                                                                                                  |
   |                   |                 |                 | The value ranges from 1 to 1000, and the default value is 1000. The returned value cannot exceed this limit.                                                                     |
   +-------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | availability_zone | String          | No              | Specifies the AZ.                                                                                                                                                                |
   +-------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sort_key          | String          | No              | Specifies the keyword based on which the returned results are sorted. The value can be **id**, **status**, **size**, or **created_at**, and the default value is **created_at**. |
   +-------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sort_dir          | String          | No              | Specifies the result sorting order. The default value is **desc**.                                                                                                               |
   |                   |                 |                 |                                                                                                                                                                                  |
   |                   |                 |                 | -  **desc**: indicates the descending order.                                                                                                                                     |
   |                   |                 |                 | -  **asc**: indicates the ascending order.                                                                                                                                       |
   +-------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request
-------

The following example shows how to query the disks in the **available** state.

-  Example request

   .. code-block:: text

      GET https://{endpoint}/v2/{project_id}/cloudvolumes/detail?status=available

Response
--------

-  Parameter description

   +-----------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type             | Description                                                                                                                                      |
   +===========+==================+==================================================================================================================================================+
   | volumes   | Array of objects | Specifies the list of queried disks. For details, see :ref:`Parameters in the volumes field <evs_04_2005__li7558467201357>`.                     |
   +-----------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | error     | Object           | Specifies the error message returned when an error occurs. For details, see :ref:`Parameters in the error field <evs_04_2005__li0419202382514>`. |
   +-----------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_2005__li7558467201357:

   Parameters in the **volumes** field

   +------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                    | Type                  | Description                                                                                                                                            |
   +==============================+=======================+========================================================================================================================================================+
   | id                           | String                | Specifies the disk ID.                                                                                                                                 |
   +------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | links                        | Array of objects      | Specifies the disk URI. For details, see :ref:`Parameters in the links field <evs_04_2005__li1043159617124>`.                                          |
   +------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                         | String                | Specifies the disk name.                                                                                                                               |
   +------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status                       | String                | Specifies the disk status. For details, see :ref:`EVS Disk Status <evs_04_0040>`.                                                                      |
   +------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | attachments                  | Array of objects      | Specifies the disk attachment information. For details, see :ref:`Parameters in the attachments field <evs_04_2005__li3900093617124>`.                 |
   +------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | availability_zone            | String                | Specifies the AZ to which the disk belongs.                                                                                                            |
   +------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | source_volid                 | String                | Specifies the source disk ID. This parameter has a value if the disk is created from a source disk.                                                    |
   |                              |                       |                                                                                                                                                        |
   |                              |                       | Currently, this field is not supported by EVS.                                                                                                         |
   +------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | snapshot_id                  | String                | Specifies the snapshot ID. This parameter has a value if the disk is created from a snapshot.                                                          |
   +------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description                  | String                | Specifies the disk description.                                                                                                                        |
   +------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | os-vol-tenant-attr:tenant_id | String                | Specifies the ID of the tenant to which the disk belongs. The tenant ID is actually the project ID.                                                    |
   +------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | volume_image_metadata        | Object                | Specifies the metadata of the disk image.                                                                                                              |
   |                              |                       |                                                                                                                                                        |
   |                              |                       | .. note::                                                                                                                                              |
   |                              |                       |                                                                                                                                                        |
   |                              |                       |    For details about **volume_image_metadata**, see **Querying Image Details (Native OpenStack API)** in the *Image Management Service API Reference*. |
   +------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | created_at                   | String                | Specifies the time when the disk was created.                                                                                                          |
   |                              |                       |                                                                                                                                                        |
   |                              |                       | Time format: UTC YYYY-MM-DDTHH:MM:SS.XXXXXX                                                                                                            |
   +------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | volume_type                  | String                | Specifies the disk type.                                                                                                                               |
   |                              |                       |                                                                                                                                                        |
   |                              |                       | Currently, the value can be **SSD**, **SAS**, **SATA**, **co-p1**, or **uh-l1**.                                                                       |
   |                              |                       |                                                                                                                                                        |
   |                              |                       | -  **SSD**: specifies the ultra-high I/O disk type.                                                                                                    |
   |                              |                       |                                                                                                                                                        |
   |                              |                       | -  **SAS**: specifies the high I/O disk type.                                                                                                          |
   |                              |                       |                                                                                                                                                        |
   |                              |                       | -  **SATA**: specifies the common I/O disk type.                                                                                                       |
   |                              |                       |                                                                                                                                                        |
   |                              |                       | -  **co-p1**: specifies the high I/O (performance-optimized I) disk type.                                                                              |
   |                              |                       |                                                                                                                                                        |
   |                              |                       | -  **uh-l1**: specifies the ultra-high I/O (latency-optimized) disk type.                                                                              |
   |                              |                       |                                                                                                                                                        |
   |                              |                       |    Disks of the **co-p1** and **uh-l1** types are used exclusively for HPC ECSs and SAP HANA ECSs.                                                     |
   +------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | size                         | Integer               | Specifies the disk size, in GB.                                                                                                                        |
   +------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | bootable                     | String                | Specifies whether the disk is bootable.                                                                                                                |
   |                              |                       |                                                                                                                                                        |
   |                              |                       | -  **true**: specifies a bootable disk.                                                                                                                |
   |                              |                       | -  **false**: specifies a non-bootable disk.                                                                                                           |
   +------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | metadata                     | Object                | Specifies the disk metadata. For details, see :ref:`Parameters in the metadata field <evs_04_2005__li29114110314>`.                                    |
   |                              |                       |                                                                                                                                                        |
   |                              |                       | If **metadata** does not contain the **hw:passthrough** field, the disk device type is VBD.                                                            |
   |                              |                       |                                                                                                                                                        |
   |                              |                       | If **metadata** does not contain the **\__system__encrypted** field, the disk is not encrypted.                                                        |
   +------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | os-vol-host-attr:host        | String                | Reserved field                                                                                                                                         |
   +------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | shareable                    | String                | Specifies whether the disk is shareable.                                                                                                               |
   |                              |                       |                                                                                                                                                        |
   |                              |                       | .. note::                                                                                                                                              |
   |                              |                       |                                                                                                                                                        |
   |                              |                       |    This field is no longer used. Use **multiattach**.                                                                                                  |
   +------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | multiattach                  | Boolean               | Specifies whether the disk is shareable.                                                                                                               |
   |                              |                       |                                                                                                                                                        |
   |                              |                       | -  **true**: specifies a shared disk.                                                                                                                  |
   |                              |                       | -  **false**: specifies a non-shared disk.                                                                                                             |
   +------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_2005__li1043159617124:

   Parameters in the **links** field

   ========= ====== ==========================================
   Parameter Type   Description
   ========= ====== ==========================================
   href      String Specifies the corresponding shortcut link.
   rel       String Specifies the shortcut link marker name.
   ========= ====== ==========================================

-  .. _evs_04_2005__li3900093617124:

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

-  .. _evs_04_2005__li29114110314:

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

-  .. _evs_04_2005__li0419202382514:

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
          "volumes": [
              {
                  "id": "c6ccc84e-feff-4114-ad83-42a11c0434e2",
                  "links": [
                      {
                          "href": "https://volume.az0.dc1.domainname.com/v2/9e179fd535e44f19a9dabb36deadf47e/volumes/c6ccc84e-feff-4114-ad83-42a11c0434e2",
                          "rel": "self"
                      },
                      {
                          "href": "https://volume.az0.dc1.domainname.com/9e179fd535e44f19a9dabb36deadf47e/volumes/c6ccc84e-feff-4114-ad83-42a11c0434e2",
                          "rel": "bookmark"
                      }
                  ],
                  "name": "test_volume",
                  "status": "available",
                  "attachments": [ ],
                  "description": null,
                  "size": 100,
                  "metadata": null,
                  "bootable": "false",
                  "availability_zone": "az-dc-1",
                  "os-vol-host-attr:host": "az-dc-1#sata",
                  "source_volid": null,
                  "snapshot_id": null,
                  "created_at": "2015-09-17T06:37:16.275659",
                  "volume_type": "SATA",
                  "os-vol-tenant-attr:tenant_id": "9e179fd535e44f19a9dabb36deadf47e",
                  "volume_image_metadata": null
              },
              {
                  "id": "a05d9342-bf27-44a6-8ab8-33afc7545d19",
                  "links": [
                      {
                          "href": "https://volume.az0.dc1.domainname.com/v2/9e179fd535e44f19a9dabb36deadf47e/volumes/a05d9342-bf27-44a6-8ab8-33afc7545d19",
                          "rel": "self"
                      },
                      {
                          "href": "https://volume.az0.dc1.domainname.com/9e179fd535e44f19a9dabb36deadf47e/volumes/a05d9342-bf27-44a6-8ab8-33afc7545d19",
                          "rel": "bookmark"
                      }
                  ],
                  "name": "test_volume",
                  "status": "available",
                  "attachments": [ ],
                  "description": null,
                  "size": 100,
                  "metadata": null,
                  "bootable": "false",
                  "availability_zone": "az-dc-1",
                  "os-vol-host-attr:host": "az-dc-1#sata",
                  "source_volid": null,
                  "snapshot_id": null,
                  "created_at": "2015-09-17T06:37:16.192556",
                  "volume_type": "SATA",
                  "os-vol-tenant-attr:tenant_id": "9e179fd535e44f19a9dabb36deadf47e",
                  "volume_image_metadata": null
              }
          ]
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
