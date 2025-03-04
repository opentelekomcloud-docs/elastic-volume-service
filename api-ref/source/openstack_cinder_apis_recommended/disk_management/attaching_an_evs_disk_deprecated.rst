:original_name: evs_04_2087.html

.. _evs_04_2087:

Attaching an EVS Disk (Deprecated)
==================================

Function
--------

This API is only used to change the EVS disk status from **available** to **in-use**.

.. important::

   This API call exists for compatibility reasons only and is not meant to be used.

Constraints
-----------

Do not call this API to attach a disk. If you need to attach a disk, call the ECS Attach Volume API.

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

   +-----------+--------+-----------+------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Mandatory | Description                                                                                                            |
   +===========+========+===========+========================================================================================================================+
   | os-attach | Object | Yes       | The disk attachment marker. For details, see :ref:`Parameters in the os-attach field <evs_04_2087__li11686008105423>`. |
   +-----------+--------+-----------+------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_2087__li11686008105423:

   Parameters in the **os-attach** field

   +---------------+--------+-----------+---------------------------------------------------------------------------------------+
   | Parameter     | Type   | Mandatory | Description                                                                           |
   +===============+========+===========+=======================================================================================+
   | instance_uuid | String | Yes       | The UUID of the host to be attached to.                                               |
   +---------------+--------+-----------+---------------------------------------------------------------------------------------+
   | mountpoint    | String | Yes       | The device name.                                                                      |
   +---------------+--------+-----------+---------------------------------------------------------------------------------------+
   | host_name     | String | No        | The name of the host to be attached to. The value can contain a maximum of 255 bytes. |
   +---------------+--------+-----------+---------------------------------------------------------------------------------------+
   | mode          | String | No        | The attachment mode. The value can be **rw** (read/write) or **ro** (read-only).      |
   +---------------+--------+-----------+---------------------------------------------------------------------------------------+

-  Example request

   .. code-block:: text

      POST https://{endpoint}/v2/{project_id}/volumes/b104b8db-170d-441b-897a-3c8ba9c5a214/action
      {
          "os-attach": {
              "instance_uuid": "95D9EF50-507D-11E5-B970-0800200C9A66",
              "mountpoint": "/dev/vdc"
          }
      }

Response
--------

-  Parameter description

   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                                                          |
   +===========+========+======================================================================================================================================+
   | error     | Object | The error message returned if an error occurs. For details, see :ref:`Parameters in the error field <evs_04_2087__li0419202382514>`. |
   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_2087__li0419202382514:

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
