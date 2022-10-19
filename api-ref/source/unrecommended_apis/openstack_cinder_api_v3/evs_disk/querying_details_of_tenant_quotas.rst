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

   +-------------------+-----------+--------------------------------------------------------------------------------------------+
   | Parameter         | Mandatory | Description                                                                                |
   +===================+===========+============================================================================================+
   | project_id        | Yes       | Specifies the project ID.                                                                  |
   +-------------------+-----------+--------------------------------------------------------------------------------------------+
   | target_project_id | Yes       | Specifies the ID of the target project. Set this parameter to the value of **project_id**. |
   +-------------------+-----------+--------------------------------------------------------------------------------------------+
   | usage             | Yes       | Specifies whether to query the quota details. Only value **true** is supported currently.  |
   +-------------------+-----------+--------------------------------------------------------------------------------------------+

Request
-------

-  Example request

   .. code-block:: text

      GET https://{endpoint}/v3/{project_id}/os-quota-sets/{project_id}?usage=True

Response
--------

-  Parameter description

   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                                                                                  |
   +===========+========+==============================================================================================================================================================+
   | quota_set | Object | Specifies the queried quota information. For details, see :ref:`Parameters in the quota_set field <evs_04_3037__evs_04_2073_li4741865201620>`.               |
   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | error     | Object | Specifies the error message returned when an error occurs. For details, see :ref:`Parameters in the error field <evs_04_3037__evs_04_2073_li0419202382514>`. |
   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_3037__evs_04_2073_li4741865201620:

   Parameters in the **quota_set** field

   +----------------------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter            | Type   | Description                                                                                                                                                                                                            |
   +======================+========+========================================================================================================================================================================================================================+
   | volumes              | Object | Specifies the number of disks. Sub-parameters include **reserved** (reserved quota), **limit** (maximum quota), and **in_use** (used quota), and are made up of key-value pairs.                                       |
   +----------------------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | snapshots            | Object | Specifies the number of snapshots. Sub-parameters include **reserved** (reserved quota), **limit** (maximum quota), and **in_use** (used quota), and are made up of key-value pairs.                                   |
   +----------------------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | gigabytes            | Object | Specifies the total size (GB) of disks and snapshots allowed. Sub-parameters include **reserved** (reserved quota), **limit** (maximum quota), and **in_use** (used quota), and are made up of key-value pairs.        |
   +----------------------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | volumes_SSD          | Object | Specifies the number of reserved ultra-high I/O disks. Sub-parameters include **reserved** (reserved quota), **limit** (maximum quota), and **in_use** (used quota), and are made up of key-value pairs.               |
   +----------------------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | volumes_SAS          | Object | Specifies the number of reserved high I/O disks. Sub-parameters include **reserved** (reserved quota), **limit** (maximum quota), and **in_use** (used quota), and are made up of key-value pairs.                     |
   +----------------------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | volumes_SATA         | Object | Specifies the number of reserved common I/O disks. Sub-parameters include **reserved** (reserved quota), **limit** (maximum quota), and **in_use** (used quota), and are made up of key-value pairs.                   |
   +----------------------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | snapshots_SSD        | Object | Specifies the number of snapshots reserved for ultra-high I/O disks. Sub-parameters include **reserved** (reserved quota), **limit** (maximum quota), and **in_use** (used quota), and are made up of key-value pairs. |
   +----------------------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | snapshots_SAS        | Object | Specifies the number of snapshots reserved for high I/O disks. Sub-parameters include **reserved** (reserved quota), **limit** (maximum quota), and **in_use** (used quota), and are made up of key-value pairs.       |
   +----------------------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | snapshots_SATA       | Object | Specifies the number of snapshots reserved for common I/O disks. Sub-parameters include **reserved** (reserved quota), **limit** (maximum quota), and **in_use** (used quota), and are made up of key-value pairs.     |
   +----------------------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | gigabytes_SSD        | Object | Specifies the size (GB) reserved for ultra-high I/O disks. Sub-parameters include **reserved** (reserved quota), **limit** (maximum quota), and **in_use** (used quota), and are made up of key-value pairs.           |
   +----------------------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | gigabytes_SAS        | Object | Specifies the size (GB) reserved for high I/O disks. Sub-parameters include **reserved** (reserved quota), **limit** (maximum quota), and **in_use** (used quota), and are made up of key-value pairs.                 |
   +----------------------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | gigabytes_SATA       | Object | Specifies the size (GB) reserved for common I/O disks. Sub-parameters include **reserved** (reserved quota), **limit** (maximum quota), and **in_use** (used quota), and are made up of key-value pairs.               |
   +----------------------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | id                   | String | Specifies the tenant ID. The tenant ID is actually the project ID.                                                                                                                                                     |
   +----------------------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | backups              | Object | Specifies the number of backups. Sub-parameters include **reserved** (reserved quota), **limit** (maximum quota), and **in_use** (used quota), and are made up of key-value pairs.                                     |
   +----------------------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | backup_gigabytes     | Object | Specifies the backup size (GB). Sub-parameters include **reserved** (reserved quota), **limit** (maximum quota), and **in_use** (used quota), and are made up of key-value pairs.                                      |
   +----------------------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | per_volume_gigabytes | Object | Specifies the capacity quota of each EVS disk. Sub-parameters include **reserved** (reserved quota), **limit** (maximum quota), and **in_use** (used quota), and are made up of key-value pairs.                       |
   +----------------------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. note::

      If the **limit** value returned in the response is **-1**, no quota limit has been set.

-  .. _evs_04_3037__evs_04_2073_li0419202382514:

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
          "quota_set": {
              "gigabytes_SAS": {
                  "reserved": 0,
                  "limit": -1,
                  "in_use": 21
              },
              "volumes_SATA": {
                  "reserved": 0,
                  "limit": -1,
                  "in_use": 8
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
              "snapshots_SAS": {
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
              "volumes_SAS": {
                  "reserved": 0,
                  "limit": -1,
                  "in_use": 2
              },
              "snapshots_SSD": {
                  "reserved": 0,
                  "limit": -1,
                  "in_use": 0
              },
              "volumes": {
                  "reserved": 0,
                  "limit": -1,
                  "in_use": 108
              },
              "gigabytes_SATA": {
                  "reserved": 0,
                  "limit": -1,
                  "in_use": 168
              },
              "backups": {
                  "reserved": 0,
                  "limit": 100,
                  "in_use": 10
              },
              "gigabytes_SSD": {
                  "reserved": 0,
                  "limit": -1,
                  "in_use": 1085
              },
              "snapshots_SATA": {
                  "reserved": 0,
                  "limit": -1,
                  "in_use": 0
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
