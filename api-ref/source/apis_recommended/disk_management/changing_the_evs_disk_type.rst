:original_name: evs_04_4008.html

.. _evs_04_4008:

Changing the EVS Disk Type
==========================

Function
--------

This API is used to change the type of a disk.

URI
---

POST /v2/{project_id}/volumes/{volume_id}/retype

.. table:: **Table 1** Path parameters

   ========== ========= ====== ===============
   Parameter  Mandatory Type   Description
   ========== ========= ====== ===============
   project_id Yes       String The project ID.
   volume_id  Yes       String The disk ID.
   ========== ========= ====== ===============

Request Parameters
------------------

.. table:: **Table 2** Request body parameter

   +-----------+-----------+----------------------------------------------------------------+-------------------------------------------+
   | Parameter | Mandatory | Type                                                           | Description                               |
   +===========+===========+================================================================+===========================================+
   | os-retype | Yes       | :ref:`RetypeVolume <evs_04_4008__request_retypevolume>` object | The request body of the disk type change. |
   +-----------+-----------+----------------------------------------------------------------+-------------------------------------------+

.. _evs_04_4008__request_retypevolume:

.. table:: **Table 3** RetypeVolume

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                                                                  |
   +=================+=================+=================+==============================================================================================================================================================================================================================================================================+
   | new_type        | Yes             | String          | The new disk type. For details about the disk type change, see `Changing the Disk Type <https://docs.otc.t-systems.com/elastic-volume-service/umn/changing_the_evs_disk_type.html>`__.                                                                                       |
   |                 |                 |                 |                                                                                                                                                                                                                                                                              |
   |                 |                 |                 | .. note::                                                                                                                                                                                                                                                                    |
   |                 |                 |                 |                                                                                                                                                                                                                                                                              |
   |                 |                 |                 |    -  If the specified disk type is not available in the AZ, the disk type change will fail.                                                                                                                                                                                 |
   |                 |                 |                 |    -  If the source disk type is backed by SAS, you can change the disk type to any of the other types.                                                                                                                                                                      |
   |                 |                 |                 |    -  If the source disk type is backed by SSD, you can only change to another SSD-backed disk type, but not the SAS-backed type.                                                                                                                                            |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | iops            | No              | Integer         | The IOPS configured for the disk.                                                                                                                                                                                                                                            |
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

.. table:: **Table 4** Response body parameter

   ========= ====== ============
   Parameter Type   Description
   ========= ====== ============
   job_id    String The task ID.
   ========= ====== ============

**Status code: 400**

.. table:: **Table 5** Response body parameter

   +-----------+---------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type                                              | Description                                                                                                         |
   +===========+===================================================+=====================================================================================================================+
   | error     | :ref:`Error <evs_04_4008__response_error>` object | The error code returned if an error occurs. For details about the error code, see :ref:`Error Codes <evs_04_0038>`. |
   +-----------+---------------------------------------------------+---------------------------------------------------------------------------------------------------------------------+

.. _evs_04_4008__response_error:

.. table:: **Table 6** Error

   +-----------+--------+---------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                                         |
   +===========+========+=====================================================================================================================+
   | code      | String | The error code returned if an error occurs. For details about the error code, see :ref:`Error Codes <evs_04_0038>`. |
   +-----------+--------+---------------------------------------------------------------------------------------------------------------------+
   | message   | String | The error message returned if an error occurs.                                                                      |
   +-----------+--------+---------------------------------------------------------------------------------------------------------------------+

Example Request
---------------

.. code-block::

   https://{endpoint}/v2/{project_id}/volumes/{volume_id}/retype

   {
     "os-retype" : {
       "new_type" : "SAS"
     }
   }

Example Response
----------------

**Status code: 202**

Accepted

-  Example 1

   .. code-block::

      {
        "job_id" : "4011af9965d85d3c0165d8628c650007"
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
202         Accepted
400         Bad Request
=========== ===========

Error Codes
-----------

For details, see :ref:`Error Codes <evs_04_0038>`.
