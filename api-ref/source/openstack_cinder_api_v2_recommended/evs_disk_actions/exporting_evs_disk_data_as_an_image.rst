:original_name: evs_04_2086.html

.. _evs_04_2086:

Exporting EVS Disk Data as an Image
===================================

Function
--------

This API is used to export the system disk data or data disk data as an IMS image. The exported image will be displayed in the IMS private image list and can be viewed and used.

Constraints
-----------

If the target disk is in the **in-use** state, stop the server where the disk has been attached before calling this API. If the target disk is a shared disk, stop all servers where the shared disk has been attached before calling this API.

URI
---

-  URI format

   POST /v2/{project_id}/volumes/{volume_id}/action

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

   +------------------------+--------+-----------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter              | Type   | Mandatory | Description                                                                                                                                                          |
   +========================+========+===========+======================================================================================================================================================================+
   | os-volume_upload_image | Object | Yes       | Specifies the operation to export the disk data as an image. For details, see :ref:`Parameters in the os-volume_upload_image field <evs_04_2086__li49734540111454>`. |
   +------------------------+--------+-----------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_2086__li49734540111454:

   Parameters in the **os-volume_upload_image** field

   +------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter        | Type            | Mandatory       | Description                                                                                                                                                                         |
   +==================+=================+=================+=====================================================================================================================================================================================+
   | disk_format      | String          | No              | Specifies the format of the exported image.                                                                                                                                         |
   |                  |                 |                 |                                                                                                                                                                                     |
   |                  |                 |                 | The value can be **vhd**, **zvhd**, **zvhd2**, **raw**, or **qcow2**. The default value is **zvhd2**.                                                                               |
   +------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | image_name       | String          | Yes             | Specifies the name of the exported image.                                                                                                                                           |
   |                  |                 |                 |                                                                                                                                                                                     |
   |                  |                 |                 | -  The name cannot start or end with space.                                                                                                                                         |
   |                  |                 |                 | -  The name contains 1 to 128 characters.                                                                                                                                           |
   |                  |                 |                 | -  The name contains the following characters: uppercase letters, lowercase letters, digits, and special characters, such as hyphens (-), periods (.), underscores (_), and spaces. |
   +------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | force            | Boolean         | No              | Specifies whether to forcibly export the image. The default value is **false**.                                                                                                     |
   |                  |                 |                 |                                                                                                                                                                                     |
   |                  |                 |                 | -  If **force** is set to **false** and the disk is in the **in-use** state, the image cannot be forcibly exported.                                                                 |
   |                  |                 |                 |                                                                                                                                                                                     |
   |                  |                 |                 | -  If **force** is set to **true** and the disk is in the **in-use** state, the image can be forcibly exported.                                                                     |
   +------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | container_format | String          | No              | Specifies the container type of the exported image.                                                                                                                                 |
   |                  |                 |                 |                                                                                                                                                                                     |
   |                  |                 |                 | The value can be **ami**, **ari**, **aki**, **ovf**, or **bare**. The default value is **bare**.                                                                                    |
   +------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | \__os_type       | String          | No              | Specifies the OS type of the exported image. Currently, only **windows** and **linux** are supported. The default value is **linux**.                                               |
   |                  |                 |                 |                                                                                                                                                                                     |
   |                  |                 |                 | .. note::                                                                                                                                                                           |
   |                  |                 |                 |                                                                                                                                                                                     |
   |                  |                 |                 |    -  There are two underscores (_) in front of **os** and one underscore (_) after **os**.                                                                                         |
   |                  |                 |                 |    -  This parameter setting takes effect only when the **\__os_type** field is not included in **volume_image_metadata** and the disk status is **available**.                     |
   |                  |                 |                 |    -  If this parameter is not specified, default value **linux** is used as the OS type of the image.                                                                              |
   +------------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   .. code-block::

      {
          "os-volume_upload_image": {
              "image_name": "sxmatch2",
              "force": true,
              "container_format": "bare",
              "disk_format": "vhd",
              "__os_type": "linux"
          }
      }

Response
--------

