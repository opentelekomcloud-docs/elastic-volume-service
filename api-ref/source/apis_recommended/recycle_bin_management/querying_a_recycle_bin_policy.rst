:original_name: ShowRecycleBinPolicy.html

.. _ShowRecycleBinPolicy:

Querying a Recycle Bin Policy
=============================

Function
--------

This API is used to query a recycle bin policy.

URI
---

GET /v3/{project_id}/recycle-bin-volumes/policy

.. table:: **Table 1** URI parameter

   +-----------------+-----------------+-----------------+-------------------+
   | Parameter       | Mandatory       | Type            | Description       |
   +=================+=================+=================+===================+
   | project_id      | Yes             | String          | **Definition**    |
   |                 |                 |                 |                   |
   |                 |                 |                 | The project ID.   |
   |                 |                 |                 |                   |
   |                 |                 |                 | **Constraints**   |
   |                 |                 |                 |                   |
   |                 |                 |                 | N/A               |
   |                 |                 |                 |                   |
   |                 |                 |                 | **Range**         |
   |                 |                 |                 |                   |
   |                 |                 |                 | N/A               |
   |                 |                 |                 |                   |
   |                 |                 |                 | **Default Value** |
   |                 |                 |                 |                   |
   |                 |                 |                 | N/A               |
   +-----------------+-----------------+-----------------+-------------------+

Request
-------

.. table:: **Table 2** Request header parameter

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                               |
   +=================+=================+=================+===========================================================================================================================================================+
   | X-Auth-Token    | Yes             | String          | **Definition**                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                           |
   |                 |                 |                 | The user token.                                                                                                                                           |
   |                 |                 |                 |                                                                                                                                                           |
   |                 |                 |                 | It can be obtained by calling the IAM API that is used to obtain a user token. The value of **X-Subject-Token** in the response header is the user token. |
   |                 |                 |                 |                                                                                                                                                           |
   |                 |                 |                 | **Constraints**                                                                                                                                           |
   |                 |                 |                 |                                                                                                                                                           |
   |                 |                 |                 | N/A                                                                                                                                                       |
   |                 |                 |                 |                                                                                                                                                           |
   |                 |                 |                 | **Range**                                                                                                                                                 |
   |                 |                 |                 |                                                                                                                                                           |
   |                 |                 |                 | N/A                                                                                                                                                       |
   |                 |                 |                 |                                                                                                                                                           |
   |                 |                 |                 | **Default Value**                                                                                                                                         |
   |                 |                 |                 |                                                                                                                                                           |
   |                 |                 |                 | N/A                                                                                                                                                       |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------+

Response
--------

**Status code: 200**

.. table:: **Table 3** Response body parameters

   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                               |
   +=======================+=======================+===========================================================================================================================+
   | switch                | Boolean               | **Definition**                                                                                                            |
   |                       |                       |                                                                                                                           |
   |                       |                       | The recycle bin switch.                                                                                                   |
   |                       |                       |                                                                                                                           |
   |                       |                       | **Range**                                                                                                                 |
   |                       |                       |                                                                                                                           |
   |                       |                       | -  **true**: The recycle bin is enabled.                                                                                  |
   |                       |                       |                                                                                                                           |
   |                       |                       | -  **false**: The recycle bin is disabled.                                                                                |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+
   | threshold_time        | Integer               | **Definition**                                                                                                            |
   |                       |                       |                                                                                                                           |
   |                       |                       | A minimum number of days that must pass after a disk was created before it can be moved to the recycle bin upon deletion. |
   |                       |                       |                                                                                                                           |
   |                       |                       | **Range**                                                                                                                 |
   |                       |                       |                                                                                                                           |
   |                       |                       | 1-1000                                                                                                                    |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+
   | keep_time             | Integer               | **Definition**                                                                                                            |
   |                       |                       |                                                                                                                           |
   |                       |                       | The retention period (days) in the recycle bin before the disk is permanently deleted.                                    |
   |                       |                       |                                                                                                                           |
   |                       |                       | **Range**                                                                                                                 |
   |                       |                       |                                                                                                                           |
   |                       |                       | 1-365                                                                                                                     |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+

**Status code: 400**

.. table:: **Table 4** Response body parameter

   +-----------------------+----------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                                                                 | Description                                                                                                                    |
   +=======================+======================================================================================================================+================================================================================================================================+
   | error                 | :ref:`Error <showrecyclebinpolicy__en-us_topic_0000002459815384_en-us_topic_0000002492732193_response_error>` object | **Definition**                                                                                                                 |
   |                       |                                                                                                                      |                                                                                                                                |
   |                       |                                                                                                                      | The error code returned if an error occurs. For details about the error code, see :ref:`Error Code Description <evs_04_0038>`. |
   |                       |                                                                                                                      |                                                                                                                                |
   |                       |                                                                                                                      | **Range**                                                                                                                      |
   |                       |                                                                                                                      |                                                                                                                                |
   |                       |                                                                                                                      | N/A                                                                                                                            |
   +-----------------------+----------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------+

.. _showrecyclebinpolicy__en-us_topic_0000002459815384_en-us_topic_0000002492732193_response_error:

.. table:: **Table 5** Error

   +-----------------------+-----------------------+------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                        |
   +=======================+=======================+====================================================================================+
   | code                  | String                | **Definition**                                                                     |
   |                       |                       |                                                                                    |
   |                       |                       | The error code returned if an error occurs.                                        |
   |                       |                       |                                                                                    |
   |                       |                       | **Range**                                                                          |
   |                       |                       |                                                                                    |
   |                       |                       | For details about the error code, see :ref:`Error Code Description <evs_04_0038>`. |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------+
   | message               | String                | **Definition**                                                                     |
   |                       |                       |                                                                                    |
   |                       |                       | The error message returned if an error occurs.                                     |
   |                       |                       |                                                                                    |
   |                       |                       | **Range**                                                                          |
   |                       |                       |                                                                                    |
   |                       |                       | N/A                                                                                |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------+

Example Request
---------------

.. code-block:: text

   GET https://{endpoint}/v3/490e121341fc481d95f946ef844cb06a/recycle-bin-volumes/policy

Example Response
----------------

**Status code: 200**

OK

.. code-block::

   {
     "switch" : true,
     "threshold_time" : 7,
     "keep_time" : 7
   }

**Status code: 400**

Bad Request

.. code-block::

   {
     "error" : {
       "message" : "XXXX",
       "code" : "XXX"
     }
   }

Status Codes
------------

=========== ===========
Status Code Description
=========== ===========
200         OK
400         Bad Request
=========== ===========

Error Codes
-----------

For details, see :ref:`Error Codes <evs_04_0038>`.
