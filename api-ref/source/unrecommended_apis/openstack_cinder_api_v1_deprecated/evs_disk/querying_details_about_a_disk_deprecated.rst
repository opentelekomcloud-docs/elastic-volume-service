:original_name: evs_04_0052.html

.. _evs_04_0052:

Querying Details About a Disk (Deprecated)
==========================================

Function
--------

This API is used to query details about a disk.

.. important::

   This API has been deprecated. Use another API. For details, see :ref:`Querying Details About a Disk <evs_04_3034>`.

URI
---

-  URI format

   GET /v1/{project_id}/volumes/{volume_id}

-  Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   volume_id  Yes       Specifies the disk ID.
   ========== ========= =========================

Request
-------

-  Example request

   .. code-block:: text

      GET https://{endpoint}/v1/{project_id}/volumes/b104b8db-170d-441b-897a-3c8ba9c5a214

Response
--------

-  Parameter description

   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                                                                      |
   +===========+========+==================================================================================================================================================+
   | volume    | Object | Specifies the disk information. For details, see :ref:`Parameters in the volume field <evs_04_0052__li3451542201439>`.                           |
   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | error     | Object | Specifies the error message returned when an error occurs. For details, see :ref:`Parameters in the error field <evs_04_0052__li0419202382514>`. |
   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_0052__li3451542201439:

   Parameters in the **volume** field

   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                             | Type                  | Description                                                                                                                                            |
   +=======================================+=======================+========================================================================================================================================================+
   | id                                    | String                | Specifies the disk ID.                                                                                                                                 |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | display_name                          | String                | Specifies the disk name.                                                                                                                               |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status                                | String                | Specifies the disk status. For details, see :ref:`EVS Disk Status <evs_04_0040>`.                                                                      |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | attachments                           | list                  | Specifies the attachment information.                                                                                                                  |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | availability_zone                     | String                | Specifies the AZ to which the disk belongs.                                                                                                            |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | os-vol-host-attr:host                 | String                | Reserved field                                                                                                                                         |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | source_volid                          | String                | Specifies the source disk ID. This parameter has a value if the disk is created from a source disk.                                                    |
   |                                       |                       |                                                                                                                                                        |
   |                                       |                       | Currently, this field is not supported by EVS.                                                                                                         |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | snapshot_id                           | String                | Specifies the snapshot ID. This parameter has a value if the disk is created from a snapshot.                                                          |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | display_description                   | String                | Specifies the disk description.                                                                                                                        |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | created_at                            | String                | Specifies the time when the disk was created.                                                                                                          |
   |                                       |                       |                                                                                                                                                        |
   |                                       |                       | Time format: UTC YYYY-MM-DDTHH:MM:SS.XXXXXX                                                                                                            |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | volume_type                           | String                | Specifies the disk type.                                                                                                                               |
   |                                       |                       |                                                                                                                                                        |
   |                                       |                       | Currently, the value can be **SSD**, **SAS**, **SATA**, **co-p1**, or **uh-l1**.                                                                       |
   |                                       |                       |                                                                                                                                                        |
   |                                       |                       | -  **SSD**: specifies the ultra-high I/O disk type.                                                                                                    |
   |                                       |                       |                                                                                                                                                        |
   |                                       |                       | -  **SAS**: specifies the high I/O disk type.                                                                                                          |
   |                                       |                       |                                                                                                                                                        |
   |                                       |                       | -  **SATA**: specifies the common I/O disk type.                                                                                                       |
   |                                       |                       |                                                                                                                                                        |
   |                                       |                       | -  **co-p1**: specifies the high I/O (performance-optimized I) disk type.                                                                              |
   |                                       |                       |                                                                                                                                                        |
   |                                       |                       | -  **uh-l1**: specifies the ultra-high I/O (latency-optimized) disk type.                                                                              |
   |                                       |                       |                                                                                                                                                        |
   |                                       |                       |    Disks of the **co-p1** and **uh-l1** types are used exclusively for HPC ECSs and SAP HANA ECSs.                                                     |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | os-vol-tenant-attr:tenant_id          | String                | Specifies the ID of the tenant to which the disk belongs. The tenant ID is actually the project ID.                                                    |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | size                                  | Integer               | Specifies the disk size, in GB.                                                                                                                        |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | metadata                              | Object                | Specifies the disk metadata.                                                                                                                           |
   |                                       |                       |                                                                                                                                                        |
   |                                       |                       | If **metadata** does not contain the **hw:passthrough** field, the disk device type is VBD.                                                            |
   |                                       |                       |                                                                                                                                                        |
   |                                       |                       | If **metadata** does not contain the **\__system__encrypted** field, the disk is not encrypted.                                                        |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | os-vol-mig-status-attr:migstat        | String                | Reserved field                                                                                                                                         |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | os-vol-mig-status-attr:name_id        | String                | Reserved field                                                                                                                                         |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | os-volume-replication:extended_status | String                | Reserved field                                                                                                                                         |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | encrypted                             | Boolean               | Currently, this field is not supported by EVS.                                                                                                         |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | bootable                              | String                | Specifies whether the disk is bootable.                                                                                                                |
   |                                       |                       |                                                                                                                                                        |
   |                                       |                       | -  **true**: specifies a bootable disk.                                                                                                                |
   |                                       |                       | -  **false**: specifies a non-bootable disk.                                                                                                           |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | shareable                             | String                | Specifies whether the disk is shareable.                                                                                                               |
   |                                       |                       |                                                                                                                                                        |
   |                                       |                       | .. note::                                                                                                                                              |
   |                                       |                       |                                                                                                                                                        |
   |                                       |                       |    This field is no longer used. Use **multiattach**.                                                                                                  |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | multiattach                           | Boolean               | Specifies whether the disk is shareable.                                                                                                               |
   |                                       |                       |                                                                                                                                                        |
   |                                       |                       | -  **true**: specifies a shared disk.                                                                                                                  |
   |                                       |                       | -  **false**: specifies a non-shared disk.                                                                                                             |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | volume_image_metadata                 | Object                | Specifies the metadata of the disk image. This field has a value if the disk is created from an image. Otherwise, it is left empty.                    |
   |                                       |                       |                                                                                                                                                        |
   |                                       |                       | .. note::                                                                                                                                              |
   |                                       |                       |                                                                                                                                                        |
   |                                       |                       |    For details about **volume_image_metadata**, see **Querying Image Details (Native OpenStack API)** in the *Image Management Service API Reference*. |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Parameters in the **attachments** field

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

-  Parameters in the **metadata** field

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

-  .. _evs_04_0052__li0419202382514:

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
              "attachments": [],
              "availability_zone": "az-dc-1",
              "os-vol-host-attr:host": "db-rabbitmq201#LVM_iSCSI",
              "encrypted": false,
              "os-volume-replication:extended_status": null,
              "volume_image_metadata": null,
              "snapshot_id": null,
              "id": "da4f9c7a-c275-4bc9-80c4-76c7d479a218",
              "size": 1,
              "os-vol-tenant-attr:tenant_id": "3dab0aaf682849678a94ec7b5a3af2ce",
              "os-vol-mig-status-attr:migstat": null,
              "metadata": {},
              "status": "available",
              "display_description": null,
              "source_volid": null,
              "os-vol-mig-status-attr:name_id": null,
              "display_name": "test",
              "bootable": "false",
              "created_at": "2014-12-18T17:14:38.000000",
              "volume_type": "SATA",
              "multiattach": false
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

   In the preceding example, **error** indicates a general error, for example, **badrequest** or **itemNotFound**. An example is provided as follows:

   .. code-block::

      {
          "itemNotFound": {
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
