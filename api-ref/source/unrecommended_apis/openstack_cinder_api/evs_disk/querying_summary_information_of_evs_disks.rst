:original_name: evs_04_3046.html

.. _evs_04_3046:

Querying Summary Information of EVS Disks
=========================================

Function
--------

This API is used to query the summary information of EVS disks, including the disk quantity, total capacity, and metadata information.

.. note::

   The request version must be 3.12 or later.

URI
---

-  URI format

   GET /v3/{project_id}/volumes/summary

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

      GET https://{endpoint}/v3/{project_id}/volumes/summary

Response
--------

-  Parameter description

   +----------------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter      | Type   | Description                                                                                                                                         |
   +================+========+=====================================================================================================================================================+
   | volume-summary | Object | Specifies the summary information of queried disks. For details, see :ref:`Parameters in the volume-summary field <evs_04_3046__li10504143155718>`. |
   +----------------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_3046__li10504143155718:

   Parameters in the **volume-summary** field

   +-------------+---------+-----------------------------------------------------------------------------------------------------------------+
   | Parameter   | Type    | Description                                                                                                     |
   +=============+=========+=================================================================================================================+
   | total_size  | Integer | Specifies the total size of disks, in GB.                                                                       |
   +-------------+---------+-----------------------------------------------------------------------------------------------------------------+
   | total_count | Integer | Specifies the total quantity of disks.                                                                          |
   +-------------+---------+-----------------------------------------------------------------------------------------------------------------+
   | metadata    | Object  | Specifies the disk metadata information. This parameter is supported when the request version is 3.36 or later. |
   +-------------+---------+-----------------------------------------------------------------------------------------------------------------+

-  Example response

   .. code-block::

      {
          "volume-summary": {
              "total_size": 83,
              "total_count": 8,
              "metadata": {}
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

   200

Error Codes
-----------

For details, see :ref:`Error Codes <evs_04_0038>`.
