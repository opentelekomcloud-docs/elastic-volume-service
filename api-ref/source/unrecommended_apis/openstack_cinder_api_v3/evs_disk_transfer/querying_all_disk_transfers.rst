:original_name: evs_04_3073.html

.. _evs_04_3073:

Querying All Disk Transfers
===========================

Function
--------

This API is used to query all disk transfers of the current tenant.

URI
---

-  URI format

   GET /v3/{project_id}/os-volume-transfer

-  Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   ========== ========= =========================

-  Request filter parameters

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Type            | Mandatory       | Description                                                                                                                                                         |
   +=================+=================+=================+=====================================================================================================================================================================+
   | limit           | Integer         | No              | Specifies the maximum number of query results that can be returned.                                                                                                 |
   |                 |                 |                 |                                                                                                                                                                     |
   |                 |                 |                 | The value ranges from 1 to 1000, and the default value is 1000. The returned value cannot exceed this limit.                                                        |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | offset          | Integer         | No              | Specifies the offset. All disk transfers after this offset will be queried. The value must be an integer greater than 0 but less than the number of disk transfers. |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request
-------

The following example shows how to query details of the disk transfers whose limit is no more than 50.

-  Example request

   .. code-block:: text

      GET https://{endpoint}/v3/{project_id}/os-volume-transfer?limit=50

Response
--------

-  Parameter description

   +-----------+----------------+-------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type           | Description                                                                                                                         |
   +===========+================+=====================================================================================================================================+
   | transfers | List<Transfer> | Specifies the disk transfers. For details, see :ref:`Parameters in the transfers field <evs_04_3073__evs_04_2110_li6113282511345>`. |
   +-----------+----------------+-------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_3073__evs_04_2110_li6113282511345:

   Parameters in the **transfers** field

   ========= ============ =========================================
   Parameter Type         Description
   ========= ============ =========================================
   links     List< Dict > Specifies the links of the disk transfer.
   volume_id String       Specifies the disk ID.
   id        String       Specifies the disk transfer ID.
   name      String       Specifies the name of the disk transfer.
   ========= ============ =========================================

-  Example response

   .. code-block::

      {
          "transfers": [
              {
                  "id": "cac5c677-73a9-4288-bb9c-b2ebfb547377",
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
              },
              {
                  "id": "f26c0dee-d20d-4e80-8dee-a8d91b9742a1",
                  "name": "second volume transfer",
                  "volume_id": "673db275-379f-41af-8371-e1652132b4c1",
                  "links": [
                      {
                          "href": "https://localhost/v2/firstproject/os-volume-transfer/2",
                          "rel": "self"
                      },
                      {
                          "href": "https://localhost/firstproject/os-volume-transfer/2",
                          "rel": "bookmark"
                      }
                  ]
              }
          ]
      }

Status Codes
------------

-  Normal

   200

Error Codes
-----------

For details, see :ref:`Error Codes <evs_04_0038>`.
