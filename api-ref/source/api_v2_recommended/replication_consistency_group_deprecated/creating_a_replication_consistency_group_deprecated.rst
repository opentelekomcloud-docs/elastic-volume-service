:original_name: evs_04_2049.html

.. _evs_04_2049:

Creating a Replication Consistency Group (Deprecated)
=====================================================

Function
--------

This API is used to create a replication consistency group for the specified EVS replication pairs.

.. note::

   This API has been deprecated. To use this function, see `Storage Disaster Recovery Service API Reference <https://docs.otc.t-systems.com/en-us/api/sdrs/sdrs_01_0000.html>`__.

Constraints
-----------

-  At least one EVS replication pair must be added when you create the replication consistency group.
-  The EVS replication pairs to be added to the group must be in the **available** state.

URI
---

-  URI format

   POST /v2/{project_id}/os-vendor-replication-consistency-groups

-  Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   ========== ========= =========================

Request
-------

-  Parameter description

   +-------------------------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                     | Mandatory | Type   | Description                                                                                                                                                                           |
   +===============================+===========+========+=======================================================================================================================================================================================+
   | replication_consistency_group | Yes       | Object | Specifies to create the replication consistency group. For details, see :ref:`•Parameters in the replication_consistency_group field <evs_04_2049__en-us_topic_0079693007_li206293>`. |
   +-------------------------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_2049__en-us_topic_0079693007_li206293:

   Parameters in the **replication_consistency_group** field

   +-------------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------+
   | Parameter         | Mandatory | Type   | Description                                                                                                         |
   +===================+===========+========+=====================================================================================================================+
   | name              | No        | String | Specifies the name of the replication consistency group. The name can contain a maximum of 255 bytes.               |
   +-------------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------+
   | description       | No        | String | Specifies the description of the replication consistency group. The description can contain a maximum of 255 bytes. |
   +-------------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------+
   | replication_ids   | Yes       | list   | Specifies the IDs of the EVS replication pairs used to create the replication consistency group.                    |
   +-------------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------+
   | priority_station  | Yes       | String | Specifies the current primary AZ, that is, the AZ where the production disks belong.                                |
   +-------------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------+
   | replication_model | Yes       | String | Specifies the type of the created replication consistency group. Currently, only type **hypermetro** is supported.  |
   +-------------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------+

-  Example request

   .. code-block::

      {
          "replication_consistency_group": {
              "name": "my replication consistency group",
              "description": "my replication consistency group",
              "replication_ids": [
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

   +-------------------------------+----------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                     | Type     | Description                                                                                                                                         |
   +===============================+==========+=====================================================================================================================================================+
   | replication_consistency_group | Object   | Specifies the replication consistency group information.                                                                                            |
   +-------------------------------+----------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
   | id                            | String   | Specifies the ID of the replication consistency group.                                                                                              |
   +-------------------------------+----------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
   | name                          | String   | Specifies the name of the replication consistency group.                                                                                            |
   +-------------------------------+----------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
   | description                   | String   | Specifies the description of the replication consistency group.                                                                                     |
   +-------------------------------+----------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
   | status                        | String   | Specifies the status of the replication consistency group. For details, see :ref:`Replication Consistency Group Status (Deprecated) <evs_04_0043>`. |
   +-------------------------------+----------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
   | priority_station              | String   | Specifies the primary site of the replication consistency group.                                                                                    |
   +-------------------------------+----------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
   | created_at                    | datetime | Specifies the creation time.                                                                                                                        |
   +-------------------------------+----------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
   | updated_at                    | datetime | Specifies the update time.                                                                                                                          |
   +-------------------------------+----------+-----------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example response

   .. code-block::

      {
          "replication_consistency_group": {
              "id": "91085433-9499-4a68-b2c6-35072467ccd2",
              "name": "my replication consistency group",
              "description": "my replication consistency group",
              "status": "creating",
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
