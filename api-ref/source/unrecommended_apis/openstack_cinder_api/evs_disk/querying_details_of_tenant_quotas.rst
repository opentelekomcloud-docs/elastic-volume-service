:original_name: evs_04_3037.html

.. _evs_04_3037:

Querying Details of Tenant Quotas
=================================

Function
--------

This API is used to query the details of tenant quotas.

URI
---

-  URI format

   GET /v3/{project_id}/os-quota-sets/{target_project_id}?usage=True

-  Parameter description

   +-------------------+-----------+----------------------------------------------------------------------------------+
   | Parameter         | Mandatory | Description                                                                      |
   +===================+===========+==================================================================================+
   | project_id        | Yes       | The project ID.                                                                  |
   +-------------------+-----------+----------------------------------------------------------------------------------+
   | target_project_id | Yes       | The ID of the target project. Set this parameter to the value of **project_id**. |
   +-------------------+-----------+----------------------------------------------------------------------------------+
   | usage             | Yes       | Whether to query quota details. Only value **true** is supported currently.      |
   +-------------------+-----------+----------------------------------------------------------------------------------+

Request
-------

-  Example request

   .. code-block:: text

      GET https://{endpoint}/v3/{project_id}/os-quota-sets/{project_id}?usage=True

Response
--------

-  Response parameters

   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                                                                      |
   +===========+========+==================================================================================================================================================+
   | quota_set | Object | The returned quota information. For details, see :ref:`Parameters in the quota_set field <evs_04_3037__evs_04_2073_li4741865201620>`.            |
   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | error     | Object | The error message returned if an error occurs. For details, see :ref:`Parameters in the error field <evs_04_3037__evs_04_2073_li0419202382514>`. |
   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_3037__evs_04_2073_li4741865201620:

   Parameters in the **quota_set** field

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                                                                                                                        |
   +=======================+=======================+====================================================================================================================================================================================================================================================================================+
   | volumes               | Object                | The number of disks. Sub-parameters include **reserved** (reserved quota), **limit** (maximum quota), and **in_use** (used quota). They are all made up of key-value pairs. See :ref:`Parameters in the QuotaDetailVolumes field <evs_04_3037__evs_04_2073_li292012111347>`.       |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | snapshots             | Object                | The number of snapshots. Sub-parameters include **reserved** (reserved quota), **limit** (maximum quota), and **in_use** (used quota). They are all made up of key-value pairs. See :ref:`Parameters in the QuotaDetailSnapshots field <evs_04_3037__evs_04_2073_li963171713412>`. |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | gigabytes             | Object                | The total size (GB) of disks and snapshots allowed. Sub-parameters include **reserved** (reserved quota), **limit** (maximum quota), and **in_use** (used quota). They are all made up of key-value pairs.                                                                         |
   |                       |                       |                                                                                                                                                                                                                                                                                    |
   |                       |                       | See :ref:`Parameters in the QuotaDetailGigabytes field <evs_04_3037__evs_04_2073_li12781611113418>`.                                                                                                                                                                               |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | volumes_SSD           | Object                | The number of reserved ultra-high I/O disks. Sub-parameters include **reserved** (reserved quota), **limit** (maximum quota), and **in_use** (used quota). They are all made up of key-value pairs.                                                                                |
   |                       |                       |                                                                                                                                                                                                                                                                                    |
   |                       |                       | See :ref:`Parameters in the QuotaDetailVolumesSSD field <evs_04_3037__evs_04_2073_li2874195493416>`.                                                                                                                                                                               |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | volumes_SAS           | Object                | The number of reserved high I/O disks. Sub-parameters include **reserved** (reserved quota), **limit** (maximum quota), and **in_use** (used quota). They are all made up of key-value pairs.                                                                                      |
   |                       |                       |                                                                                                                                                                                                                                                                                    |
   |                       |                       | See :ref:`Parameters in the QuotaDetailVolumesSAS field <evs_04_3037__evs_04_2073_li07672462342>`.                                                                                                                                                                                 |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | volumes_SATA          | Object                | The number of reserved common I/O disks. Sub-parameters include **reserved** (reserved quota), **limit** (maximum quota), and **in_use** (used quota). They are all made up of key-value pairs.                                                                                    |
   |                       |                       |                                                                                                                                                                                                                                                                                    |
   |                       |                       | See :ref:`Parameters in the QuotaDetailVolumesSATA field <evs_04_3037__evs_04_2073_li3935163483411>`.                                                                                                                                                                              |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | volumes_ESSD          | Object                | The number of reserved extreme SSD disks. Sub-parameters include **reserved** (reserved quota), **limit** (maximum quota), and **in_use** (used quota). They are all made up of key-value pairs.                                                                                   |
   |                       |                       |                                                                                                                                                                                                                                                                                    |
   |                       |                       | See :ref:`Parameters in the QuotaDetailVolumesESSD field <evs_04_3037__evs_04_2073_li6211423143513>`.                                                                                                                                                                              |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | snapshots_SSD         | Object                | The number of snapshots reserved for ultra-high I/O disks. Sub-parameters include **reserved** (reserved quota), **limit** (maximum quota), and **in_use** (used quota). They are all made up of key-value pairs.                                                                  |
   |                       |                       |                                                                                                                                                                                                                                                                                    |
   |                       |                       | See :ref:`Parameters in the QuotaDetailSnapshotsSSD field <evs_04_3037__evs_04_2073_li33071651163411>`.                                                                                                                                                                            |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | snapshots_SAS         | Object                | The number of snapshots reserved for high I/O disks. Sub-parameters include **reserved** (reserved quota), **limit** (maximum quota), and **in_use** (used quota). They are all made up of key-value pairs.                                                                        |
   |                       |                       |                                                                                                                                                                                                                                                                                    |
   |                       |                       | See :ref:`Parameters in the QuotaDetailSnapshotsSAS field <evs_04_3037__evs_04_2073_li1766714373411>`.                                                                                                                                                                             |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | snapshots_SATA        | Object                | The number of snapshots reserved for common I/O disks. Sub-parameters include **reserved** (reserved quota), **limit** (maximum quota), and **in_use** (used quota). They are all made up of key-value pairs.                                                                      |
   |                       |                       |                                                                                                                                                                                                                                                                                    |
   |                       |                       | See :ref:`Parameters in the QuotaDetailSnapshotsSATA field <evs_04_3037__evs_04_2073_li4447143018345>`.                                                                                                                                                                            |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | snapshots_ESSD        | Object                | The number of snapshots reserved for extreme SSD disks. Sub-parameters include **reserved** (reserved quota), **limit** (maximum quota), and **in_use** (used quota). They are all made up of key-value pairs.                                                                     |
   |                       |                       |                                                                                                                                                                                                                                                                                    |
   |                       |                       | See :ref:`Parameters in the QuotaDetailSnapshotsESSD field <evs_04_3037__evs_04_2073_li144181011123512>`.                                                                                                                                                                          |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | gigabytes_SSD         | Object                | The size (GB) reserved for ultra-high I/O disks. Sub-parameters include **reserved** (reserved quota), **limit** (maximum quota), and **in_use** (used quota). They are all made up of key-value pairs.                                                                            |
   |                       |                       |                                                                                                                                                                                                                                                                                    |
   |                       |                       | See :ref:`Parameters in the QuotaDetailGigabytesSSD field <evs_04_3037__evs_04_2073_li1538024919344>`.                                                                                                                                                                             |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | gigabytes_SAS         | Object                | The size (GB) reserved for high I/O disks. Sub-parameters include **reserved** (reserved quota), **limit** (maximum quota), and **in_use** (used quota). They are all made up of key-value pairs.                                                                                  |
   |                       |                       |                                                                                                                                                                                                                                                                                    |
   |                       |                       | See :ref:`Parameters in the QuotaDetailGigabytesSAS field <evs_04_3037__evs_04_2073_li1513517383342>`.                                                                                                                                                                             |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | gigabytes_SATA        | Object                | The size (GB) reserved for common I/O disks. Sub-parameters include **reserved** (reserved quota), **limit** (maximum quota), and **in_use** (used quota). They are all made up of key-value pairs.                                                                                |
   |                       |                       |                                                                                                                                                                                                                                                                                    |
   |                       |                       | See :ref:`Parameters in the QuotaDetailGigabytesSATA field <evs_04_3037__evs_04_2073_li1794762693411>`.                                                                                                                                                                            |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | gigabytes_ESSD        | Object                | The size (GB) reserved for extreme SSD disks. Sub-parameters include **reserved** (reserved quota), **limit** (maximum quota), and **in_use** (used quota). They are all made up of key-value pairs.                                                                               |
   |                       |                       |                                                                                                                                                                                                                                                                                    |
   |                       |                       | See :ref:`Parameters in the QuotaDetailGigabytesESSD field <evs_04_3037__evs_04_2073_li9208164663417>`.                                                                                                                                                                            |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | id                    | String                | The tenant ID. The tenant ID is the same as the project ID.                                                                                                                                                                                                                        |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | backups               | Object                | The number of backups. Sub-parameters include **reserved** (reserved quota), **limit** (maximum quota), and **in_use** (used quota). They are all made up of key-value pairs. See :ref:`Parameters in the QuotaDetailBackups field <evs_04_3037__evs_04_2073_li39301654113311>`.   |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | backup_gigabytes      | Object                | The backup size (GB). Sub-parameters include **reserved** (reserved quota), **limit** (maximum quota), and **in_use** (used quota). They are all made up of key-value pairs.                                                                                                       |
   |                       |                       |                                                                                                                                                                                                                                                                                    |
   |                       |                       | See :ref:`Parameters in the QuotaDetailBackupGigabytes field <evs_04_3037__evs_04_2073_li18465426336>`.                                                                                                                                                                            |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | per_volume_gigabytes  | Object                | The capacity quota of each disk. Sub-parameters include **reserved** (reserved quota), **limit** (maximum quota), and **in_use** (used quota). They are all made up of key-value pairs.                                                                                            |
   |                       |                       |                                                                                                                                                                                                                                                                                    |
   |                       |                       | See :ref:`Parameters in the QuotaDetailPerVolumeGigabytes field <evs_04_3037__evs_04_2073_li687518353519>`.                                                                                                                                                                        |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. note::

      If the **limit** value returned in the response is **-1**, no quota limit has been set.

