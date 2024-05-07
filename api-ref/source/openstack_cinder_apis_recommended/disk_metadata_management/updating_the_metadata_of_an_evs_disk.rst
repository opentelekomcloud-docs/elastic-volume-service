:original_name: evs_04_2076.html

.. _evs_04_2076:

Updating the Metadata of an EVS Disk
====================================

Function
--------

This API is used to update the metadata of an EVS disk.

URI
---

-  URI format

   PUT /v2/{project_id}/volumes/{volume_id}/metadata

-  Parameter description

   ========== ========= ===============
   Parameter  Mandatory Description
   ========== ========= ===============
   project_id Yes       The project ID.
   volume_id  Yes       The disk ID.
   ========== ========= ===============

Request
-------

-  Request parameters

   +-----------------+--------------------+-----------------+----------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Type               | Mandatory       | Description                                                                                                          |
   +=================+====================+=================+======================================================================================================================+
   | metadata        | Map<String,String> | Yes             | The metadata to be updated. For details, see :ref:`Parameter in the metadata field <evs_04_2076__li54973602211845>`. |
   |                 |                    |                 |                                                                                                                      |
   |                 |                    |                 | The length of **key** and **value** under **metadata** can contain no more than 255 bytes.                           |
   +-----------------+--------------------+-----------------+----------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_2076__li54973602211845:

   Parameter in the **metadata** field

   +-----------+--------+-----------+--------------------------------------------------------------------------------+
   | Parameter | Type   | Mandatory | Description                                                                    |
   +===========+========+===========+================================================================================+
   | key_val   | String | No        | The metadata information, which is made up of one or multiple key-value pairs. |
   +-----------+--------+-----------+--------------------------------------------------------------------------------+

-  Example request

   .. code-block::

      {
          "metadata": {
              "key1": "value1",
              "key2": "value2"
          }
      }

Response
--------

-  Response parameters

   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type   | Description                                                                                                                          |
   +===========+========+======================================================================================================================================+
   | metadata  | Object | The disk metadata, which is made up of key-value pairs.                                                                              |
   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------+
   | error     | Object | The error message returned if an error occurs. For details, see :ref:`Parameters in the error field <evs_04_2076__li0419202382514>`. |
   +-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_2076__li0419202382514:

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

   .. code-block::

      {
          "metadata": {
              "key1": "value1",
              "key2": "value2"
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

   In the preceding example, **error** indicates a general error, for example, **badrequest** or **itemNotFound**. An example is provided as follows:

   .. code-block::

      {
          "badrequest": {
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
