:original_name: evs_04_3045.html

.. _evs_04_3045:

Querying All AZs
================

Function
--------

This API is used to query all AZs.

URI
---

-  URI format

   GET /v3/{project_id}/os-availability-zone

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

      GET https://{endpoint}/v3/{project_id}/os-availability-zone

Response
--------

-  Parameter description

   +----------------------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter            | Type   | Description                                                                                                                                                  |
   +======================+========+==============================================================================================================================================================+
   | availabilityZoneInfo | list   | Specifies the list of queried AZs. For details, see :ref:`Parameters in the availabilityZoneInfo field <evs_04_3045__evs_04_2081_li19751007201910>`.         |
   +----------------------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | error                | Object | Specifies the error message returned when an error occurs. For details, see :ref:`Parameters in the error field <evs_04_3045__evs_04_2081_li0419202382514>`. |
   +----------------------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_3045__evs_04_2081_li19751007201910:

   Parameters in the **availabilityZoneInfo** field

   +-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                                                           |
   +===========+========+=======================================================================================================================================+
   | zoneState | Object | Specifies the status of the AZ. For details, see :ref:`Parameter in the zoneState field <evs_04_3045__evs_04_2081_li11149334112511>`. |
   +-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------+
   | zoneName  | String | Specifies the AZ name.                                                                                                                |
   +-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_3045__evs_04_2081_li11149334112511:

   Parameter in the **zoneState** field

   +-----------------------+-----------------------+----------------------------------------+
   | Parameter             | Type                  | Description                            |
   +=======================+=======================+========================================+
   | available             | Boolean               | Specifies whether the AZ is available. |
   |                       |                       |                                        |
   |                       |                       | -  **true**: available                 |
   |                       |                       | -  **false**: unavailable              |
   +-----------------------+-----------------------+----------------------------------------+

-  .. _evs_04_3045__evs_04_2081_li0419202382514:

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
