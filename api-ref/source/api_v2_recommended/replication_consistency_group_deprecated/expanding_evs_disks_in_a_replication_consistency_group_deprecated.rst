:original_name: evs_04_2059.html

.. _evs_04_2059:

Expanding EVS Disks in a Replication Consistency Group (Deprecated)
===================================================================

Function
--------

This API is used to expand the EVS disks in one or multiple EVS replication pairs. In such an expansion operation, two EVS disks in one EVS replication pair are expanded together.

.. note::

   The **status** and **replication_status** values of the replication consistency group remain unchanged before and after capacity expansion. When **200** is returned, the capacity expansion is complete.

   If the expansion fails, contact technical support engineers to locate and rectify the fault. After the fault is rectified, expand the disks again.

   If the capacities of multiple EVS replication pairs in a protection group are expanded, an error indicating incorrect capacity will occur after the capacity expansion.

   This API has been deprecated. To use this function, see `Storage Disaster Recovery Service API Reference <https://docs.otc.t-systems.com/en-us/api/sdrs/sdrs_01_0000.html>`__.

Constraints
-----------

-  The **status** value of the replication consistency group must be **available**.
-  The **replication_status** value of the replication consistency group cannot be **error**.

URI
---

-  URI

   POST /v2/{project_id}/os-vendor-replication-consistency-groups/{replication_consistency_group_id}/action

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

   +-------------------------------+-----------+--------+-------------------------------------------------------------------------------+
   | Parameter                     | Mandatory | Type   | Description                                                                   |
   +===============================+===========+========+===============================================================================+
   | os-extend-replication-volumes | Yes       | Object | Specifies the EVS disk expansion operation.                                   |
   +-------------------------------+-----------+--------+-------------------------------------------------------------------------------+
   | replications                  | Yes       | list   | Specifies the expansion information of one or multiple EVS replication pairs. |
   +-------------------------------+-----------+--------+-------------------------------------------------------------------------------+

-  Parameters in the **replications** field

   +-----------+-----------+---------+------------------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type    | Description                                                                              |
   +===========+===========+=========+==========================================================================================+
   | id        | Yes       | String  | Specifies the IDs of EVS replication pairs.                                              |
   +-----------+-----------+---------+------------------------------------------------------------------------------------------+
   | new_size  | Yes       | integer | Specifies the disk capacity after expansion in the EVS replication pair. The unit is GB. |
   +-----------+-----------+---------+------------------------------------------------------------------------------------------+

-  Example request

   .. code-block::

      {
          "os-extend-replication-volumes": {
              "replications": [
                  {"id": "25132c7a-bf71-4d18-8a2e-1ad11416c057", "new_size": 10},
                  {"id": "6a61d65c-269e-4592-8a89-95742b075b1a", "new_size": 20}
              ]
          }
      }

Response
--------

None

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
