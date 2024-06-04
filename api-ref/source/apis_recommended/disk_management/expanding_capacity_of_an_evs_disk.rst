:original_name: evs_04_2014.html

.. _evs_04_2014:

Expanding Capacity of an EVS Disk
=================================

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

   ========== ========= =================
   Parameter  Mandatory Description
   ========== ========= =================
   project_id Yes       The project ID.
   volume_id  Yes       The ID of a disk.
   ========== ========= =================

Request
-------

-  Request parameters

   +-----------+--------+-----------+----------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Mandatory | Description                                                                                                          |
   +===========+========+===========+======================================================================================================================+
   | os-extend | Object | Yes       | The disk expansion marker. For details, see :ref:`Parameter in the os-extend field <evs_04_2014__li19185119124117>`. |
   +-----------+--------+-----------+----------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_2014__li19185119124117:

   Parameter in the **os-extend** field

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Type            | Mandatory       | Description                                                                                                                |
   +=================+=================+=================+============================================================================================================================+
   | new_size        | Integer         | Yes             | The new disk size, in GB.                                                                                                  |
   |                 |                 |                 |                                                                                                                            |
   |                 |                 |                 | The new size ranges from the original size to the maximum size (**32768** for a data disk and **1024** for a system disk). |
   |                 |                 |                 |                                                                                                                            |
   |                 |                 |                 | .. note::                                                                                                                  |
   |                 |                 |                 |                                                                                                                            |
   |                 |                 |                 |    If the specified value is a decimal, the number part of the value will be used.                                         |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------+

-  Example request

   .. code-block::

      {
          "os-extend": {
              "new_size": 200
          }
      }

Response
--------

-  Response parameters

   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                     |
   +=======================+=======================+=================================================================================================================================+
   | job_id                | String                | The task ID.                                                                                                                    |
   |                       |                       |                                                                                                                                 |
   |                       |                       | .. note::                                                                                                                       |
   |                       |                       |                                                                                                                                 |
   |                       |                       |    For details about how to query the task status, see :ref:`Querying Task Status <evs_04_0054>`.                               |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------+
   | error                 | Object                | The error message returned if an error occurs. For details, see :ref:`Parameters in the error field <evs_04_2014__li24688256>`. |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_2014__li24688256:

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
