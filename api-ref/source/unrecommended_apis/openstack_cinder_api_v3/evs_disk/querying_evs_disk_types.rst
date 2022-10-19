:original_name: evs_04_3035.html

.. _evs_04_3035:

Querying EVS Disk Types
=======================

Function
--------

This API is used to query EVS disk types and display the query results in a list.

URI
---

-  URI format

   GET /v3/{project_id}/types

-  Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   ========== ========= =========================

Request
-------

-  Example request

   .. code-block:: text

      GET https://{endpoint}/v3/{project_id}/types

Response
--------

-  Parameter description

   +--------------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Type   | Description                                                                                                                                                  |
   +==============+========+==============================================================================================================================================================+
   | volume_types | list   | Specifies the list of queried disk types. For details, see :ref:`Parameters in the volume_types field <evs_04_3035__evs_04_2071_li61994451201537>`.          |
   +--------------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | error        | Object | Specifies the error message returned when an error occurs. For details, see :ref:`Parameters in the error field <evs_04_3035__evs_04_2071_li0419202382514>`. |
   +--------------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_3035__evs_04_2071_li61994451201537:

   Parameters in the **volume_types** field

   +--------------+---------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Type    | Description                                                                                                                                    |
   +==============+=========+================================================================================================================================================+
   | extra_specs  | Object  | Specifies the disk type specifications. For details, see :ref:`Parameters in the extra_specs field <evs_04_3035__evs_04_2071_li963595619529>`. |
   +--------------+---------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | name         | String  | Specifies the name of the disk type.                                                                                                           |
   +--------------+---------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | id           | String  | Specifies the ID of the disk type.                                                                                                             |
   +--------------+---------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | description  | String  | Specifies the description of the disk type.                                                                                                    |
   +--------------+---------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | qos_specs_id | String  | Reserved field                                                                                                                                 |
   +--------------+---------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | is_public    | Boolean | Reserved field                                                                                                                                 |
   +--------------+---------+------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_3035__evs_04_2071_li963595619529:

   Parameters in the **extra_specs** field

   +---------------------------+--------+-------------------------------------------------------+
   | Parameter                 | Type   | Description                                           |
   +===========================+========+=======================================================+
   | volume_backend_name       | String | Reserved field                                        |
   +---------------------------+--------+-------------------------------------------------------+
   | availability-zone         | String | Reserved field                                        |
   +---------------------------+--------+-------------------------------------------------------+
   | HW:availability_zone      | String | Reserved field                                        |
   +---------------------------+--------+-------------------------------------------------------+
   | RESKEY:availability_zones | String | Specifies the AZs that support the current disk type. |
   +---------------------------+--------+-------------------------------------------------------+

-  .. _evs_04_3035__evs_04_2071_li0419202382514:

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
          "volume_types": [
              {
                  "extra_specs": {
                      "volume_backend_name": "SAS",
                      "availability-zone": "az-dc-1"
                  },
                  "name": "SAS",
                  "qos_specs_id": null,
                  "id": "6c81c680-df58-4512-81e7-ecf66d160638",
                  "is_public": true,
                  "description": null
              },
              {
                  "extra_specs": {
                      "volume_backend_name": "SATA",
                      "availability-zone": "az-dc-1"
                  },
                  "name": "SATA",
                  "qos_specs_id": "585f29d6-7147-42e7-bfb8-ca214f640f6f",
                  "is_public": true,
                  "id": "ea6e3c13-aac5-46e0-b280-745ed272e662",
                  "description": null
              },
              {
                  "extra_specs": {
                      "volume_backend_name": "SSD",
                      "availability-zone": "az-dc-1"
                  },
                  "name": "SSD",
                  "qos_specs_id": "39b0c29a-308b-4f86-b478-5d3d02a43837",
                  "is_public": true,
                  "id": "6f2dee9e-82f0-4be3-ad89-bae605a3d24f",
                  "description": null
              }
          ]
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