-  .. _evs_04_3037__evs_04_2073_li18465426336:

   Parameters in the **QuotaDetailBackupGigabytes** field

   ========= ======= ===================
   Parameter Type    Description
   ========= ======= ===================
   in_use    Integer The used quota.
   limit     Integer The maximum quota.
   reserved  Integer The reserved field.
   ========= ======= ===================

-  .. _evs_04_3037__evs_04_2073_li39301654113311:

   Parameters in the **QuotaDetailBackups** field

   ========= ======= ===================
   Parameter Type    Description
   ========= ======= ===================
   in_use    Integer The used quota.
   limit     Integer The maximum quota.
   reserved  Integer The reserved field.
   ========= ======= ===================

-  .. _evs_04_3037__evs_04_2073_li12781611113418:

   Parameters in the **QuotaDetailGigabytes** field

   ========= ======= ===================
   Parameter Type    Description
   ========= ======= ===================
   in_use    Integer The used quota.
   limit     Integer The maximum quota.
   reserved  Integer The reserved field.
   ========= ======= ===================

-  .. _evs_04_3037__evs_04_2073_li963171713412:

   Parameters in the **QuotaDetailSnapshots** field

   ========= ======= ===================
   Parameter Type    Description
   ========= ======= ===================
   in_use    Integer The used quota.
   limit     Integer The maximum quota.
   reserved  Integer The reserved field.
   ========= ======= ===================

