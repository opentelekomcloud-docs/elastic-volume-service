:original_name: evs_04_3051.html

.. _evs_04_3051:

Exporting EVS Disk Data as an Image
===================================

Function
--------

This API is used to export the system disk data or data disk data as an IMS image. The exported image will be displayed in the IMS private image list and can be viewed and used.

URI
---

-  URI format

   POST /v3/{project_id}/volumes/{volume_id}/action

-  Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   volume_id  Yes       Specifies the disk ID.
   ========== ========= =========================

Request
-------

-  Request parameters

   +------------------------+--------+-----------+--------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter              | Type   | Mandatory | Description                                                                                                                                            |
   +========================+========+===========+========================================================================================================================================================+
   | os-volume_upload_image | Object | Yes       | The image export operation marker. For details, see :ref:`Parameters in the os-volume_upload_image field <evs_04_3051__evs_04_2086_li49734540111454>`. |
   +------------------------+--------+-----------+--------------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_3051__evs_04_2086_li49734540111454:

   Parameters in the **os-volume_upload_image** field

   +------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter        | Type            | Mandatory       | Description                                                                                                                                                     |
   +==================+=================+=================+=================================================================================================================================================================+
   | disk_format      | String          | No              | The format of the image to be exported.                                                                                                                         |
   |                  |                 |                 |                                                                                                                                                                 |
   |                  |                 |                 | The value can be **vhd**, **zvhd**, **zvhd2**, **raw**, or **qcow2**. The default value is **zvhd2**.                                                           |
   +------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | image_name       | String          | Yes             | The name of the image to be exported.                                                                                                                           |
   |                  |                 |                 |                                                                                                                                                                 |
   |                  |                 |                 | -  It cannot start or end with space.                                                                                                                           |
   |                  |                 |                 | -  It can contain 1 to 128 characters.                                                                                                                          |
   |                  |                 |                 | -  It can contain the following characters: letters, digits, special characters including hyphens (-), periods (.), and underscores (_), and spaces.            |
   +------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | force            | Boolean         | No              | Whether to forcibly export the image. The default value is **false**.                                                                                           |
   |                  |                 |                 |                                                                                                                                                                 |
   |                  |                 |                 | -  If this parameter is set to **false**, images cannot be forcibly exported when the disk status is **in-use**.                                                |
   |                  |                 |                 |                                                                                                                                                                 |
   |                  |                 |                 | -  If this parameter is set to **true**, images can be forcibly exported even when the disk status is **in-use**.                                               |
   +------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | container_format | String          | No              | The container type of the image to be exported.                                                                                                                 |
   |                  |                 |                 |                                                                                                                                                                 |
   |                  |                 |                 | The value can be **ami**, **ari**, **aki**, **ovf**, or **bare**. The default value is **bare**.                                                                |
   +------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | \__os_type       | String          | No              | The OS type of the image to be exported. Only **windows** and **linux** are supported currently. The default value is **linux**.                                |
   |                  |                 |                 |                                                                                                                                                                 |
   |                  |                 |                 | .. note::                                                                                                                                                       |
   |                  |                 |                 |                                                                                                                                                                 |
   |                  |                 |                 |    -  There are two underscores (_) in front of **os** and one underscore (_) after **os**.                                                                     |
   |                  |                 |                 |    -  This parameter setting takes effect only when the **\__os_type** field is not included in **volume_image_metadata** and the disk status is **available**. |
   |                  |                 |                 |    -  If this parameter is not specified, default value **linux** is used.                                                                                      |
   +------------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

