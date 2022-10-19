:original_name: evs_04_2014.html

.. _evs_04_2014:

Expanding Capacity of an EVS Disk (Deprecated)
==============================================

Function
--------

This API is used to expand the capacity of an EVS disk.

-  If the status of the to-be-expanded disk is **available**, there are no restrictions.
-  If the status of the to-be-expanded disk is **in-use**, the restrictions are as follows:

   -  A shared disk cannot be expanded, that is, the value of parameter **multiattach** must be **false**.
   -  The status of the server to which the disk attached must be **ACTIVE**, **PAUSED**, **SUSPENDED**, or **SHUTOFF**.

.. important::

   This API call exists for compatibility reasons only and is not meant to be used.

URI
---

-  URI format

   POST /v2/{project_id}/cloudvolumes/{volume_id}/action

-  Parameter description

   ========== ========= =============================
   Parameter  Mandatory Description
   ========== ========= =============================
   project_id Yes       Specifies the project ID.
   volume_id  Yes       Specifies the ID of the disk.
   ========== ========= =============================

Request
-------

-  Parameter description

   +-----------+--------+-----------+--------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Mandatory | Description                                                                                                                    |
   +===========+========+===========+================================================================================================================================+
   | os-extend | Object | Yes       | Specifies the disk expansion marker. For details, see :ref:`Parameter in the os-extend field <evs_04_2014__li19185119124117>`. |
   +-----------+--------+-----------+--------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_2014__li19185119124117:

   Parameter in the **os-extend** field

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Type            | Mandatory       | Description                                                                                                                          |
   +=================+=================+=================+======================================================================================================================================+
   | new_size        | Integer         | Yes             | Specifies the size of the disk after capacity expansion, in GB.                                                                      |
   |                 |                 |                 |                                                                                                                                      |
   |                 |                 |                 | The new disk size ranges from the original disk size to the maximum size (**32768** for a data disk and **1024** for a system disk). |
   |                 |                 |                 |                                                                                                                                      |
   |                 |                 |                 | .. note::                                                                                                                            |
   |                 |                 |                 |                                                                                                                                      |
   |                 |                 |                 |    If the specified parameter value is a decimal, the integral part of the value is used by default when the request is sent.        |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   .. code-block::

      {
          "os-extend": {
              "new_size": 200
          }
      }

Response
--------

-  Parameter description

   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                      |
   +=======================+=======================+==================================================================================================================================================+
   | job_id                | String                | Specifies the task ID.                                                                                                                           |
   |                       |                       |                                                                                                                                                  |
   |                       |                       | .. note::                                                                                                                                        |
   |                       |                       |                                                                                                                                                  |
   |                       |                       |    For details about how to query the task status, see :ref:`Querying Task Status <evs_04_0054>`.                                                |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | error                 | Object                | Specifies the error message returned when an error occurs. For details, see :ref:`Parameters in the error field <evs_04_2014__li0419202382514>`. |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_2014__li0419202382514:

   Parameters in the **error** field

   +-----------------------+-----------------------+-------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                             |
   +=======================+=======================+=========================================================================+
   | message               | String                | Specifies the error message returned when an error occurs.              |
   +-----------------------+-----------------------+-------------------------------------------------------------------------+
   | code                  | String                | Specifies the error code returned when an error occurs.                 |
   |                       |                       |                                                                         |
   |                       |                       | For details about the error code, see :ref:`Error Codes <evs_04_0038>`. |
   +-----------------------+-----------------------+-------------------------------------------------------------------------+

-  Example response

   .. code-block::

      {
          "job_id": "70a599e0-31e7-49b7-b260-868f441e862b"
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
