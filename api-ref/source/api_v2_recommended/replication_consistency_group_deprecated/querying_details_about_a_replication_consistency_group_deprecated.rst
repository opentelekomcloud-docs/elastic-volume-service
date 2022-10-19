:original_name: evs_04_2052.html

.. _evs_04_2052:

Querying Details About a Replication Consistency Group (Deprecated)
===================================================================

Function
--------

This API is used to query the details about a replication consistency group, including the name, ID, and status of the consistency group.

.. note::

   This API has been deprecated. To use this function, see `Storage Disaster Recovery Service API Reference <https://docs.otc.t-systems.com/en-us/api/sdrs/sdrs_01_0000.html>`__.

Constraints
-----------

None

URI
---

-  URI format

   GET /v2/{project_id}/os-vendor-replication-consistency-groups/{replication_consistency_group_id}

-  Parameter description

   +----------------------------------+-----------+--------------------------------------------------------+
   | Parameter                        | Mandatory | Description                                            |
   +==================================+===========+========================================================+
   | project_id                       | Yes       | Specifies the project ID.                              |
   +----------------------------------+-----------+--------------------------------------------------------+
   | replication_consistency_group_id | Yes       | Specifies the ID of the replication consistency group. |
   +----------------------------------+-----------+--------------------------------------------------------+

Request
-------

None

Response
--------

-  Parameter description

   +-------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                     | Type                  | Description                                                                                                                                                                                             |
   +===============================+=======================+=========================================================================================================================================================================================================+
   | replication_consistency_group | Object                | Specifies the details of replication consistency groups.                                                                                                                                                |
   +-------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | id                            | String                | Specifies the ID of the replication consistency group.                                                                                                                                                  |
   +-------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                          | String                | Specifies the name of the replication consistency group.                                                                                                                                                |
   +-------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | description                   | String                | Specifies the description of the replication consistency group.                                                                                                                                         |
   +-------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status                        | String                | Specifies the status of the replication consistency group. For details, see :ref:`Replication Consistency Group Status (Deprecated) <evs_04_0043>`.                                                     |
   +-------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | priority_station              | String                | Specifies the primary site of the replication consistency group.                                                                                                                                        |
   +-------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | replication_model             | String                | Specifies the replication type of the replication consistency group.                                                                                                                                    |
   +-------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | replication_status            | String                | Specifies the replication status of the replication consistency group. For details, see :ref:`Replication Consistency Group Status (Deprecated) <evs_04_0043>`.                                         |
   +-------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | replication_ids               | list                  | Specifies the IDs of all EVS replication pairs in the replication consistency group.                                                                                                                    |
   +-------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | created_at                    | datetime              | Specifies the creation time.                                                                                                                                                                            |
   +-------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | updated_at                    | datetime              | Specifies the update time.                                                                                                                                                                              |
   +-------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | failure_detail                | String                | Specifies the returned error code if the status of the replication consistency group is **error**. For details, see :ref:`Details of EVS Replication failure_detail Values (Deprecated) <evs_04_0044>`. |
   +-------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | fault_level                   | String                | Specifies the fault level of the replication consistency group. The value can be as follows:                                                                                                            |
   |                               |                       |                                                                                                                                                                                                         |
   |                               |                       | -  **0**: indicates that no fault occurs.                                                                                                                                                               |
   |                               |                       | -  **2**: indicates that a production disk in the replication consistency group does not have read/write permissions. In this case, you are advised to perform a failover.                              |
   |                               |                       | -  **5**: indicates that the replication link is disconnected. In this case, a failover cannot be performed. Contact technical support engineers.                                                       |
   +-------------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example response

   .. code-block::

      {
          "replication_consistency_group": {
              "id": "bd35d31b-7ab9-47fc-84c6-3d326c6fa6cb",
              "name": " replicationcgtest",
              "description": "my replicationcg pair",
              "status": "available",
              "priority_staion": "az2.dc2",
              "replication_model": "hypermetro",
              "fault_level": "0",
              "replication_status": "active-stopped",
              "replication_ids": [
                  "e5bd643b-7407-4a0e-8d9a-2a88903e8812"
              ],
              "created_at": "2017-09-30T07:37:06.035360",
              "updated_at": null
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
