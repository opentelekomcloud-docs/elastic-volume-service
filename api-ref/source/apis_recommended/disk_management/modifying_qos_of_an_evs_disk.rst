:original_name: evs_04_4009.html

.. _evs_04_4009:

Modifying QoS of an EVS Disk
============================

Function
--------

This API is used to change the IOPS or throughput of an EVS disk.

Constraints
-----------

The disk must be in the **available** or **in-use** state. For a General Purpose SSD V2 disk, both the IOPS and throughput can be changed. This API is not supported for other types of EVS disks.

URI
---

PUT /v5/{project_id}/cloudvolumes/{volume_id}/qos

.. table:: **Table 1** Path parameters

   ========== ========= ====== ===============
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===============
   project_id Yes       String The project ID.
   volume_id  Yes       String The disk ID.
   ========== ========= ====== ===============

Request Parameters
------------------

.. table:: **Table 2** Request header parameter

   +--------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                                               |
   +==============+===========+========+===========================================================================================================================================================================+
   | X-Auth-Token | Yes       | String | The user token. It can be obtained by calling the IAM API that is used to obtain a user token. The value of **X-Subject-Token** in the response header is the user token. |
   +--------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** Request body parameter

   +------------+-----------+----------------------------------------------------------------------------------+-----------------------------+
   | Parameter  | Mandatory | Type                                                                             | Description                 |
   +============+===========+==================================================================================+=============================+
   | qos_modify | Yes       | :ref:`ModifyVolumeQoSOption <evs_04_4009__request_modifyvolumeqosoption>` object | The disk QoS change marker. |
   +------------+-----------+----------------------------------------------------------------------------------+-----------------------------+

.. _evs_04_4009__request_modifyvolumeqosoption:

.. table:: **Table 4** ModifyVolumeQoSOption

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                                                                  |
   +=================+=================+=================+==============================================================================================================================================================================================================================================================================+
   | iops            | Yes             | Integer         | The IOPS configured for the disk.                                                                                                                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                                                                                                                              |
   |                 |                 |                 | This parameter is mandatory when you purchase general purpose SSD V2 disks. This parameter is not available for other types of EVS disks.                                                                                                                                    |
   |                 |                 |                 |                                                                                                                                                                                                                                                                              |
   |                 |                 |                 | .. note::                                                                                                                                                                                                                                                                    |
   |                 |                 |                 |                                                                                                                                                                                                                                                                              |
   |                 |                 |                 |    To learn the IOPS ranges of general purpose SSD V2 disks, see the EVS performance data table in `Disk Types and Performance <https://docs.otc.t-systems.com/elastic-volume-service/umn/service_overview/disk_types_and_performance.html#en-us-topic-0014580744>`__.       |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | throughput      | No              | Integer         | The throughput configured for the disk.                                                                                                                                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                                                                                                                              |
   |                 |                 |                 | This parameter is only mandatory when you purchase a general purpose SSD V2 disk.                                                                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                                                                                                                              |
   |                 |                 |                 | .. note::                                                                                                                                                                                                                                                                    |
   |                 |                 |                 |                                                                                                                                                                                                                                                                              |
   |                 |                 |                 |    To learn the throughput ranges of general purpose SSD V2 disks, see the EVS performance data table in `Disk Types and Performance <https://docs.otc.t-systems.com/elastic-volume-service/umn/service_overview/disk_types_and_performance.html#en-us-topic-0014580744>`__. |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 202**

.. table:: **Table 5** Response body parameter

   +-----------------------+-----------------------+-----------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                 |
   +=======================+=======================+=============================================================================+
   | job_id                | String                | The task ID.                                                                |
   |                       |                       |                                                                             |
   |                       |                       | .. note::                                                                   |
   |                       |                       |                                                                             |
   |                       |                       |    To query the task status, see :ref:`Querying Task Status <evs_04_0054>`. |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------+

**Status code: 400**

.. table:: **Table 6** Response body parameter

   +-----------+---------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type                                              | Description                                                                                                         |
   +===========+===================================================+=====================================================================================================================+
   | error     | :ref:`Error <evs_04_4009__response_error>` object | The error code returned if an error occurs. For details about the error code, see :ref:`Error Codes <evs_04_0038>`. |
   +-----------+---------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+

.. _evs_04_4009__response_error:

.. table:: **Table 7** Error

   +-----------+--------+---------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                                         |
   +===========+========+=====================================================================================================================+
   | code      | String | The error code returned if an error occurs. For details about the error code, see :ref:`Error Codes <evs_04_0038>`. |
   +-----------+--------+---------------------------------------------------------------------------------------------------------------------+
   | message   | String | The error message returned if an error occurs.                                                                      |
   +-----------+--------+---------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

.. code-block:: text

   PUT https://{endpoint}/v5/{project_id}/cloudvolumes/{volume_id}/qos

   {
     "qos_modify" : {
       "iops" : 10000,
       "throughput" : 200
     }
   }

Example Response
----------------

**Status code: 202**

Accepted

.. code-block::

   {
     "job_id" : "70a599e0-31e7-49b7-b260-868f441e862b"
   }

**Status code: 400**

Bad Request

.. code-block::

   {
     "error" : {
       "code" : "XXXX",
       "message" : "XXX"
     }
   }

Status Codes
------------

=========== ===========
Status Code Description
=========== ===========
202         Accepted
400         Bad Request
=========== ===========

Error Codes
-----------

For details, see :ref:`Error Codes <evs_04_0038>`.