-  Parameter description

   +------------------------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter              | Type   | Description                                                                                                                                                         |
   +========================+========+=====================================================================================================================================================================+
   | os-volume_upload_image | Object | Specifies the operation to export the disk data as an image. For details, see :ref:`Parameters in the os-volume_upload_image field <evs_04_2086__li8542654111830>`. |
   +------------------------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | error                  | Object | Specifies the error message returned when an error occurs. For details, see :ref:`Parameters in the error field <evs_04_2086__li0419202382514>`.                    |
   +------------------------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_2086__li8542654111830:

   Parameters in the **os-volume_upload_image** field

   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                       |
   +=======================+=======================+===================================================================================================================================+
   | status                | String                | Specifies the disk status after the image is exported. The correct value is **uploading**.                                        |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------+
   | image_id              | String                | Specifies the ID of the exported image.                                                                                           |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------+
   | image_name            | String                | Specifies the name of the exported image.                                                                                         |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------+
   | volume_type           | Object                | Specifies the disk type information. For details, see :ref:`Parameters in the volume_type field <evs_04_2086__li28869709111957>`. |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------+
   | container_format      | String                | Specifies the container type of the exported image.                                                                               |
   |                       |                       |                                                                                                                                   |
   |                       |                       | The value can be **ami**, **ari**, **aki**, **ovf**, or **bare**. The default value is **bare**.                                  |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------+
   | size                  | Integer               | Specifies the disk size, in GB.                                                                                                   |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------+
   | disk_format           | String                | Specifies the format of the exported image.                                                                                       |
   |                       |                       |                                                                                                                                   |
   |                       |                       | The value can be **vhd**, **zvhd**, **zvhd2**, **raw**, or **qcow2**. The default value is **vhd**.                               |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------+
   | id                    | String                | Specifies the disk ID.                                                                                                            |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------+
   | display_description   | String                | Specifies the disk description.                                                                                                   |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------+
   | updated_at            | String                | Specifies the time when the disk was updated.                                                                                     |
   |                       |                       |                                                                                                                                   |
   |                       |                       | Time format: UTC YYYY-MM-DDTHH:MM:SS.XXXXXX                                                                                       |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_2086__li28869709111957:

   Parameters in the **volume_type** field

   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                           |
   +=======================+=======================+=======================================================================================================================================+
   | id                    | String                | Specifies the ID of the disk type.                                                                                                    |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------+
   | name                  | String                | Specifies the name of the disk type.                                                                                                  |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------+
   | deleted               | Boolean               | Specifies whether to delete the disk type.                                                                                            |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------+
   | is_public             | Boolean               | Reserved field                                                                                                                        |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------+
   | extra_spec            | Object                | Specifies the disk type specifications. For details, see :ref:`Parameters in the extra_specs field <evs_04_2086__li105361616191716>`. |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------+
   | description           | Integer               | Specifies the description of the disk type.                                                                                           |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------+
   | created_at            | String                | Specifies the time when the disk type was created.                                                                                    |
   |                       |                       |                                                                                                                                       |
   |                       |                       | Time format: UTC YYYY-MM-DDTHH:MM:SS.XXXXXX                                                                                           |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------+
   | updated_at            | String                | Specifies the time when the disk type was updated.                                                                                    |
   |                       |                       |                                                                                                                                       |
   |                       |                       | Time format: UTC YYYY-MM-DDTHH:MM:SS.XXXXXX                                                                                           |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------+
   | deleted_at            | String                | Specifies the time when the disk type was deleted.                                                                                    |
   |                       |                       |                                                                                                                                       |
   |                       |                       | Time format: UTC YYYY-MM-DDTHH:MM:SS.XXXXXX                                                                                           |
   +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_2086__li105361616191716:

   Parameters in the **extra_specs** field

   +---------------------------+--------+-------------------------------------------------------+
   | Parameter                 | Type   | Description                                           |
   +===========================+========+=======================================================+
   | volume_backend_name       | String | Reserved field                                        |
   +---------------------------+--------+-------------------------------------------------------+
   | availability-zone         | String | Reserved field                                        |
   +---------------------------+--------+-------------------------------------------------------+
   | HW:availability_zone      | String | Reserved field                                        |
   +---------------------------+--------+-------------------------------------------------------+
   | RESKEY:availability_zones | String | Specifies the AZs that support the current disk type. |
   +---------------------------+--------+-------------------------------------------------------+

-  .. _evs_04_2086__li0419202382514:

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
          "os-volume_upload_image": {
              "status": "uploading",
              "size": 40,
              "id": "16369c5d-384d-4e64-b37a-56d898769362",
              "image_id": "c5333daa-fbc8-4d1d-bf79-b0567bb45d15",
              "image_name": "evs-ims-test1027",
              "volume_type": {
                  "description": "None",
                  "deleted": false,
                  "created_at": "2015-05-24T14:47:22.132268",
                  "updated_at": "2017-07-29T11:29:33.730076",
                  "extra_specs": {
                      "volume_backend_name": "<or> iaas blockstorage_SATA <or> iaas blockstorage_SAS <or> iaas blockstoragesata",
                      "XX:availability_zone": "az-dc-1"
                  },
                  "is_public": true,
                  "deleted_at": null,
                  "id": "8247b6ed-37f0-4c48-8ef1-f0027fb332bc",
                  "name": "SATA"
              },
              "container_format": "bare",
              "disk_format": "vhd",
              "display_description": "",
              "updated_at": "2018-01-11T01:50:25.800931"
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

   In the preceding example, **error** indicates a general error, for example, **badRequest** or **itemNotFound**. An example is provided as follows:

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

   202

Error Codes
-----------

For details, see :ref:`Error Codes <evs_04_0038>`.
