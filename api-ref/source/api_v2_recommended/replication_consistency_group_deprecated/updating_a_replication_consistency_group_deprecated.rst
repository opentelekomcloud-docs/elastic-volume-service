:original_name: evs_04_2053.html

.. _evs_04_2053:

Updating a Replication Consistency Group (Deprecated)
=====================================================

Function
--------

This API is used to update a replication consistency group. An update includes the following operations:

-  Update the name or description of the replication consistency group.
-  Add EVS replication pairs to or remove EVS replication pairs from the replication consistency group.

   .. note::

      This API has been deprecated. To use this function, see `Storage Disaster Recovery Service API Reference <https://docs.otc.t-systems.com/en-us/api/sdrs/sdrs_01_0000.html>`__.

Constraints
-----------

-  The replication consistency group must be paused before the update.
-  Data needs to be synchronized after a replication consistency group update.

URI
---

-  URI format

   PUT /v2/{project_id}/os-vendor-replication-consistency-groups/{replication_consistency_group_id}

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

-  Parameter description

   +-------------------------------+-----------+--------+----------------------------------------------------------+
   | Parameter                     | Mandatory | Type   | Description                                              |
   +===============================+===========+========+==========================================================+
   | replication_consistency_group | Yes       | Object | Specifies the replication consistency group information. |
   +-------------------------------+-----------+--------+----------------------------------------------------------+

-  Parameters in the **replication_consistency_group** field

   +------------------------+-----------+--------+------------------------------------------------------------------------------------------------------------+
   | Parameter              | Mandatory | Type   | Description                                                                                                |
   +========================+===========+========+============================================================================================================+
   | name                   | No        | String | Specifies the name of the replication consistency group.                                                   |
   +------------------------+-----------+--------+------------------------------------------------------------------------------------------------------------+
   | description            | No        | String | Specifies the description of the replication consistency group.                                            |
   +------------------------+-----------+--------+------------------------------------------------------------------------------------------------------------+
   | replication_model      | No        | String | Specifies the type of the replication consistency group. Currently, only type **hypermetro** is supported. |
   +------------------------+-----------+--------+------------------------------------------------------------------------------------------------------------+
   | add_replication_ids    | No        | list   | Specifies the IDs of the EVS replication pairs to be added.                                                |
   +------------------------+-----------+--------+------------------------------------------------------------------------------------------------------------+
   | remove_replication_ids | No        | list   | Specifies the IDs of the EVS replication pairs to be removed.                                              |
   +------------------------+-----------+--------+------------------------------------------------------------------------------------------------------------+

-  Example request

   .. code-block::

      {
          "replication_consistency_group": {
              "name": "my replication consistency group",
              "description": "my replication consistency group",
              "replication_model": "hypermetro",
              "add_replication_ids": [
                  "0fc12f4e-381d-4f4a-acb0-9890c1683afe",
                  "0aee8399-4aeb-4d84-8d77-9d8a9d3dbe1a"
              ],
              "remove_replication_ids": [
                  "6b27b8b3-95d2-44e3-9cb2-f7de9e8739f2",
                  "cadeda61-7817-466e-bc0c-96448c4d106e"
              ]
          }
      }

Response
--------

-  Parameter description

   +-------------------------------+-----------+--------+------------------------------------------------------------------------+
   | Parameter                     | Mandatory | Type   | Description                                                            |
   +===============================+===========+========+========================================================================+
   | replication_consistency_group | Yes       | Object | Specifies the replication consistency group information.               |
   +-------------------------------+-----------+--------+------------------------------------------------------------------------+
   | id                            | Yes       | String | Specifies the ID of the replication consistency group.                 |
   +-------------------------------+-----------+--------+------------------------------------------------------------------------+
   | name                          | Yes       | String | Specifies the name of the replication consistency group.               |
   +-------------------------------+-----------+--------+------------------------------------------------------------------------+
   | description                   | Yes       | String | Specifies the description of the replication consistency group.        |
   +-------------------------------+-----------+--------+------------------------------------------------------------------------+
   | status                        | Yes       | String | Specifies the status of the replication consistency group.             |
   +-------------------------------+-----------+--------+------------------------------------------------------------------------+
   | priority_station              | Yes       | String | Specifies the primary site of the replication consistency group.       |
   +-------------------------------+-----------+--------+------------------------------------------------------------------------+
   | created_at                    | Yes       | String | Specifies the time when the replication consistency group was created. |
   +-------------------------------+-----------+--------+------------------------------------------------------------------------+
   | updated_at                    | Yes       | String | Specifies the time when the replication consistency group was updated. |
   +-------------------------------+-----------+--------+------------------------------------------------------------------------+

-  Example response

   .. code-block::

      {
          "replication_consistency_group": {
              "id": "91085433-9499-4a68-b2c6-35072467ccd2",
              "name": "my replication consistency group",
              "description": "my replication consistency group",
              "status": "updating",
              "priority_station": "az2.dc2",
              "created_at": "2017-10-19T03:57:36.577967",
              "updated_at": "2017-10-19T04:45:26.467988"
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