-  .. _evs_04_3037__evs_04_2073_li292012111347:

   Parameters in the **QuotaDetailVolumes** field

   ========= ======= ===================
   Parameter Type    Description
   ========= ======= ===================
   in_use    Integer The used quota.
   limit     Integer The maximum quota.
   reserved  Integer The reserved field.
   ========= ======= ===================

-  .. _evs_04_3037__evs_04_2073_li1794762693411:

   Parameters in the **QuotaDetailGigabytesSATA** field

   ========= ======= ===================
   Parameter Type    Description
   ========= ======= ===================
   in_use    Integer The used quota.
   limit     Integer The maximum quota.
   reserved  Integer The reserved field.
   ========= ======= ===================

-  .. _evs_04_3037__evs_04_2073_li9208164663417:

   Parameters in the **QuotaDetailGigabytesESSD** field

   ========= ======= ===================
   Parameter Type    Description
   ========= ======= ===================
   in_use    Integer The used quota.
   limit     Integer The maximum quota.
   reserved  Integer The reserved field.
   ========= ======= ===================

-  .. _evs_04_3037__evs_04_2073_li4447143018345:

   Parameters in the **QuotaDetailSnapshotsSATA** field

   ========= ======= ===================
   Parameter Type    Description
   ========= ======= ===================
   in_use    Integer The used quota.
   limit     Integer The maximum quota.
   reserved  Integer The reserved field.
   ========= ======= ===================

-  .. _evs_04_3037__evs_04_2073_li144181011123512:

   Parameters in the **QuotaDetailSnapshotsESSD** field

