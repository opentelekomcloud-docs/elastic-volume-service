:original_name: evs_04_3011.html

.. _evs_04_3011:

Batch Adding Tags for the Specified EVS Disk
============================================

Function
--------

This API is used to batch add tags for the specified EVS disk.

-  When adding tags, if a tag key is consistent with an existing one, the new tag will overwrite the existing tag.
-  A maximum of 10 tags can be created for a disk.

Constraints
-----------

None

URI
---

-  URI format

   POST /v3/{project_id}/os-vendor-volumes/{volume_id}/tags/action

-  Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   volume_id  Yes       Specifies the disk ID.
   ========== ========= =========================

Request
-------

-  Parameter description

   +-----------------+------------------+-----------------+-------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Type             | Mandatory       | Description                                                                                                             |
   +=================+==================+=================+=========================================================================================================================+
   | tags            | Array of objects | Yes             | Specifies the tag list. For details, see :ref:`Parameters in the tag field <evs_04_3011__evs_04_2027_li4495404118563>`. |
   +-----------------+------------------+-----------------+-------------------------------------------------------------------------------------------------------------------------+
   | action          | String           | Yes             | Specifies the operation to perform. The value can be **create** or **delete**.                                          |
   |                 |                  |                 |                                                                                                                         |
   |                 |                  |                 | **create**: specifies to add tags.                                                                                      |
   +-----------------+------------------+-----------------+-------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_3011__evs_04_2027_li4495404118563:

   Parameters in the **tag** field

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------+
   | Parameter       | Type            | Mandatory       | Description                                                            |
   +=================+=================+=================+========================================================================+
   | key             | String          | Yes             | Specifies the tag key.                                                 |
   |                 |                 |                 |                                                                        |
   |                 |                 |                 | -  Cannot be left blank.                                               |
   |                 |                 |                 | -  Must be unique for each resource.                                   |
   |                 |                 |                 | -  Can contain a maximum of 36 characters.                             |
   |                 |                 |                 | -  Can contain only digits, letters, hyphens (-), and underscores (_). |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------+
   | value           | String          | Yes             | Specifies the tag value.                                               |
   |                 |                 |                 |                                                                        |
   |                 |                 |                 | -  Can contain a maximum of 43 characters.                             |
   |                 |                 |                 | -  Can contain only digits, letters, hyphens (-), and underscores (_). |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------+

-  Example request

   .. code-block::

      {
          "action": "create",
          "tags": [
              {
                  "key": "key1",
                  "value": "value1"
              },
              {
                  "key": "key2",
                  "value": "value3"
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
