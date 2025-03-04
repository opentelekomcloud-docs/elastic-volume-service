:original_name: evs_04_2108.html

.. _evs_04_2108:

Deleting a Disk Transfer
========================

Function
--------

This API is used to delete a disk transfer. A disk transfer can be deleted if it is not accepted. Accepted disk transfers cannot be deleted.

URI
---

-  URI format

   DELETE /v2/{project_id}/os-volume-transfer/{transfer_id}

-  Parameter description

   =========== ========= ================
   Parameter   Mandatory Description
   =========== ========= ================
   project_id  Yes       The project ID.
   transfer_id Yes       The transfer ID.
   =========== ========= ================

Request
-------

-  Example request

   .. code-block:: text

      DELETE https://{endpoint}/v2/{project_id}/os-volume-transfer/cac5c677-73a9-4288-bb9c-b2ebfb547377

Response
--------

None

Status Codes
------------

-  Normal

   202

Error Codes
-----------

For details, see :ref:`Error Codes <evs_04_0038>`.
