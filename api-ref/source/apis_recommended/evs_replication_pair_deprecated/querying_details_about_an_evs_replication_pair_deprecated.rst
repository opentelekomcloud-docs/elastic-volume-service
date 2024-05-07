:original_name: evs_04_2047.html

.. _evs_04_2047:

Querying Details About an EVS Replication Pair (Deprecated)
===========================================================

Function
--------

This API is used to query the details about an EVS replication pair, including the name, ID, and status of the replication pair.

.. note::

   This API has been deprecated. To use this function, see `Storage Disaster Recovery Service API Reference <https://docs.otc.t-systems.com/en-us/api/sdrs/sdrs_01_0000.html>`__.

Constraints
-----------

None

URI
---

-  URI format

   GET /v2/{project_id}/os-vendor-replications/{replication_id}

-  Parameter description

   ============== ========= =============================================
   Parameter      Mandatory Description
   ============== ========= =============================================
   project_id     Yes       Specifies the project ID.
   replication_id Yes       Specifies the ID of the EVS replication pair.
   ============== ========= =============================================

Request
-------

None

Response
--------

-  Parameter description

   +----------------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                        | Type                  | Description                                                                                                                                                                             |
   +==================================+=======================+=========================================================================================================================================================================================+
   | replication                      | Object                | Specifies the details of the EVS replication pair.                                                                                                                                      |
   +----------------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | id                               | String                | Specifies the ID of the EVS replication pair.                                                                                                                                           |
   +----------------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                             | String                | Specifies the name of the EVS replication pair.                                                                                                                                         |
   +----------------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description                      | String                | Specifies the description of the EVS replication pair.                                                                                                                                  |
   +----------------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status                           | String                | Specifies the status of the EVS replication pair. For details, see :ref:`EVS Replication Pair Status (Deprecated) <evs_04_0042>`.                                                       |
   +----------------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | replication_consistency_group_id | String                | Specifies the ID of the replication consistency group where the EVS replication pair belongs.                                                                                           |
   +----------------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | volume_ids                       | String                | Specifies the IDs of the EVS disks used to create the EVS replication pair.                                                                                                             |
   +----------------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | priority_station                 | String                | Specifies the primary site of the EVS replication pair.                                                                                                                                 |
   +----------------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | created_at                       | datetime              | Specifies the creation time.                                                                                                                                                            |
   +----------------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | updated_at                       | datetime              | Specifies the update time.                                                                                                                                                              |
   +----------------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | replication_model                | String                | Specifies the replication type of the EVS replication pair.                                                                                                                             |
   +----------------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | replication_status               | String                | Specifies the replication status of the EVS replication pair. For details, see :ref:`EVS Replication Pair Status (Deprecated) <evs_04_0042>`.                                           |
   +----------------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | progress                         | String                | Specifies the synchronization progress of the EVS replication pair.                                                                                                                     |
   |                                  |                       |                                                                                                                                                                                         |
   |                                  |                       | Unit: %                                                                                                                                                                                 |
   +----------------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | failure_detail                   | String                | Specifies the returned error code if the EVS replication pair status is **error**. For details, see :ref:`Details of EVS Replication failure_detail Values (Deprecated) <evs_04_0044>`. |
   +----------------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | record_metadata                  | Object                | Specifies the billing record of the replication pair. For details, see :ref:`Parameters in the record_metadata field <evs_04_2047__li59982790112347>`.                                  |
   +----------------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | fault_level                      | String                | Specifies the fault level of the EVS replication pair. The value can be as follows:                                                                                                     |
   |                                  |                       |                                                                                                                                                                                         |
   |                                  |                       | -  **0**: indicates that no fault occurs.                                                                                                                                               |
   |                                  |                       | -  **2**: indicates that the production disk does not have read/write permissions. In this case, you are advised to perform a failover.                                                 |
   |                                  |                       | -  **5**: indicates that the replication link is disconnected. In this case, a failover cannot be performed. Contact technical support engineers.                                       |
   +----------------------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_2047__li59982790112347:

   Parameters in the **record_metadata** field

   +-------------+---------+-----------------------------------------------------------------------------------+
   | Parameter   | Type    | Description                                                                       |
   +=============+=========+===================================================================================+
   | volume_type | String  | Specifies the type of the EVS disks in the EVS replication pair.                  |
   +-------------+---------+-----------------------------------------------------------------------------------+
   | multiattach | Boolean | Specifies whether the EVS disks in the EVS replication pair are shared EVS disks. |
   +-------------+---------+-----------------------------------------------------------------------------------+
   | volume_size | integer | Specifies the size of each EVS disk in the EVS replication pair. The unit is GB.  |
   +-------------+---------+-----------------------------------------------------------------------------------+

-  Example response

   .. code-block::

      {
          "replication": {
              "status": "available",
              "priority_station": "az2.dc2",
              "volume_ids": "a623cd91-89f9-4baf-a5aa-7774d2bfcb8b,3e8fdded-64bb-4c60-a55e-2e4bc3d240d6",
              "record_metadata": "{\"volume_size\": 10,\"volume_type\": \"ssd\", \"multiattach\": false}",
              "name": "yes",
              "created_at": "2017-09-30T10:14:32.747000",
              "updated_at": "2017-09-30T10:14:34.505912",
              "replication_consistency_group_id": null,
              "replication_status": "active",
              "fault_level": "0",
              "replication_model": "hypermetro",
              "id": "dddd9746-14df-4823-be9d-7b4f4f8518ed",
              "description": "yes",
              "progress": "100"
          }
      }

Status Codes
------------

-  Normal

   ============== =====================================
   Returned Value Description
   ============== =====================================
   200            The server has processed the request.
   ============== =====================================

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
