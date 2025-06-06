:original_name: evs_04_3049.html

.. _evs_04_3049:

Setting Bootable Flag for an EVS Disk
=====================================

Function
--------

This API is used to set the bootable flag for an EVS disk.

Constraints
-----------

A data disk cannot be used as system disk for an ECS even if this API has been called to set the bootable flag for it.

URI
---

-  URI format

   POST /v3/{project_id}/volumes/{volume_id}/action

-  Parameter description

   ========== ========= ===============
   Parameter  Mandatory Description
   ========== ========= ===============
   project_id Yes       The project ID.
   volume_id  Yes       The disk ID.
   ========== ========= ===============

Request
-------

-  Parameter description

   +-----------------+--------+-----------+-------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Type   | Mandatory | Description                                                                                                                         |
   +=================+========+===========+=====================================================================================================================================+
   | os-set_bootable | Object | Yes       | The disk bootable flag. For details, see :ref:`Parameter in the os-set_bootable field <evs_04_3049__evs_04_2084_li11686008105423>`. |
   +-----------------+--------+-----------+-------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_3049__evs_04_2084_li11686008105423:

   Parameter in the **os-set_bootable** field

   +-----------------+-----------------+-----------------+------------------------------------------------+
   | Parameter       | Type            | Mandatory       | Description                                    |
   +=================+=================+=================+================================================+
   | bootable        | Boolean         | Yes             | Whether to set the bootable flag for the disk. |
   |                 |                 |                 |                                                |
   |                 |                 |                 | -  **false**: does not set the flag.           |
   |                 |                 |                 | -  **true**: sets the flag.                    |
   +-----------------+-----------------+-----------------+------------------------------------------------+

-  Example request

   .. code-block::

      {
          "os-set_bootable": {
              "bootable": true
          }
      }

Response
--------

-  Parameter description

   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                                                                      |
   +===========+========+==================================================================================================================================================+
   | error     | Object | The error message returned if an error occurs. For details, see :ref:`Parameters in the error field <evs_04_3049__evs_04_2084_li0419202382514>`. |
   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_3049__evs_04_2084_li0419202382514:

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
          "itemNotFound": {
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
