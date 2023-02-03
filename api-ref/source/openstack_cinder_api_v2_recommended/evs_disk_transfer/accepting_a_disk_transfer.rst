:original_name: evs_04_2107.html

.. _evs_04_2107:

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

   POST /v2/{project_id}/os-volume-transfer/{transfer_id}/accept

-  Parameter description

   =========== ========= ================
   Parameter   Mandatory Description
   =========== ========= ================
   project_id  Yes       The project ID.
   transfer_id Yes       The transfer ID.
   =========== ========= ================

Request
-------

-  Request parameters

   +-----------+--------+-----------+------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Mandatory | Description                                                                                                            |
   +===========+========+===========+========================================================================================================================+
   | accept    | Object | Yes       | The transfer acceptance marker. For details, see :ref:`Parameter in the accept field <evs_04_2107__li55316081111336>`. |
   +-----------+--------+-----------+------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_2107__li55316081111336:

   Parameter in the **accept** field

   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------+
   | Parameter       | Type            | Mandatory       | Description                                                             |
   +=================+=================+=================+=========================================================================+
   | auth_key        | String          | Yes             | The authentication key of the transfer.                                 |
   |                 |                 |                 |                                                                         |
   |                 |                 |                 | An authentication key will be returned when a disk transfer is created. |
   +-----------------+-----------------+-----------------+-------------------------------------------------------------------------+

-  Example request

   .. code-block::

      {
          "accept": {
              "auth_key": "9266c59563c84664"
          }
      }

Response
--------

-  Response parameters

   +-----------+--------+---------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                                         |
   +===========+========+=====================================================================================================================+
   | transfer  | Object | The transfer information. For details, see :ref:`Parameters in the transfer field <evs_04_2107__li12496189111714>`. |
   +-----------+--------+---------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_2107__li12496189111714:

   Parameters in the **transfer** field

   +-----------+------------------+-------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type             | Description                                                                                                       |
   +===========+==================+===================================================================================================================+
   | volume_id | String           | The disk ID.                                                                                                      |
   +-----------+------------------+-------------------------------------------------------------------------------------------------------------------+
   | id        | String           | The transfer ID.                                                                                                  |
   +-----------+------------------+-------------------------------------------------------------------------------------------------------------------+
   | name      | String           | The transfer name.                                                                                                |
   +-----------+------------------+-------------------------------------------------------------------------------------------------------------------+
   | links     | Array of Objects | The links of the transfer. For details, see :ref:`Parameters in the links field <evs_04_2107__li12225016174715>`. |
   +-----------+------------------+-------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_2107__li12225016174715:

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
