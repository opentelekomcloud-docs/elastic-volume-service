:original_name: evs_04_3070.html

.. _evs_04_3070:

Accepting a Disk Transfer
=========================

Function
--------

This API is used to accept a disk transfer through the transfer ID and authentication key.

Constraints
-----------

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

   POST /v3/{project_id}/os-volume-transfer/{transfer_id}/accept

-  Parameter description

   =========== ========= ===============================
   Parameter   Mandatory Description
   =========== ========= ===============================
   project_id  Yes       Specifies the project ID.
   transfer_id Yes       Specifies the disk transfer ID.
   =========== ========= ===============================

Request
-------

-  Parameter description

   +-----------+--------+-----------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Mandatory | Description                                                                                                                                       |
   +===========+========+===========+===================================================================================================================================================+
   | accept    | Object | Yes       | Specifies the disk transfer acceptance marker. For details, see :ref:`Parameter in the accept field <evs_04_3070__evs_04_2107_li55316081111336>`. |
   +-----------+--------+-----------+---------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_3070__evs_04_2107_li55316081111336:

   Parameter in the **accept** field

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------+
   | Parameter       | Type            | Mandatory       | Description                                                                  |
   +=================+=================+=================+==============================================================================+
   | auth_key        | String          | Yes             | Specifies the authentication key of the disk transfer.                       |
   |                 |                 |                 |                                                                              |
   |                 |                 |                 | Specifies the authentication key returned during the disk transfer creation. |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------+

-  Example request

   .. code-block::

      {
          "accept": {
              "auth_key": "9266c59563c84664"
          }
      }

Response
--------

-  Parameter description

   +-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                                                                    |
   +===========+========+================================================================================================================================================+
   | transfer  | Object | Specifies the disk transfer information. For details, see :ref:`Parameters in the transfer field <evs_04_3070__evs_04_2107_li12496189111714>`. |
   +-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_3070__evs_04_2107_li12496189111714:

   Parameters in the **transfer** field

   ========= ============ =========================================
   Parameter Type         Description
   ========= ============ =========================================
   volume_id String       Specifies the disk ID.
   id        String       Specifies the disk transfer ID.
   name      String       Specifies the name of the disk transfer.
   links     List< Dict > Specifies the links of the disk transfer.
   ========= ============ =========================================

-  Example response

   .. code-block::

      {
          "transfer": {
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
          }
      }

Status Codes
------------

-  Normal

   202

Error Codes
-----------

For details, see :ref:`Error Codes <evs_04_0038>`.
