:original_name: evs_04_3013.html

.. _evs_04_3013:

Batch Deleting Tags for the Specified EVS Disk
==============================================

Function
--------

This API is used to batch delete tags of a specified EVS disk.

Constraints
-----------

None

URI
---

-  URI format

   POST /v3/{project_id}/os-vendor-volumes/{volume_id}/tags/action

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

   +-----------------+--------------------+-----------------+------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Type               | Mandatory       | Description                                                                                                            |
   +=================+====================+=================+========================================================================================================================+
   | tags            | List<resource_tag> | Yes             | The tag list. For details, see :ref:`Parameters in the resource_tag field <evs_04_3013__evs_04_2029_li2051510427374>`. |
   +-----------------+--------------------+-----------------+------------------------------------------------------------------------------------------------------------------------+
   | action          | String             | Yes             | The operation to perform. The value can be **create** or **delete**.                                                   |
   |                 |                    |                 |                                                                                                                        |
   |                 |                    |                 | **delete**: deletes tags.                                                                                              |
   +-----------------+--------------------+-----------------+------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_3013__evs_04_2029_li2051510427374:

   Parameters in the **resource_tag** field

   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Type            | Mandatory       | Description                                                                                                                                                                             |
   +=================+=================+=================+=========================================================================================================================================================================================+
   | key             | String          | Yes             | The tag key.                                                                                                                                                                            |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | value           | String          | No              | The tag value.                                                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                                                         |
   |                 |                 |                 | -  It can contain up to 43 Unicode characters.                                                                                                                                          |
   |                 |                 |                 | -  It can be an empty string. The spaces before and after the character string are discarded.                                                                                           |
   |                 |                 |                 | -  It cannot contain the following characters:                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                                                         |
   |                 |                 |                 |    -  Non-printable ASCII characters (0-31)                                                                                                                                             |
   |                 |                 |                 |    -  Special characters, including asterisks (*), left angle brackets (<), right angle brackets (>), backslashes (\\), equal signs (=), commas (,), vertical bars (|), and slashes (/) |
   +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   .. code-block::

      {
          "action": "delete",
          "tags": [
              {
                  "key": "key1"
              },
              {
                  "key": "key2"
              }
          ]
      }

Response
--------

None

Status Codes
------------

-  Normal

   204

Error Codes
-----------

For details, see :ref:`Error Codes <evs_04_0038>`.
