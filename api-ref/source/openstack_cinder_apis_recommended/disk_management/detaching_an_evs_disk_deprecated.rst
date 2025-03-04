:original_name: evs_04_2088.html

.. _evs_04_2088:

Detaching an EVS Disk (Deprecated)
==================================

Function
--------

This API is only used to change the EVS disk status from **in-use** to **available**.

.. important::

   This API call exists for compatibility reasons only and is not meant to be used.

Constraints
-----------

Do not call this API to detach a disk. If you need to detach a disk, call the ECS Detach Volume API.

URI
---

-  URI format

   POST /v2/{project_id}/volumes/{volume_id}/action

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

   ========= ====== ========= ===========================
   Parameter Type   Mandatory Description
   ========= ====== ========= ===========================
   os-detach Object Yes       The disk detachment marker.
   ========= ====== ========= ===========================

-  Parameter in the **os-detach** field

   +---------------+--------+-----------+-------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter     | Type   | Mandatory | Description                                                                                                                                     |
   +===============+========+===========+=================================================================================================================================================+
   | attachment_id | String | No        | The attachment ID. If the disk has only one attachment, this parameter is optional. If it has multiple attachments, the parameter is mandatory. |
   +---------------+--------+-----------+-------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   .. code-block:: text

      POST https://{endpoint}/v2/{project_id}/volumes/b104b8db-170d-441b-897a-3c8ba9c5a214/action
      {
          "os-detach": {
              "attachment_id": "d8777f54-84cf-4809-a679-468ffed56cf1"
          }
      }

Response
--------

-  Parameter description

   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                                                          |
   +===========+========+======================================================================================================================================+
   | error     | Object | The error message returned if an error occurs. For details, see :ref:`Parameters in the error field <evs_04_2088__li0419202382514>`. |
   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_2088__li0419202382514:

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

   202

Error Codes
-----------

For details, see :ref:`Error Codes <evs_04_0038>`.
