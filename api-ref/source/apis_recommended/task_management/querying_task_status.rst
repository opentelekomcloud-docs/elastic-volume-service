:original_name: evs_04_0054.html

.. _evs_04_0054:

Querying Task Status
====================

Function
--------

This API is used to query the execution status of tasks, such as the status of disk creation, capacity expansion, and deletion.

URI
---

-  URI format

   GET /v1/{project_id}/jobs/{job_id}

-  Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   job_id     Yes       Specifies the task ID.
   ========== ========= =========================

Request
-------

The following example shows how to query the status of the task whose task ID is ff808081692a62c70169b4dcf9514264.

-  Example request

   .. code-block::

       GET https://{endpoint}/v1/{project_id}/jobs/ff808081692a62c70169b4dcf9514264

Response
--------

-  Parameter description

   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                      |
   +=======================+=======================+==================================================================================================================================================+
   | status                | String                | Specifies the task status.                                                                                                                       |
   |                       |                       |                                                                                                                                                  |
   |                       |                       | -  **SUCCESS**: The task is successfully executed.                                                                                               |
   |                       |                       | -  **RUNNING**: The task is in progress.                                                                                                         |
   |                       |                       | -  **FAIL**: The task fails.                                                                                                                     |
   |                       |                       | -  **INIT**: The task is being initialized.                                                                                                      |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | entities              | Object                | Specifies the response to the task. For details, see :ref:`•Parameters in the entities field <evs_04_0054__li134182540818>`.                     |
   |                       |                       |                                                                                                                                                  |
   |                       |                       | The content for each type of task is different.                                                                                                  |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | job_id                | String                | Specifies the task ID.                                                                                                                           |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | job_type              | String                | Specifies the task type.                                                                                                                         |
   |                       |                       |                                                                                                                                                  |
   |                       |                       | -  **createVolume**: creates a disk.                                                                                                             |
   |                       |                       | -  **batchCreateVolume**: batch creates disks.                                                                                                   |
   |                       |                       | -  **deleteVolume**: deletes a disk.                                                                                                             |
   |                       |                       | -  **extendVolume**: expands the disk capacity.                                                                                                  |
   |                       |                       | -  **bulkDeleteVolume**: batch deletes disks.                                                                                                    |
   |                       |                       | -  **deleteSingleVolume**: deletes disks one by one during a batch deletion.                                                                     |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | begin_time            | String                | Specifies the time when the task was started.                                                                                                    |
   |                       |                       |                                                                                                                                                  |
   |                       |                       | Time format: YYYY-MM-DDTHH:MM:SS.SSS'Z'                                                                                                          |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | end_time              | String                | Specifies the time when the task finished.                                                                                                       |
   |                       |                       |                                                                                                                                                  |
   |                       |                       | Time format: YYYY-MM-DDTHH:MM:SS.SSS'Z'                                                                                                          |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | error_code            | String                | Specifies the returned error code when the task execution fails.                                                                                 |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | fail_reason           | String                | Specifies the cause of the task execution failure.                                                                                               |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | error                 | Object                | Specifies the error message returned when an error occurs. For details, see :ref:`Parameters in the error field <evs_04_0054__li0419202382514>`. |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_0054__li134182540818:

   Parameter in the **entities** field

   +-------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Type             | Description                                                                                                                          |
   +=============+==================+======================================================================================================================================+
   | name        | String           | Specifies the EVS disk name.                                                                                                         |
   +-------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------+
   | size        | Integer          | Specifies the disk size, in GB.                                                                                                      |
   +-------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------+
   | sub_jobs    | Array of Objects | Specifies the information about a sub-job. For details, see :ref:`•Parameters in the sub_jobs field <evs_04_0054__li1622214314366>`. |
   +-------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------+
   | volume_id   | String           | Specifies the disk ID.                                                                                                               |
   +-------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------+
   | volume_type | String           | Specifies the disk type.                                                                                                             |
   +-------------+------------------+--------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_0054__li1622214314366:

   Parameters in the **sub_jobs** field

   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                   |
   +=======================+=======================+===============================================================================================================================+
   | status                | String                | Specifies the task status.                                                                                                    |
   |                       |                       |                                                                                                                               |
   |                       |                       | -  **SUCCESS**: The task is successfully executed.                                                                            |
   |                       |                       | -  **RUNNING**: The task is in progress.                                                                                      |
   |                       |                       | -  **FAIL**: The task fails.                                                                                                  |
   |                       |                       | -  **INIT**: The task is being initialized.                                                                                   |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------+
   | entities              | Object                | Specifies the response to the task. For details, see :ref:`•Parameters in the entities field <evs_04_0054__li7735129144218>`. |
   |                       |                       |                                                                                                                               |
   |                       |                       | The content for each type of task is different.                                                                               |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------+
   | job_id                | String                | Specifies the task ID.                                                                                                        |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------+
   | job_type              | String                | Specifies the task type.                                                                                                      |
   |                       |                       |                                                                                                                               |
   |                       |                       | -  **createVolume**: creates a disk.                                                                                          |
   |                       |                       | -  **batchCreateVolume**: batch creates disks.                                                                                |
   |                       |                       | -  **deleteVolume**: deletes a disk.                                                                                          |
   |                       |                       | -  **extendVolume**: expands the disk capacity.                                                                               |
   |                       |                       | -  **bulkDeleteVolume**: batch deletes disks.                                                                                 |
   |                       |                       | -  **deleteSingleVolume**: deletes disks one by one during a batch deletion.                                                  |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------+
   | begin_time            | String                | Specifies the time when the task was started.                                                                                 |
   |                       |                       |                                                                                                                               |
   |                       |                       | Time format: YYYY-MM-DDTHH:MM:SS.SSS'Z'                                                                                       |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------+
   | end_time              | String                | Specifies the time when the task finished.                                                                                    |
   |                       |                       |                                                                                                                               |
   |                       |                       | Time format: YYYY-MM-DDTHH:MM:SS.SSS'Z'                                                                                       |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------+
   | error_code            | String                | Specifies the returned error code when the task execution fails.                                                              |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------+
   | fail_reason           | String                | Specifies the cause of the task execution failure.                                                                            |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_0054__li7735129144218:

   Parameter in the **entities** field

   =========== ======= ===============================
   Parameter   Type    Description
   =========== ======= ===============================
   name        String  Specifies the EVS disk name.
   size        Integer Specifies the disk size, in GB.
   volume_id   String  Specifies the disk ID.
   volume_type String  Specifies the disk type.
   =========== ======= ===============================

