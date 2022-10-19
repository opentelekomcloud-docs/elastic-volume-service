:original_name: evs_04_2068.html

.. _evs_04_2068:

Querying EVS Disks
==================

Function
--------

This API is used to query EVS disks.

URI
---

-  URI format

   GET /v2/{project_id}/volumes

-  Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   ========== ========= =========================

-  Request filter parameters

   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter         | Type            | Mandatory       | Description                                                                                                                                                                         |
   +===================+=================+=================+=====================================================================================================================================================================================+
   | marker            | String          | No              | Specifies the ID of the last record on the previous page. The returned value is the value of the item after this one.                                                               |
   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name              | String          | No              | Specifies the disk name. The value can contain a maximum of 255 bytes.                                                                                                              |
   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit             | Integer         | No              | Specifies the maximum number of query results that can be returned.                                                                                                                 |
   |                   |                 |                 |                                                                                                                                                                                     |
   |                   |                 |                 | The value ranges from 1 to 1000, and the default value is 1000. The returned value cannot exceed this limit.                                                                        |
   |                   |                 |                 |                                                                                                                                                                                     |
   |                   |                 |                 | If the tenant has more than 50 disks in total, you are advised to use this parameter and set its value to **50** to improve the query efficiency. Examples are provided as follows: |
   |                   |                 |                 |                                                                                                                                                                                     |
   |                   |                 |                 | **GET /v2/**\ *xxx*\ **/volumes?limit=50**: Queries the 1–50 disks. **GET /v2/**\ *xxx*\ **/volumes?offset=50&limit=50**: Queries the 51–100 disks.                                 |
   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sort_key          | String          | No              | Specifies the keyword based on which the returned results are sorted. The value can be **id**, **status**, **size**, or **created_at**, and the default value is **created_at**.    |
   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sort_dir          | String          | No              | Specifies the result sorting order. The default value is **desc**.                                                                                                                  |
   |                   |                 |                 |                                                                                                                                                                                     |
   |                   |                 |                 | -  **desc**: indicates the descending order.                                                                                                                                        |
   |                   |                 |                 | -  **asc**: indicates the ascending order.                                                                                                                                          |
   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | offset            | Integer         | No              | Specifies the offset.                                                                                                                                                               |
   |                   |                 |                 |                                                                                                                                                                                     |
   |                   |                 |                 | All disks after this offset will be queried. The value must be an integer greater than 0 but less than the number of disks.                                                         |
   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status            | String          | No              | Specifies the disk status. For details, see :ref:`EVS Disk Status <evs_04_0040>`.                                                                                                   |
   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | metadata          | String          | No              | Specifies the disk metadata.                                                                                                                                                        |
   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | availability_zone | String          | No              | Specifies the AZ.                                                                                                                                                                   |
   +-------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request
-------

The following example shows how to query the disks in the **available** state.

-  Example request

   .. code-block:: text

      GET https://{endpoint}/v2/{project_id}/volumes?status=available

Response
--------

-  Parameter description

   +---------------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter     | Type   | Description                                                                                                                                                                                                                              |
   +===============+========+==========================================================================================================================================================================================================================================+
   | volumes       | list   | Specifies the list of queried disks. For details, see :ref:`Parameters in the volumes field <evs_04_2068__li3451542201439>`.                                                                                                             |
   +---------------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | volumes_links | list   | Specifies the query position marker in the disk list. If only some disks are returned in this query, the URL of the last disk queried will be returned. You can use this URL to continue to query the remaining disks in the next query. |
   +---------------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | error         | Object | Specifies the error message returned when an error occurs. For details, see :ref:`Parameters in the error field <evs_04_2068__li0419202382514>`.                                                                                         |
   +---------------+--------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_2068__li3451542201439:

   Parameters in the **volumes** field

   +-----------+---------------------------+---------------------------------------------------------------------------------------------------------------+
   | Parameter | Type                      | Description                                                                                                   |
   +===========+===========================+===============================================================================================================+
   | id        | String                    | Specifies the disk ID.                                                                                        |
   +-----------+---------------------------+---------------------------------------------------------------------------------------------------------------+
   | links     | list<map<String, String>> | Specifies the disk URI. For details, see :ref:`Parameters in the links field <evs_04_2068__li1077125119136>`. |
   +-----------+---------------------------+---------------------------------------------------------------------------------------------------------------+
   | name      | String                    | Specifies the disk name. The value can contain a maximum of 255 bytes.                                        |
   +-----------+---------------------------+---------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_2068__li1077125119136:

   Parameters in the **links** field

   ========= ====== ==========================================
   Parameter Type   Description
   ========= ====== ==========================================
   href      String Specifies the corresponding shortcut link.
   rel       String Specifies the shortcut link marker name.
   ========= ====== ==========================================

-  .. _evs_04_2068__li0419202382514:

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
          "volumes": [
              {
                  "id": "6b604cef-9bd8-4f5a-ae56-45839e6e1f0a",
                  "links": [
                      {
                          "href": "https://volume.localdomain.com:8776/v2/dd14c6ac581f40059e27f5320b60bf2f/volumes/6b604cef-9bd8-4f5a-ae56-45839e6e1f0a",
                          "rel": "self"
                      },
                      {
                          "href": "https://volume.localdomain.com:8776/dd14c6ac581f40059e27f5320b60bf2f/volumes/6b604cef-9bd8-4f5a-ae56-45839e6e1f0a",
                          "rel": "bookmark"
                      }
                  ],
                  "name": "zjb_u25_test"
              },
              {
                  "id": "2bce4552-9a7d-48fa-8484-abbbf64b206e",
                  "links": [
                      {
                          "href": "https://volume.localdomain.com:8776/v2/dd14c6ac581f40059e27f5320b60bf2f/volumes/2bce4552-9a7d-48fa-8484-abbbf64b206e",
                          "rel": "self"
                      },
                      {
                          "href": "https://volume.localdomain.com:8776/dd14c6ac581f40059e27f5320b60bf2f/volumes/2bce4552-9a7d-48fa-8484-abbbf64b206e",
                          "rel": "bookmark"
                      }
                  ],
                  "name": "zjb_u25_test"
              },
              {
                  "id": "3f1b98ec-a8b5-4e92-a727-88def62d5ad3",
                  "links": [
                      {
                          "href": "https://volume.localdomain.com:8776/v2/dd14c6ac581f40059e27f5320b60bf2f/volumes/3f1b98ec-a8b5-4e92-a727-88def62d5ad3",
                          "rel": "self"
                      },
                      {
                          "href": "https://volume.localdomain.com:8776/dd14c6ac581f40059e27f5320b60bf2f/volumes/3f1b98ec-a8b5-4e92-a727-88def62d5ad3",
                          "rel": "bookmark"
                      }
                  ],
                  "name": "zjb_u25_test"
              }
          ],
          "volumes_links": [
              {
                  "href": "https://volume.localdomain.com:8776/v2/dd14c6ac581f40059e27f5320b60bf2f/volumes?limit=3&marker=3f1b98ec-a8b5-4e92-a727-88def62d5ad3",
                  "rel": "next"
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
