:original_name: evs_04_3005.html

.. _evs_04_3005:

Querying Details About an EVS Disk (Deprecated)
===============================================

Function
--------

This API is used to query details about a disk.

URI
---

-  URI format

   GET /v3/{project_id}/os-vendor-volumes/{volume_id}

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

      GET https://{endpoint}/v3/{project_id}/os-vendor-volumes/b104b8db-170d-441b-897a-3c8ba9c5a214

Response
--------

-  Parameter description

   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                                                                      |
   +===========+========+==================================================================================================================================================+
   | volume    | Object | Specifies the queried disk. For details, see :ref:`Parameters in the volume field <evs_04_3005__li85501353123417>`.                              |
   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | error     | Object | Specifies the error message returned when an error occurs. For details, see :ref:`Parameters in the error field <evs_04_3005__li0419202382514>`. |
   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_3005__li85501353123417:

   Parameters in the **volume** field

   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                             | Type                  | Description                                                                                                                                            |
   +=======================================+=======================+========================================================================================================================================================+
   | id                                    | String                | Specifies the disk ID.                                                                                                                                 |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | links                                 | Array of objects      | Specifies the disk URI. For details, see :ref:`Parameters in the links field <evs_04_3005__li16591153203415>`.                                         |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                                  | String                | Specifies the disk name.                                                                                                                               |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status                                | String                | Specifies the disk status. For details, see :ref:`EVS Disk Status <evs_04_0040>`.                                                                      |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | attachments                           | Array of objects      | Specifies the disk attachment information. For details, see :ref:`Parameters in the attachments field <evs_04_3005__li159875317347>`.                  |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | availability_zone                     | String                | Specifies the AZ to which the disk belongs.                                                                                                            |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | source_volid                          | String                | Specifies the source disk ID. This parameter has a value if the disk is created from a source disk.                                                    |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | snapshot_id                           | String                | Specifies the snapshot ID. This parameter has a value if the disk is created from a snapshot.                                                          |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description                           | String                | Specifies the disk description.                                                                                                                        |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | os-vol-tenant-attr:tenant_id          | String                | Specifies the ID of the tenant to which the disk belongs. The tenant ID is actually the project ID.                                                    |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | volume_image_metadata                 | Object                | Specifies the metadata of the disk image.                                                                                                              |
   |                                       |                       |                                                                                                                                                        |
   |                                       |                       | .. note::                                                                                                                                              |
   |                                       |                       |                                                                                                                                                        |
   |                                       |                       |    For details about **volume_image_metadata**, see **Querying Image Details (Native OpenStack API)** in the *Image Management Service API Reference*. |
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
   | size                                  | Integer               | Specifies the disk size, in GB.                                                                                                                        |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | bootable                              | String                | Specifies whether the disk is bootable.                                                                                                                |
   |                                       |                       |                                                                                                                                                        |
   |                                       |                       | -  **true**: specifies a bootable disk.                                                                                                                |
   |                                       |                       | -  **false**: specifies a non-bootable disk.                                                                                                           |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | metadata                              | Object                | Specifies the disk metadata. For details, see :ref:`Parameters in the metadata field <evs_04_3005__li29114110314>`.                                    |
   |                                       |                       |                                                                                                                                                        |
   |                                       |                       | If **metadata** does not contain the **hw:passthrough** field, the disk device type is VBD.                                                            |
   |                                       |                       |                                                                                                                                                        |
   |                                       |                       | If **metadata** does not contain the **\__system__encrypted** field, the disk is not encrypted.                                                        |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | os-vol-host-attr:host                 | String                | Reserved field                                                                                                                                         |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | encrypted                             | Boolean               | Currently, this field is not supported by EVS.                                                                                                         |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | updated_at                            | String                | Specifies the time when the disk was updated.                                                                                                          |
   |                                       |                       |                                                                                                                                                        |
   |                                       |                       | Time format: UTC YYYY-MM-DDTHH:MM:SS.XXXXXX                                                                                                            |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | os-volume-replication:extended_status | String                | Reserved field                                                                                                                                         |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | replication_status                    | String                | Reserved field                                                                                                                                         |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | os-vol-mig-status-attr:migstat        | String                | Reserved field                                                                                                                                         |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | consistencygroup_id                   | String                | Reserved field                                                                                                                                         |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | os-vol-mig-status-attr:name_id        | String                | Reserved field                                                                                                                                         |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | shareable                             | String                | Specifies whether the disk is shareable.                                                                                                               |
   |                                       |                       |                                                                                                                                                        |
   |                                       |                       | .. note::                                                                                                                                              |
   |                                       |                       |                                                                                                                                                        |
   |                                       |                       |    This field is no longer used. Use **multiattach**.                                                                                                  |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | user_id                               | String                | Reserved field                                                                                                                                         |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | multiattach                           | Boolean               | Specifies whether the disk is shareable.                                                                                                               |
   |                                       |                       |                                                                                                                                                        |
   |                                       |                       | -  **true**: specifies a shared disk.                                                                                                                  |
   |                                       |                       | -  **false**: specifies a non-shared disk.                                                                                                             |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | service_type                          | String                | Specifies the service type. The value can be **EVS**.                                                                                                  |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tags                                  | Object                | Specifies the disk tags.                                                                                                                               |
   |                                       |                       |                                                                                                                                                        |
   |                                       |                       | This field is returned if the disk has tags. Otherwise, it is left empty.                                                                              |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | wwn                                   | String                | Specifies the unique identifier used when attaching the disk.                                                                                          |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | storage_cluster_id                    | String                | Reserved field                                                                                                                                         |
   +---------------------------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_3005__li16591153203415:

   Parameters in the **links** field

   ========= ====== ==========================================
   Parameter Type   Description
   ========= ====== ==========================================
   href      String Specifies the corresponding shortcut link.
   rel       String Specifies the shortcut link marker name.
   ========= ====== ==========================================

