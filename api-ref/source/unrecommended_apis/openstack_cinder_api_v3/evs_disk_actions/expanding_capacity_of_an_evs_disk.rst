:original_name: evs_04_3048.html

.. _evs_04_3048:

Expanding Capacity of an EVS Disk
=================================

Function
--------

This API is used to expand the capacity of an EVS disk.

-  If the status of the to-be-expanded disk is **available**, there are no restrictions.
-  If the status of the to-be-expanded disk is **in-use**, the restrictions are as follows:

   -  The shared disk cannot be expanded, that is, the value of parameter **multiattach** must be **false**.
   -  The status of the server to which the disk attached must be **ACTIVE**, **PAUSED**, **SUSPENDED**, or **SHUTOFF**.

URI
---

-  URI format

   POST /v3/{project_id}/volumes/{volume_id}/action

-  Parameter description

   ========== ========= ===========================
   Parameter  Mandatory Description
   ========== ========= ===========================
   project_id Yes       Specifies the project ID.
   volume_id  Yes       Specifies the ID of a disk.
   ========== ========= ===========================

Request
-------

-  Parameter description

   +-----------+--------+-----------+--------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Mandatory | Description                                                                                                                                |
   +===========+========+===========+============================================================================================================================================+
   | os-extend | Object | Yes       | Specifies the disk expansion marker. For details, see :ref:`Parameter in the os-extend field <evs_04_3048__evs_04_2083_li11686008105423>`. |
   +-----------+--------+-----------+--------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_3048__evs_04_2083_li11686008105423:

   Parameter in the **os-extend** field

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Type            | Mandatory       | Description                                                                                                                          |
   +=================+=================+=================+======================================================================================================================================+
   | new_size        | Integer         | Yes             | Specifies the size of the disk after capacity expansion, in GB.                                                                      |
   |                 |                 |                 |                                                                                                                                      |
   |                 |                 |                 | The new disk size ranges from the original disk size to the maximum size (**32768** for a data disk and **1024** for a system disk). |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   .. code-block::

      {
          "os-extend": {
              "new_size": 100
          }
      }

Response
--------

-  Parameter description

   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                                                                                  |
   +===========+========+==============================================================================================================================================================+
   | error     | Object | Specifies the error message returned when an error occurs. For details, see :ref:`Parameters in the error field <evs_04_3048__evs_04_2083_li0419202382514>`. |
   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_3048__evs_04_2083_li0419202382514:

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

   None

   or

   .. code-block::

      {
          "error": {
              "message": "XXXX",
              "code": "XXX"
          }
      }

   In the preceding example, **error** indicates a general error, for example, **badRequest** or **itemNotFound**. An example is provided as follows:

   .. code-block::

      {
          "badRequest": {
              "message": "XXXX",
              "code": "XXX"
          }
      }

Status Codes
------------

-  Normal

   202

Error Codes
-----------

For details, see :ref:`Error Codes <evs_04_0038>`.