-  .. _evs_04_3037__evs_04_2073_li3935163483411:

   Parameters in the **QuotaDetailVolumesSATA** field

   ========= ======= ===================
   Parameter Type    Description
   ========= ======= ===================
   in_use    Integer The used quota.
   limit     Integer The maximum quota.
   reserved  Integer The reserved field.
   ========= ======= ===================

-  .. _evs_04_3037__evs_04_2073_li6211423143513:

   Parameters in the **QuotaDetailVolumesESSD** field

-  .. _evs_04_3037__evs_04_2073_li1513517383342:

   Parameters in the **QuotaDetailGigabytesSAS** field

   ========= ======= ===================
   Parameter Type    Description
   ========= ======= ===================
   in_use    Integer The used quota.
   limit     Integer The maximum quota.
   reserved  Integer The reserved field.
   ========= ======= ===================

-  .. _evs_04_3037__evs_04_2073_li1766714373411:

   Parameters in the **QuotaDetailSnapshotsSAS** field

   ========= ======= ===================
   Parameter Type    Description
   ========= ======= ===================
   in_use    Integer The used quota.
   limit     Integer The maximum quota.
   reserved  Integer The reserved field.
   ========= ======= ===================

-  .. _evs_04_3037__evs_04_2073_li07672462342:

   Parameters in the **QuotaDetailVolumesSAS** field

   ========= ======= ===================
   Parameter Type    Description
   ========= ======= ===================
   in_use    Integer The used quota.
   limit     Integer The maximum quota.
   reserved  Integer The reserved field.
   ========= ======= ===================

-  .. _evs_04_3037__evs_04_2073_li1538024919344:

   Parameters in the **QuotaDetailGigabytesSSD** field

   ========= ======= ===================
   Parameter Type    Description
   ========= ======= ===================
   in_use    Integer The used quota.
   limit     Integer The maximum quota.
   reserved  Integer The reserved field.
   ========= ======= ===================

-  .. _evs_04_3037__evs_04_2073_li33071651163411:

   Parameters in the **QuotaDetailSnapshotsSSD** field

   ========= ======= ===================
   Parameter Type    Description
   ========= ======= ===================
   in_use    Integer The used quota.
   limit     Integer The maximum quota.
   reserved  Integer The reserved field.
   ========= ======= ===================

-  .. _evs_04_3037__evs_04_2073_li2874195493416:

   Parameters in the **QuotaDetailVolumesSSD** field

   ========= ======= ===================
   Parameter Type    Description
   ========= ======= ===================
   in_use    Integer The used quota.
   limit     Integer The maximum quota.
   reserved  Integer The reserved field.
   ========= ======= ===================

-  .. _evs_04_3037__evs_04_2073_li687518353519:

   Parameters in the **QuotaDetailPerVolumeGigabytes** field

   ========= ======= ===================
   Parameter Type    Description
   ========= ======= ===================
   in_use    Integer The used quota.
   limit     Integer The maximum quota.
   reserved  Integer The reserved field.
   ========= ======= ===================

-  .. _evs_04_3037__evs_04_2073_li0419202382514:

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
          "quota_set": {
              "gigabytes_SSD": {
                  "reserved": 0,
                  "limit": -1,
                  "in_use": 21
              },
              "gigabytes": {
                  "reserved": 0,
                  "limit": 42790,
                  "in_use": 2792
              },
              "backup_gigabytes": {
                  "reserved": 0,
                  "limit": 5120,
                  "in_use": 51
              },
              "snapshots_SSD": {
                  "reserved": 0,
                  "limit": -1,
                  "in_use": 0
              },
              "volumes_SSD": {
                  "reserved": 0,
                  "limit": -1,
                  "in_use": 28
              },
              "snapshots": {
                  "reserved": 0,
                  "limit": 10,
                  "in_use": 6
              },
              "id": "cd631140887d4b6e9c786b67a6dd4c02",
              "volumes_ESSD": {
                  "reserved": 0,
                  "limit": -1,
                  "in_use": 2
              },
              "snapshots_ESSD": {
                  "reserved": 0,
                  "limit": -1,
                  "in_use": 0
              },
              "volumes": {
                  "reserved": 0,
                  "limit": -1,
                  "in_use": 108
              },
              "backups": {
                  "reserved": 0,
                  "limit": 100,
                  "in_use": 10
              },
              "gigabytes_ESSD": {
                  "reserved": 0,
                  "limit": -1,
                  "in_use": 1085
              }

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
