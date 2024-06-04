:original_name: evs_04_2081.html

.. _evs_04_2081:

Querying All AZs
================

Function
--------

This API is used to query all AZs.

URI
---

-  URI format

   GET /v2/{project_id}/os-availability-zone

-  Parameter description

   ========== ========= ===============
   Parameter  Mandatory Description
   ========== ========= ===============
   project_id Yes       The project ID.
   ========== ========= ===============

Request
-------

-  Example request

   .. code-block:: text

      GET https://{endpoint}/v2/{project_id}/os-availability-zone

Response
--------

-  Response parameters

   +----------------------+--------+--------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter            | Type   | Description                                                                                                                          |
   +======================+========+======================================================================================================================================+
   | availabilityZoneInfo | list   | The list of queried AZs. For details, see :ref:`Parameters in the availabilityZoneInfo field <evs_04_2081__li19751007201910>`.       |
   +----------------------+--------+--------------------------------------------------------------------------------------------------------------------------------------+
   | error                | Object | The error message returned if an error occurs. For details, see :ref:`Parameters in the error field <evs_04_2081__li0419202382514>`. |
   +----------------------+--------+--------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_2081__li19751007201910:

   Parameters in the **availabilityZoneInfo** field

   +-----------+--------+----------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                              |
   +===========+========+==========================================================================================================+
   | zoneState | Object | The AZ status. For details, see :ref:`Parameter in the zoneState field <evs_04_2081__li11149334112511>`. |
   +-----------+--------+----------------------------------------------------------------------------------------------------------+
   | zoneName  | String | The AZ name.                                                                                             |
   +-----------+--------+----------------------------------------------------------------------------------------------------------+

-  .. _evs_04_2081__li11149334112511:

   Parameter in the **zoneState** field

   +-----------------------+-----------------------+------------------------------+
   | Parameter             | Type                  | Description                  |
   +=======================+=======================+==============================+
   | available             | Boolean               | Whether the AZ is available. |
   |                       |                       |                              |
   |                       |                       | -  **true**: available       |
   |                       |                       | -  **false**: unavailable    |
   +-----------------------+-----------------------+------------------------------+

-  .. _evs_04_2081__li0419202382514:

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
          "availabilityZoneInfo": [
              {
                  "zoneState": {
                      "available": true
                  },
                  "zoneName": "az-dc-1"
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

Status Codes
------------

-  Normal

   200

Error Codes
-----------

For details, see :ref:`Error Codes <evs_04_0038>`.
