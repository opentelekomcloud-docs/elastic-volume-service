:original_name: evs_04_2106.html

.. _evs_04_2106:

Creating a Disk Transfer
========================

Function
--------

This API is used to create a disk transfer. After the transfer has been created, a transfer ID and an authentication key are returned.

After a disk transfer is created, the disk status changes from **available** to **awaiting-transfer**. Once the disk transfer is accepted, the disk status changes to **available** again.

Constraints
-----------

A disk transfer can be created only when the disk status is **available**. The detailed constraints are as follows:

-  Encrypted EVS disks cannot be transferred.
-  EVS disks with backups and snapshots available cannot be transferred.
-  EVS disks associated with backup policies cannot be transferred.
-  EVS disks used as system disks cannot be transferred.
-  EVS disks in EVS replication pairs cannot be transferred.

.. note::

   If the disk transfer is created using one of the unsupported disks, error code 400 will be returned.

URI
---

-  URI format

   POST /v2/{project_id}/os-volume-transfer

-  Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   ========== ========= =========================

Request
-------

-  Parameter description

   +-----------+--------+-----------+-------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Mandatory | Description                                                                                                                   |
   +===========+========+===========+===============================================================================================================================+
   | transfer  | Object | Yes       | Specifies the disk transfer marker. For details, see :ref:`Parameters in the transfer field <evs_04_2106__li55316081111336>`. |
   +-----------+--------+-----------+-------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_2106__li55316081111336:

   Parameters in the **transfer** field

   +-----------+--------+-----------+---------------------------------------------------------------------------------+
   | Parameter | Type   | Mandatory | Description                                                                     |
   +===========+========+===========+=================================================================================+
   | volume_id | String | Yes       | Specifies the disk ID.                                                          |
   +-----------+--------+-----------+---------------------------------------------------------------------------------+
   | name      | String | No        | Specifies the disk transfer name. The value can contain a maximum of 255 bytes. |
   +-----------+--------+-----------+---------------------------------------------------------------------------------+

-  Example request

   .. code-block::

      {
          "transfer": {
              "volume_id": "c86b9af4-151d-4ead-b62c-5fb967af0e37",
              "name": "first volume"
          }
      }

Response
--------

-  Parameter description

   +-----------+--------+------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                                                        |
   +===========+========+====================================================================================================================================+
   | transfer  | Object | Specifies the disk transfer information. For details, see :ref:`Parameters in the transfer field <evs_04_2106__li32419762111447>`. |
   +-----------+--------+------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_2106__li32419762111447:

   Parameters in the **transfer** field

   +-----------------------+-----------------------+--------------------------------------------------------+
   | Parameter             | Type                  | Description                                            |
   +=======================+=======================+========================================================+
   | auth_key              | String                | Specifies the authentication key of the disk transfer. |
   +-----------------------+-----------------------+--------------------------------------------------------+
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
              "id": "1a7059f5-8ed7-45b7-8d05-2811e5d09f24",
              "created_at": "2015-02-25T03:56:53.081642",
              "name": "first volume",
              "volume_id": "c86b9af4-151d-4ead-b62c-5fb967af0e37",
              "auth_key": "9266c59563c84664",
              "links": [
                  {
                      "href": "https://localhost/v2/firstproject/os-volume-transfer/3",
                      "rel": "self"
                  },
                  {
                      "href": "https://localhost/firstproject/os-volume-transfer/3",
                      "rel": "bookmark"
                  }
              ]
          }
      }

Status Codes
------------

-  Normal

   202

Error Codes
-----------

For details, see :ref:`Error Codes <evs_04_0038>`.
