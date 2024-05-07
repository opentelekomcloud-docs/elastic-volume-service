:original_name: evs_04_2044.html

.. _evs_04_2044:

Creating an EVS Replication Pair (Deprecated)
=============================================

Function
--------

This API is used to create an EVS replication pair using a specified production disk and a disaster recovery (DR) disk. The production disk is in the primary AZ, and the DR disk is in the secondary AZ.

.. note::

   This API has been deprecated. To use this function, see `Storage Disaster Recovery Service API Reference <https://docs.otc.t-systems.com/en-us/api/sdrs/sdrs_01_0000.html>`__.

Constraints
-----------

-  Two EVS disks used to create the EVS replication pair have been created and belong to different AZs.
-  The types and capacities of the two EVS disks must be consistent.
-  If the DR disk has been attached to a server, the server must be stopped.

URI
---

-  URI format

   POST /v2/{project_id}/os-vendor-replications

-  Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   ========== ========= =========================

Request
-------

-  Parameter description

   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type   | Description                                                                                                                                                   |
   +=============+===========+========+===============================================================================================================================================================+
   | replication | Yes       | Object | Specifies the replication pair creation marker. For details, see :ref:`Parameters in the replication field <evs_04_2044__en-us_topic_0079693002_li50842877>`. |
   +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_2044__en-us_topic_0079693002_li50842877:

   Parameters in the **replication** field

   +-------------------+-----------+--------+------------------------------------------------------------------------------------------------------------+
   | Parameter         | Mandatory | Type   | Description                                                                                                |
   +===================+===========+========+============================================================================================================+
   | name              | No        | String | Specifies the name of the EVS replication pair. The name can contain a maximum of 255 bytes.               |
   +-------------------+-----------+--------+------------------------------------------------------------------------------------------------------------+
   | description       | No        | String | Specifies the description of the EVS replication pair. The description can contain a maximum of 255 bytes. |
   +-------------------+-----------+--------+------------------------------------------------------------------------------------------------------------+
   | volume_ids        | Yes       | list   | Specifies the IDs of the EVS disks used to create the EVS replication pair.                                |
   +-------------------+-----------+--------+------------------------------------------------------------------------------------------------------------+
   | priority_station  | Yes       | String | Specifies the primary AZ of the EVS replication pair, that is, the AZ where the production disk belongs.   |
   +-------------------+-----------+--------+------------------------------------------------------------------------------------------------------------+
   | replication_model | Yes       | String | Specifies the type of the EVS replication pair. Currently, only type **hypermetro** is supported.          |
   +-------------------+-----------+--------+------------------------------------------------------------------------------------------------------------+

-  Example request

   .. code-block::

      {
          "replication": {
              "name": "my replication",
              "description": "my replication",
              "volume_ids": [
                  "18aa67ea-c7cb-4826-800d-50e67f0de75b",
                  "375d23be-3658-498f-8b50-d3b950a890ec"
              ],
              "priority_station": "az2.dc2",
              "replication_model": "hypermetro"
          }
      }

Response
--------

-  Parameter description

   +----------------------------------+----------+-----------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                        | Type     | Description                                                                                                                       |
   +==================================+==========+===================================================================================================================================+
   | replication                      | Object   | Specifies the EVS replication pair information.                                                                                   |
   +----------------------------------+----------+-----------------------------------------------------------------------------------------------------------------------------------+
   | id                               | String   | Specifies the ID of the EVS replication pair.                                                                                     |
   +----------------------------------+----------+-----------------------------------------------------------------------------------------------------------------------------------+
   | name                             | String   | Specifies the name of the EVS replication pair.                                                                                   |
   +----------------------------------+----------+-----------------------------------------------------------------------------------------------------------------------------------+
   | description                      | String   | Specifies the description of the EVS replication pair.                                                                            |
   +----------------------------------+----------+-----------------------------------------------------------------------------------------------------------------------------------+
   | status                           | String   | Specifies the status of the EVS replication pair. For details, see :ref:`EVS Replication Pair Status (Deprecated) <evs_04_0042>`. |
   +----------------------------------+----------+-----------------------------------------------------------------------------------------------------------------------------------+
   | replication_consistency_group_id | String   | Specifies the ID of the replication consistency group where the EVS replication pair belongs.                                     |
   +----------------------------------+----------+-----------------------------------------------------------------------------------------------------------------------------------+
   | volume_ids                       | String   | Specifies the IDs of the EVS disks used to create the EVS replication pair.                                                       |
   +----------------------------------+----------+-----------------------------------------------------------------------------------------------------------------------------------+
   | priority_station                 | String   | Specifies the primary site of the EVS replication pair.                                                                           |
   +----------------------------------+----------+-----------------------------------------------------------------------------------------------------------------------------------+
   | created_at                       | datetime | Specifies the creation time.                                                                                                      |
   +----------------------------------+----------+-----------------------------------------------------------------------------------------------------------------------------------+
   | updated_at                       | datetime | Specifies the update time.                                                                                                        |
   +----------------------------------+----------+-----------------------------------------------------------------------------------------------------------------------------------+

-  Example response

   .. code-block::

      {
          "replication": {
              "id": "91085433-9499-4a68-b2c6-35072467ccd2",
              "name": "my replication",
              "description": "my replication",
              "status": "creating",
              "replication_consistency_group_id": null,
              "volume_ids": "18aa67ea-c7cb-4826-800d-50e67f0de75b, 375d23be-3658-498f-8b50-d3b950a890ec",
              "priority_station": "az2.dc2",
              "created_at": "2017-09-28T05:08:32.839953",
              "updated_at": null
          }
      }

Status Codes
------------

-  Normal

   ============== ====================================
   Returned Value Description
   ============== ====================================
   202            The server has accepted the request.
   ============== ====================================

-  Abnormal

   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | Returned Value                    | Description                                                                                |
   +===================================+============================================================================================+
   | 400 Bad Request                   | The server failed to process the request.                                                  |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 401 Unauthorized                  | You must enter the username and password to access the requested page.                     |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 403 Forbidden                     | You are forbidden to access the requested page.                                            |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 404 Not Found                     | The requested page was not found.                                                          |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 405 Method Not Allowed            | You are not allowed to use the method specified in the request.                            |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 406 Not Acceptable                | The response generated by the server cannot be accepted by the client.                     |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 407 Proxy Authentication Required | You must use the proxy server for authentication. Then, the request can be processed.      |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 408 Request Timeout               | The request timed out.                                                                     |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 409 Conflict                      | The request cannot be processed due to a conflict.                                         |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 500 Internal Server Error         | Failed to complete the request because of an internal service error.                       |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 501 Not Implemented               | Failed to complete the request because the server does not support the requested function. |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 502 Bad Gateway                   | Failed to complete the request because the server has received an invalid response.        |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 503 Service Unavailable           | Failed to complete the request because the service is unavailable.                         |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
   | 504 Gateway Timeout               | A gateway timeout error occurs.                                                            |
   +-----------------------------------+--------------------------------------------------------------------------------------------+
