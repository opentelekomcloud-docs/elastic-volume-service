:original_name: evs_04_2027.html

.. _evs_04_2027:

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

   POST /v2/{project_id}/os-vendor-volumes/{volume_id}/tags/action

-  Parameter description

   ========== ========= ===============
   Parameter  Mandatory Description
   ========== ========= ===============
   project_id Yes       The project ID.
   volume_id  Yes       The disk ID.
   ========== ========= ===============

Request
-------

-  Parameter description

   +-----------------+--------------------+-----------------+------------------------------------------------------------------------------------------------------------+
   | Parameter       | Type               | Mandatory       | Description                                                                                                |
   +=================+====================+=================+============================================================================================================+
   | tags            | List<resource_tag> | Yes             | The tag list. For details, see :ref:`Parameters in the resource_tag field <evs_04_2027__li4495404118563>`. |
   +-----------------+--------------------+-----------------+------------------------------------------------------------------------------------------------------------+
   | action          | String             | Yes             | The operation to perform. The value can be **create** or **delete**.                                       |
   |                 |                    |                 |                                                                                                            |
   |                 |                    |                 | **create**: specifies to add tags.                                                                         |
   +-----------------+--------------------+-----------------+------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_2027__li4495404118563:

   Parameters in the **resource_tag** field

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------+
   | Parameter       | Type            | Mandatory       | Description                                                            |
   +=================+=================+=================+========================================================================+
   | key             | String          | Yes             | The tag key.                                                           |
   |                 |                 |                 |                                                                        |
   |                 |                 |                 | -  Cannot be left blank.                                               |
   |                 |                 |                 | -  Must be unique for each resource.                                   |
   |                 |                 |                 | -  Can contain a maximum of 36 characters.                             |
   |                 |                 |                 | -  Can contain only digits, letters, hyphens (-), and underscores (_). |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------+
   | value           | String          | Yes             | The tag value.                                                         |
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