-  .. _evs_04_3005__li159875317347:

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

-  .. _evs_04_3005__li29114110314:

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

-  .. _evs_04_3005__li0419202382514:

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
              "links": [
                  {
                      "href": "https://volume.az0.dc1.domainname.com/v3/40acc331ac784f34842ba4f08ff2be48/volumes/591ac654-26d8-41be-bb77-4f90699d2d41",
                      "rel": "self"
                  },
                  {
                      "href": "https://volume.az0.dc1.domainname.com/40acc331ac784f34842ba4f08ff2be48/volumes/591ac654-26d8-41be-bb77-4f90699d2d41",
                      "rel": "bookmark"
                  }
              ],
              "availability_zone": "az-dc-1",
              "os-vol-host-attr:host": "az-dc-1#SSD",
              "encrypted": false,
              "multiattach": true,
              "updated_at": "2016-02-03T02:19:29.895237",
              "os-volume-replication:extended_status": null,
              "replication_status": "disabled",
              "snapshot_id": null,
              "id": "591ac654-26d8-41be-bb77-4f90699d2d41",
              "size": 40,
              "user_id": "fd03ee73295e45478d88e15263d2ee4e",
              "os-vol-tenant-attr:tenant_id": "40acc331ac784f34842ba4f08ff2be48",
              "volume_image_metadata": null,
              "os-vol-mig-status-attr:migstat": null,
              "metadata": {},
              "tags": {
                  "key1": "value1",
                  "key2": "value2"
              },
              "status": "error_restoring",
              "description": "auto-created_from_restore_from_backup",
              "source_volid": null,
              "consistencygroup_id": null,
              "os-vol-mig-status-attr:name_id": null,
              "name": "restore_backup_0115efb3-678c-4a9e-bff6-d3cd278238b9",
              "bootable": "false",
              "created_at": "2016-02-03T02:19:11.723797",
              "volume_type": null,
              "service_type": "EVS",
              "wwn": " 688860300000d136fa16f48f05992360"
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
          "badrequest": {
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
