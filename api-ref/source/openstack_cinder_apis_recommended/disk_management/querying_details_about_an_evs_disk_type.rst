:original_name: evs_04_2072.html

.. _evs_04_2072:

Querying Details About an EVS Disk Type
=======================================

Function
--------

This API is used to query details about an EVS disk type.

URI
---

-  URI format

   GET /v2/{project_id}/types/{type_id}

-  Parameter description

   ========== ========= =================
   Parameter  Mandatory Description
   ========== ========= =================
   project_id Yes       The project ID.
   type_id    Yes       The disk type ID.
   ========== ========= =================

Request
-------

-  Example request

   .. code-block:: text

      GET https://{endpoint}/v2/{project_id}/types/6c81c680-df58-4512-81e7-ecf66d160638

Response
--------

-  Parameter description

   +-------------+--------+--------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Type   | Description                                                                                                                          |
   +=============+========+======================================================================================================================================+
   | volume_type | Object | The details of queried disk types. For details, see :ref:`Parameters in the volume_type field <evs_04_2072__li27654073201555>`.      |
   +-------------+--------+--------------------------------------------------------------------------------------------------------------------------------------+
   | error       | Object | The error message returned if an error occurs. For details, see :ref:`Parameters in the error field <evs_04_2072__li0419202382514>`. |
   +-------------+--------+--------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_2072__li27654073201555:

   Parameters in the **volume_type** field

   +--------------+---------+---------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Type    | Description                                                                                                               |
   +==============+=========+===========================================================================================================================+
   | extra_specs  | Object  | The disk type specifications. For details, see :ref:`Parameters in the extra_specs field <evs_04_2072__li1957456185414>`. |
   +--------------+---------+---------------------------------------------------------------------------------------------------------------------------+
   | name         | String  | The disk type name.                                                                                                       |
   +--------------+---------+---------------------------------------------------------------------------------------------------------------------------+
   | id           | String  | The disk type ID.                                                                                                         |
   +--------------+---------+---------------------------------------------------------------------------------------------------------------------------+
   | description  | String  | The disk type description.                                                                                                |
   +--------------+---------+---------------------------------------------------------------------------------------------------------------------------+
   | qos_specs_id | String  | The reserved field.                                                                                                       |
   +--------------+---------+---------------------------------------------------------------------------------------------------------------------------+
   | is_public    | Boolean | The reserved field.                                                                                                       |
   +--------------+---------+---------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_2072__li1957456185414:

   Parameters in the **extra_specs** field

   +---------------------------+--------+---------------------------------------------+
   | Parameter                 | Type   | Description                                 |
   +===========================+========+=============================================+
   | volume_backend_name       | String | The reserved field.                         |
   +---------------------------+--------+---------------------------------------------+
   | availability-zone         | String | The reserved field.                         |
   +---------------------------+--------+---------------------------------------------+
   | HW:availability_zone      | String | The reserved field.                         |
   +---------------------------+--------+---------------------------------------------+
   | RESKEY:availability_zones | String | The AZs that support the current disk type. |
   +---------------------------+--------+---------------------------------------------+

-  .. _evs_04_2072__li0419202382514:

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
          "volume_type": {
              "extra_specs": {
                  "volume_backend_name": "SSD",
                  "availability-zone": "az-dc-1"
              },
              "name": "SSD",
              "qos_specs_id": null,
              "is_public": true,
              "id": "ea6e3c13-aac5-46e0-b280-745ed272e662",
              "description": null
          }
      }

   or

   .. code-block::

      {
          "error": {
              "message": "XXXX",
              "code": "XXX"
          }
      }

   In the preceding example, **error** indicates a general error, for example, **badrequest** or **itemNotFound**. An example is provided as follows:

   .. code-block::

      {
          "badrequest": {
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
