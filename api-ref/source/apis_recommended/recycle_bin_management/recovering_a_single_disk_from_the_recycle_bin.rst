:original_name: revertSingleDiskInRecycleBin.html

.. _revertSingleDiskInRecycleBin:

Recovering a Single Disk from the Recycle Bin
=============================================

Function
--------

This API is used to recover a single disk from the recycle bin.

URI
---

POST /v3/{project_id}/recycle-bin-volumes/{volume_id}/revert

.. table:: **Table 1** URI parameters

   +-----------------+-----------------+-----------------+------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                      |
   +=================+=================+=================+==================================================================+
   | project_id      | Yes             | String          | **Definition**                                                   |
   |                 |                 |                 |                                                                  |
   |                 |                 |                 | The project ID.                                                  |
   |                 |                 |                 |                                                                  |
   |                 |                 |                 | **Constraints**                                                  |
   |                 |                 |                 |                                                                  |
   |                 |                 |                 | N/A                                                              |
   |                 |                 |                 |                                                                  |
   |                 |                 |                 | **Range**                                                        |
   |                 |                 |                 |                                                                  |
   |                 |                 |                 | N/A                                                              |
   |                 |                 |                 |                                                                  |
   |                 |                 |                 | **Default Value**                                                |
   |                 |                 |                 |                                                                  |
   |                 |                 |                 | N/A                                                              |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------+
   | volume_id       | Yes             | String          | **Definition**                                                   |
   |                 |                 |                 |                                                                  |
   |                 |                 |                 | The disk ID.                                                     |
   |                 |                 |                 |                                                                  |
   |                 |                 |                 | You can query details about all EVS disks to obtain the disk ID. |
   |                 |                 |                 |                                                                  |
   |                 |                 |                 | **Constraints**                                                  |
   |                 |                 |                 |                                                                  |
   |                 |                 |                 | N/A                                                              |
   |                 |                 |                 |                                                                  |
   |                 |                 |                 | **Range**                                                        |
   |                 |                 |                 |                                                                  |
   |                 |                 |                 | N/A                                                              |
   |                 |                 |                 |                                                                  |
   |                 |                 |                 | **Default Value**                                                |
   |                 |                 |                 |                                                                  |
   |                 |                 |                 | N/A                                                              |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------+

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

**Status code: 204**

No Content

**Status code: 400**

.. table:: **Table 3** Response body parameter

   +-----------------------+------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                                                                         | Description                                                                                                                    |
   +=======================+==============================================================================================================================+================================================================================================================================+
   | error                 | :ref:`Error <revertsinglediskinrecyclebin__en-us_topic_0000002459655764_en-us_topic_0000002459812642_response_error>` object | **Definition**                                                                                                                 |
   |                       |                                                                                                                              |                                                                                                                                |
   |                       |                                                                                                                              | The error code returned if an error occurs. For details about the error code, see :ref:`Error Code Description <evs_04_0038>`. |
   |                       |                                                                                                                              |                                                                                                                                |
   |                       |                                                                                                                              | **Range**                                                                                                                      |
   |                       |                                                                                                                              |                                                                                                                                |
   |                       |                                                                                                                              | N/A                                                                                                                            |
   +-----------------------+------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------+

.. _revertsinglediskinrecyclebin__en-us_topic_0000002459655764_en-us_topic_0000002459812642_response_error:

.. table:: **Table 4** Error

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

   POST https://{endpoint}/v3/490e121341fc481d95f946ef844cb06a/recycle-bin-volumes/55b4c5a7-a82e-4881-9463-f8fbf8730d4f/revert

Example Response
----------------

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
204         No Content
400         Bad Request
=========== ===========

Error Codes
-----------

For details, see :ref:`Error Codes <evs_04_0038>`.
