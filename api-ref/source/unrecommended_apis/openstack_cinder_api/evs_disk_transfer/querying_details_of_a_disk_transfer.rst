:original_name: evs_04_3072.html

.. _evs_04_3072:

Querying Details of a Disk Transfer
===================================

Function
--------

This API is used to query the details of a disk transfer, including the transfer creation time, transfer ID, and transfer name.

URI
---

-  URI format

   GET /v3/{project_id}/os-volume-transfer/{transfer_id}

-  Parameter description

   =========== ========= ================
   Parameter   Mandatory Description
   =========== ========= ================
   project_id  Yes       The project ID.
   transfer_id Yes       The transfer ID.
   =========== ========= ================

Request
-------

-  Example request

   .. code-block:: text

      GET  https://{endpoint}/v3/{project_id}/os-volume-transfer/cac5c677-73a9-4288-bb9c-b2ebfb547377

Response
--------

-  Response parameters

   +-----------+--------+-----------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                                                 |
   +===========+========+=============================================================================================================================+
   | transfer  | Object | The transfer details. For details, see :ref:`Parameters in the transfer field <evs_04_3072__evs_04_2109_li61468331112723>`. |
   +-----------+--------+-----------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_3072__evs_04_2109_li61468331112723:

   Parameters in the **transfer** field

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                      |
   +=======================+=======================+==================================================================================================================+
   | links                 | Array of Objects      | The links of the transfer. See :ref:`Parameters in the links field <evs_04_3072__evs_04_2109_li14760102134419>`. |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------+
   | created_at            | String                | The time when the transfer was created.                                                                          |
   |                       |                       |                                                                                                                  |
   |                       |                       | Time format: UTC YYYY-MM-DDTHH:MM:SS.XXXXXX                                                                      |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------+
   | volume_id             | String                | The disk ID.                                                                                                     |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------+
   | id                    | String                | The transfer ID.                                                                                                 |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------+
   | name                  | String                | The transfer name.                                                                                               |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_3072__evs_04_2109_li14760102134419:

   Parameters in the **links** field

   +-----------------------+-----------------------+----------------------------------+
   | Parameter             | Type                  | Description                      |
   +=======================+=======================+==================================+
   | href                  | String                | The corresponding shortcut link. |
   +-----------------------+-----------------------+----------------------------------+
   | rel                   | String                | The shortcut link marker name.   |
   |                       |                       |                                  |
   |                       |                       | The default value is **next**.   |
   +-----------------------+-----------------------+----------------------------------+

-  Example response

   .. code-block::

      {
          "transfer": {
              "id": "cac5c677-73a9-4288-bb9c-b2ebfb547377",
              "created_at": "2015-02-25T03:56:53.081642",
              "name": "first volume transfer",
              "volume_id": "894623a6-e901-4312-aa06-4275e6321cce",
              "links": [
                  {
                      "href": "https://localhost/v2/firstproject/os-volume-transfer/1",
                      "rel": "self"
                  },
                  {
                      "href": "https://localhost/firstproject/os-volume-transfer/1",
                      "rel": "bookmark"
                  }
              ]
          }
      }

Status Codes
------------

-  Normal

   200

Error Codes
-----------

For details, see :ref:`Error Codes <evs_04_0038>`.
