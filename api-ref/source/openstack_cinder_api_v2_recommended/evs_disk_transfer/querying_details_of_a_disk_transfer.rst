:original_name: evs_04_2109.html

.. _evs_04_2109:

Querying Details of a Disk Transfer
===================================

Function
--------

This API is used to query the details of a disk transfer, including the transfer creation time, transfer ID, and transfer name.

URI
---

-  URI format

   GET /v2/{project_id}/os-volume-transfer/{transfer_id}

-  Parameter description

   =========== ========= ===============================
   Parameter   Mandatory Description
   =========== ========= ===============================
   project_id  Yes       Specifies the project ID.
   transfer_id Yes       Specifies the disk transfer ID.
   =========== ========= ===============================

Request
-------

-  Example request

   .. code-block:: text

      GET  https://{endpoint}/v2/{project_id}/os-volume-transfer/cac5c677-73a9-4288-bb9c-b2ebfb547377

Response
--------

-  Parameter description

   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                                                    |
   +===========+========+================================================================================================================================+
   | transfer  | Object | Specifies the disk transfer details. For details, see :ref:`Parameters in the transfer field <evs_04_2109__li61468331112723>`. |
   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_2109__li61468331112723:

   Parameters in the **transfer** field

   +-----------------------+-----------------------+--------------------------------------------------------+
   | Parameter             | Type                  | Description                                            |
   +=======================+=======================+========================================================+
   | links                 | List< Dict >          | Specifies the links of the disk transfer.              |
   +-----------------------+-----------------------+--------------------------------------------------------+
   | created_at            | String                | Specifies the time when the disk transfer was created. |
   |                       |                       |                                                        |
   |                       |                       | Time format: UTC YYYY-MM-DDTHH:MM:SS.XXXXXX            |
   +-----------------------+-----------------------+--------------------------------------------------------+
   | volume_id             | String                | Specifies the disk ID.                                 |
   +-----------------------+-----------------------+--------------------------------------------------------+
   | id                    | String                | Specifies the disk transfer ID.                        |
   +-----------------------+-----------------------+--------------------------------------------------------+
   | name                  | String                | Specifies the name of the disk transfer.               |
   +-----------------------+-----------------------+--------------------------------------------------------+

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