-  .. _evs_04_0054__li0419202382514:

   Parameters in the **error** field

   +-----------------------+-----------------------+-------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                             |
   +=======================+=======================+=========================================================================+
   | message               | String                | The error message returned if an error occurs.                          |
   +-----------------------+-----------------------+-------------------------------------------------------------------------+
   | code                  | String                | The error code returned if an error occurs.                             |
   |                       |                       |                                                                         |
   |                       |                       | For details about the error code, see :ref:`Error Codes <evs_04_0038>`. |
   +-----------------------+-----------------------+-------------------------------------------------------------------------+

-  Example response

   .. code-block::

      {
          "status": "RUNNING",
          "entities": {
              "volume_id": "bdf1bb37-f20f-4266-9a04-f43e0a127376"
          },
          "job_id": "4010a32d535527910153552b492c0002",
          "job_type": "createVolume",
          "begin_time": "2016-03-08T07:40:13.219Z",
          "end_time": "",
          "error_code": null,
          "fail_reason": null
      }

   or

   .. code-block::

      {
          "status": "SUCCESS",
          "entities": {
              "sub_jobs": [
                  {
                      "status": "SUCCESS",
                      "entities": {
                          "volume_id": "0b549095-4937-4849-8e4c-52aa027d64f7"
                      },
                      "job_id": "21917a8d52a19b040152a9f2f2e50041",
                      "job_type": "createVolume",
                      "begin_time": "2016-02-04T01:43:37.445Z",
                      "end_time": "2016-02-04T01:44:02.239Z",
                      "error_code": null,
                      "fail_reason": null
                  },
                  {
                      "status": "SUCCESS",
                      "entities": {
                          "volume_id": "e7bca1a2-d3ed-434f-86f4-a1f11aa80072"
                      },
                      "job_id": "21917a8d52a19b040152a9f2f2f60042",
                      "job_type": "createVolume",
                      "begin_time": "2016-02-04T01:43:37.462Z",
                      "end_time": "2016-02-04T01:44:02.245Z",
                      "error_code": null,
                      "fail_reason": null
                  }
              ]
          },
          "job_id": "21917a8d52a19b040152a9f2f1eb003e",
          "job_type": "batchCreateVolume",
          "begin_time": "2016-02-04T01:43:37.193Z",
          "end_time": "2016-02-04T01:44:08.283Z",
          "error_code": null,
          "fail_reason": null
      }

   or

   .. code-block::

      {
          "error": {
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