-  Response parameters

   +------------------------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter              | Type   | Description                                                                                                                                           |
   +========================+========+=======================================================================================================================================================+
   | os-volume_upload_image | Object | The image export operation marker. For details, see :ref:`Parameters in the os-volume_upload_image field <evs_04_3051__evs_04_2086_li8542654111830>`. |
   +------------------------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------+
   | error                  | Object | The error message returned if an error occurs. For details, see :ref:`Parameters in the error field <evs_04_3051__evs_04_2086_li0419202382514>`.      |
   +------------------------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_3051__evs_04_2086_li8542654111830:

   Parameters in the **os-volume_upload_image** field

   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                         |
   +=======================+=======================+=====================================================================================================================================+
   | status                | String                | The disk status after the image is exported. The correct value is **uploading**.                                                    |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------+
   | image_id              | String                | The ID of the exported image.                                                                                                       |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------+
   | image_name            | String                | The name of the exported image.                                                                                                     |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------+
   | volume_type           | Object                | The disk type information. For details, see :ref:`Parameters in the volume_type field <evs_04_3051__evs_04_2086_li28869709111957>`. |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------+
   | container_format      | String                | The container type of the exported image.                                                                                           |
   |                       |                       |                                                                                                                                     |
   |                       |                       | The value can be **ami**, **ari**, **aki**, **ovf**, or **bare**. The default value is **bare**.                                    |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------+
   | size                  | Integer               | The disk size, in GB.                                                                                                               |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------+
   | disk_format           | String                | The format of the exported image.                                                                                                   |
   |                       |                       |                                                                                                                                     |
   |                       |                       | The value can be **vhd**, **zvhd**, **zvhd2**, **raw**, or **qcow2**. The default value is **vhd**.                                 |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------+
   | id                    | String                | The disk ID.                                                                                                                        |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------+
   | display_description   | String                | The disk description.                                                                                                               |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------+
   | updated_at            | String                | The time when the disk was updated.                                                                                                 |
   |                       |                       |                                                                                                                                     |
   |                       |                       | Time format: UTC YYYY-MM-DDTHH:MM:SS.XXXXXX                                                                                         |
   +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_3051__evs_04_2086_li28869709111957:

   Parameters in the **volume_type** field

   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                             |
   +=======================+=======================+=========================================================================================================================================+
   | id                    | String                | The disk type ID.                                                                                                                       |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | name                  | String                | The disk type name.                                                                                                                     |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | deleted               | Boolean               | Whether the disk has been deleted.                                                                                                      |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | is_public             | Boolean               | The reserved field.                                                                                                                     |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | extra_spec            | Object                | The disk type specifications. For details, see :ref:`Parameters in the extra_specs field <evs_04_3051__evs_04_2086_li105361616191716>`. |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | description           | Integer               | The disk type description.                                                                                                              |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | created_at            | String                | The time when the disk type was created.                                                                                                |
   |                       |                       |                                                                                                                                         |
   |                       |                       | Time format: UTC YYYY-MM-DDTHH:MM:SS.XXXXXX                                                                                             |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | updated_at            | String                | The time when the disk type was updated.                                                                                                |
   |                       |                       |                                                                                                                                         |
   |                       |                       | Time format: UTC YYYY-MM-DDTHH:MM:SS.XXXXXX                                                                                             |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------+
   | deleted_at            | String                | The time when the disk type was deleted.                                                                                                |
   |                       |                       |                                                                                                                                         |
   |                       |                       | Time format: UTC YYYY-MM-DDTHH:MM:SS.XXXXXX                                                                                             |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_3051__evs_04_2086_li105361616191716:

   Parameters in the **extra_specs** field

   +---------------------------+--------+---------------------------------------------+
   | Parameter                 | Type   | Description                                 |
   +===========================+========+=============================================+
   | volume_backend_name       | String | The reserved field.                         |
   +---------------------------+--------+---------------------------------------------+
   | availability-zone         | String | The reserved field.                         |
   +---------------------------+--------+---------------------------------------------+
   | HW:availability_zone      | String | The reserved field.                         |
   +---------------------------+--------+---------------------------------------------+
   | RESKEY:availability_zones | String | The AZs that support the current disk type. |
   +---------------------------+--------+---------------------------------------------+

-  .. _evs_04_3051__evs_04_2086_li0419202382514:

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
                      "volume_backend_name": "<or> iaas blockstorage_SAS <or> iaas blockstorage_SAS <or> iaas blockstoragesas",
                      "XX:availability_zone": "az-dc-1"
                  },
                  "is_public": true,
                  "deleted_at": null,
                  "id": "8247b6ed-37f0-4c48-8ef1-f0027fb332bc",
                  "name": "SAS"
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
