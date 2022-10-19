:original_name: evs_04_2012.html

.. _evs_04_2012:

Querying EVS Disks (Deprecated)
===============================

Function
--------

This API is used to query EVS disks and display the query results in a list.

.. important::

   This API has been deprecated. Use another API. For details, see :ref:`Querying EVS Disks <evs_04_2068>`.

URI
---

-  URI format

   GET /v2/{project_id}/cloudvolumes

-  Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   ========== ========= =========================

-  Request filter parameters

   +-------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter         | Type            | Mandatory       | Description                                                                                                                                                                      |
   +===================+=================+=================+==================================================================================================================================================================================+
   | marker            | String          | No              | Specifies the ID of the last record on the previous page. The returned value is the value of the item after this one.                                                            |
   +-------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name              | String          | No              | Specifies the disk name. The value can contain a maximum of 255 bytes.                                                                                                           |
   +-------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status            | String          | No              | Specifies the disk status. For details, see :ref:`EVS Disk Status <evs_04_0040>`.                                                                                                |
   +-------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit             | Integer         | No              | Specifies the maximum number of query results that can be returned.                                                                                                              |
   |                   |                 |                 |                                                                                                                                                                                  |
   |                   |                 |                 | The value ranges from 1 to 1000, and the default value is 1000. The returned value cannot exceed this limit.                                                                     |
   +-------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | availability_zone | String          | No              | Specifies the AZ.                                                                                                                                                                |
   +-------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sort_key          | String          | No              | Specifies the keyword based on which the returned results are sorted. The value can be **id**, **status**, **size**, or **created_at**, and the default value is **created_at**. |
   +-------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sort_dir          | String          | No              | Specifies the result sorting order. The default value is **desc**.                                                                                                               |
   |                   |                 |                 |                                                                                                                                                                                  |
   |                   |                 |                 | -  **desc**: indicates the descending order.                                                                                                                                     |
   |                   |                 |                 | -  **asc**: indicates the ascending order.                                                                                                                                       |
   +-------------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request
-------

The following example shows how to query the disks in the **available** state.

-  Example request

   .. code-block:: text

      GET https://{endpoint}/v2/{project_id}/cloudvolumes?status=available

Response
--------

-  Parameter description

   +-----------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type             | Description                                                                                                                                      |
   +===========+==================+==================================================================================================================================================+
   | volumes   | Array of objects | Specifies the list of queried disks. For details, see :ref:`Parameters in the volumes field <evs_04_2012__li53362106201054>`.                    |
   +-----------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | error     | Object           | Specifies the error message returned when an error occurs. For details, see :ref:`Parameters in the error field <evs_04_2012__li0419202382514>`. |
   +-----------+------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_2012__li53362106201054:

   Parameters in the **volumes** field

   +-----------+------------------+---------------------------------------------------------------------------------------------------------------+
   | Parameter | Type             | Description                                                                                                   |
   +===========+==================+===============================================================================================================+
   | id        | String           | Specifies the disk ID.                                                                                        |
   +-----------+------------------+---------------------------------------------------------------------------------------------------------------+
   | links     | Array of objects | Specifies the disk URI. For details, see :ref:`Parameters in the links field <evs_04_2012__li1284243594910>`. |
   +-----------+------------------+---------------------------------------------------------------------------------------------------------------+
   | name      | String           | Specifies the disk name. The value can contain a maximum of 255 bytes.                                        |
   +-----------+------------------+---------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_2012__li1284243594910:

   Parameters in the **links** field

   ========= ====== ==========================================
   Parameter Type   Description
   ========= ====== ==========================================
   href      String Specifies the corresponding shortcut link.
   rel       String Specifies the shortcut link marker name.
   ========= ====== ==========================================

-  .. _evs_04_2012__li0419202382514:

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
                  "id": "e6cf4401-15f6-44bd-ae2b-cff4dc9523e6",
                  "links": [
                      {
                          "href": "https://volume.az0.dc1.domainname.com/v2/cd631140887d4b6e9c786b67a6dd4c02/volumes/e6cf4401-15f6-44bd-ae2b-cff4dc9523e6",
                          "rel": "self"
                      },
                      {
                          "href": "https://volume.az0.dc1.domainname.com/cd631140887d4b6e9c786b67a6dd4c02/volumes/e6cf4401-15f6-44bd-ae2b-cff4dc9523e6",
                          "rel": "bookmark"
                      }
                  ],
                  "name": "hallo5"
              },
              {
                  "id": "4c5e8203-f70e-4717-90cd-4a8f636888d1",
                  "links": [
                      {
                          "href": "https://volume.az0.dc1.domainname.com/v2/cd631140887d4b6e9c786b67a6dd4c02/volumes/4c5e8203-f70e-4717-90cd-4a8f636888d1",
                          "rel": "self"
                      },
                      {
                          "href": "https://volume.az0.dc1.domainname.com/cd631140887d4b6e9c786b67a6dd4c02/volumes/4c5e8203-f70e-4717-90cd-4a8f636888d1",
                          "rel": "bookmark"
                      }
                  ],
                  "name": "hallo4"
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
