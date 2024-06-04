:original_name: evs_04_2056.html

.. _evs_04_2056:

Performing a Primary/Secondary Switchover for a Replication Consistency Group (Deprecated)
==========================================================================================

Function
--------

This API is used to perform a primary/secondary switchover for a replication consistency group. A switchover can be performed to switch the primary and secondary AZs of a replication consistency group, which means that the original secondary AZ will be switched to function as the primary AZ, and original DR ECSs and DR disks will be enabled.

After the primary/secondary switchover, the **replication_status** value of the replication consistency group is **active**. At this time, the data between production disks and DR disks in the primary and secondary AZs is consistent in real time, and EVS replication is working normally.

.. note::

   This API has been deprecated. To use this function, see `Storage Disaster Recovery Service API Reference <https://docs.otc.t-systems.com/en-us/api/sdrs/sdrs_01_0000.html>`__.

Constraints
-----------

The data synchronization of the replication consistency group is complete, and the replication consistency group is working normally.

URI
---

-  URI format

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

   +------------------------------------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter                                | Mandatory | Type   | Description                                                                                                                          |
   +==========================================+===========+========+======================================================================================================================================+
   | os-reverse-replication-consistency-group | Yes       | object | The parameter value is null, indicating that a primary/secondary switchover will be performed for the replication consistency group. |
   +------------------------------------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   .. code-block::

      {
          "os-reverse-replication-consistency-group": null
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
