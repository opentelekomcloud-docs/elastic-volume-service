:original_name: evs_04_3043.html

.. _evs_04_3043:

Deleting One Piece of Metadata for an EVS Disk
==============================================

Function
--------

This API is used to delete one piece of the EVS disk metadata.

URI
---

-  URI format

   DELETE /v3/{project_id}/volumes/{volume_id}/metadata/{key}

-  Parameter description

   +------------+-----------+-----------------------------------------------------------+
   | Parameter  | Mandatory | Description                                               |
   +============+===========+===========================================================+
   | project_id | Yes       | Specifies the project ID.                                 |
   +------------+-----------+-----------------------------------------------------------+
   | volume_id  | Yes       | Specifies the disk ID.                                    |
   +------------+-----------+-----------------------------------------------------------+
   | key        | Yes       | Specifies the key of the piece of metadata to be deleted. |
   +------------+-----------+-----------------------------------------------------------+

Request
-------

-  Example request

   .. code-block:: text

      DELETE https://{endpoint}/v3/{project_id}/volumes/b104b8db-170d-441b-897a-3c8ba9c5a214/metadata/value1

Response
--------

-  Parameter description

   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                                                                                  |
   +===========+========+==============================================================================================================================================================+
   | error     | Object | Specifies the error message returned when an error occurs. For details, see :ref:`Parameters in the error field <evs_04_3043__evs_04_2079_li0419202382514>`. |
   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_3043__evs_04_2079_li0419202382514:

   Parameters in the **error** field

   +-----------------------+-----------------------+-------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                             |
   +=======================+=======================+=========================================================================+
   | message               | String                | The error message returned if an error occurs.                          |
   +-----------------------+-----------------------+-------------------------------------------------------------------------+
   | code                  | String                | The error code returned if an error occurs.                             |
   |                       |                       |                                                                         |
   |                       |                       | For details about the error code, see :ref:`Error Codes <evs_04_0038>`. |
   +-----------------------+-----------------------+-------------------------------------------------------------------------+

-  Example response

   None

   or

   .. code-block::

      {
          "error": {
              "message": "XXXX",
              "code": "XXX"
          }
      }

   In the preceding example, **error** indicates a general error, for example, **badrequest** or **itemNotFound**. An example is provided as follows:

   .. code-block::

      {
          "itemNotFound": {
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
