:original_name: evs_04_2096.html

.. _evs_04_2096:

Querying EVS Snapshots
======================

Function
--------

This API is used to query the EVS snapshots.

URI
---

-  URI format

   GET /v2/{project_id}/snapshots

-  Parameter description

   ========== ========= ===============
   Parameter  Mandatory Description
   ========== ========= ===============
   project_id Yes       The project ID.
   ========== ========= ===============

-  Request filter parameters

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Type            | Mandatory       | Description                                                                                                                                                                                                                                                                                                                        |
   +=================+=================+=================+====================================================================================================================================================================================================================================================================================================================================+
   | marker          | String          | No              | The ID of the resource from which the pagination query starts. It is the ID of the last resource on the previous page.                                                                                                                                                                                                             |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | offset          | Integer         | No              | The query offset.                                                                                                                                                                                                                                                                                                                  |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                    |
   |                 |                 |                 | .. note::                                                                                                                                                                                                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                    |
   |                 |                 |                 |    This parameter is used when snapshots are queried by page and is used together with the **limit** parameter. For example, there are a total of 30 snapshots. If you set **offset** to **11** and **limit** to **10**, the queried snapshot starts from the twelfth snapshot, and at most 10 snapshots can be queried at a time. |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit           | Integer         | No              | The maximum number of query results that can be returned.                                                                                                                                                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                    |
   |                 |                 |                 | The value ranges from 1 to 1000, and the default value is 1000. The returned value cannot exceed this limit.                                                                                                                                                                                                                       |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                    |
   |                 |                 |                 | If the tenant has more than 50 snapshots in total, you are advised to use this parameter and set its value to **50** to improve the query efficiency. Examples are provided as follows:                                                                                                                                            |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                    |
   |                 |                 |                 | **GET /v2/**\ *xxx*\ **/snapshots?limit=50**: Queries the 1-50 snapshots. **GET /v2/**\ *xxx*\ **/snapshots?offset=50&limit=50**: Queries the 51-100 snapshots.                                                                                                                                                                    |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name            | String          | No              | The snapshot name. This parameter does not support fuzzy search. The value can contain a maximum of 255 bytes.                                                                                                                                                                                                                     |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status          | String          | No              | The snapshot status. For details, see :ref:`EVS Snapshot Status <evs_04_0041>`.                                                                                                                                                                                                                                                    |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | volume_id       | String          | No              | The ID of the snapshot's source disk.                                                                                                                                                                                                                                                                                              |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request
-------

The following example shows how to query the snapshots in the **available** state.

-  Example request

   .. code-block:: text

      GET https://{endpoint}/v2/{project_id}/snapshots?status=available

Response
--------

-  Parameter description

   +-----------------+--------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Type                     | Description                                                                                                                                                                                                                                                                          |
   +=================+==========================+======================================================================================================================================================================================================================================================================================+
   | snapshots       | Object                   | The snapshot information. For details, see :ref:`Parameters in the snapshots field <evs_04_2096__li367387041175>`.                                                                                                                                                                   |
   +-----------------+--------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | snapshots_links | list<map<String,String>> | The query position marker in the snapshot list. This parameter is at the same level as parameter **snapshots** in the response body. It is returned only when parameter **limit** is specified in the request, and it indicates that only some snapshots are returned in this query. |
   +-----------------+--------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | error           | Object                   | The error message returned if an error occurs. For details, see :ref:`Parameters in the error field <evs_04_2096__li0419202382514>`.                                                                                                                                                 |
   +-----------------+--------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_2096__li367387041175:

   Parameters in the **snapshots** field

   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                          |
   +=======================+=======================+======================================================================================================================================+
   | id                    | String                | The snapshot ID.                                                                                                                     |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------+
   | status                | String                | The snapshot status. For details, see :ref:`EVS Snapshot Status <evs_04_0041>`.                                                      |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------+
   | name                  | String                | The snapshot name.                                                                                                                   |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------+
   | description           | String                | The snapshot description.                                                                                                            |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------+
   | created_at            | String                | The time when the snapshot was created.                                                                                              |
   |                       |                       |                                                                                                                                      |
   |                       |                       | Time format: UTC YYYY-MM-DDTHH:MM:SS.XXXXXX                                                                                          |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------+
   | metadata              | Object                | The snapshot metadata.                                                                                                               |
   |                       |                       |                                                                                                                                      |
   |                       |                       | If **metadata** contains the **\__system__enableActive** field, the snapshot is automatically created during the backup of a server. |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------+
   | volume_id             | String                | The ID of the snapshot's source disk.                                                                                                |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------+
   | size                  | Integer               | The snapshot size, in GB.                                                                                                            |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------+
   | updated_at            | String                | The time when the snapshot was updated.                                                                                              |
   |                       |                       |                                                                                                                                      |
   |                       |                       | Time format: UTC YYYY-MM-DDTHH:MM:SS.XXXXXX                                                                                          |
   +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_2096__li0419202382514:

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
          "snapshots": [
              {
                  "created_at": "2016-02-16T16:54:14.981520",
                  "description": null,
                  "id": "b836dc3d-4e10-4ea4-a34c-8f6b0460a583",
                  "metadata": { },
                  "name": "test01",
                  "size": 1,
                  "status": "available",
                  "volume_id": "ba5730ea-8621-4ae8-b702-ff0ffc12c209",
                  "updated_at": null
              },
              {
                  "created_at": "2016-02-16T16:54:19.475397",
                  "description": null,
                  "id": "83be494d-329e-4a78-8ac5-9af900f48b95",
                  "metadata": { },
                  "name": "test02",
                  "size": 1,
                  "status": "available",
                  "volume_id": "ba5730ea-8621-4ae8-b702-ff0ffc12c209",
                  "updated_at": null
              },
              {
                  "created_at": "2016-02-16T16:54:24.367414",
                  "description": null,
                  "id": "dd360f46-7593-4d35-8f2c-5566fd0bd79e",
                  "metadata": { },
                  "name": "test03",
                  "size": 1,
                  "status": "available",
                  "volume_id": "ba5730ea-8621-4ae8-b702-ff0ffc12c209",
                  "updated_at": null
              },
              {
                  "created_at": "2016-02-16T16:54:29.766740",
                  "description": null,
                  "id": "4c29796a-8cf4-4482-9afc-e66da9a81240",
                  "metadata": { },
                  "name": "test04",
                  "size": 1,
                  "status": "available",
                  "volume_id": "ba5730ea-8621-4ae8-b702-ff0ffc12c209",
                  "updated_at": null
              }
          ],
          "snapshots_links": null
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

   200

Error Codes
-----------

For details, see :ref:`Error Codes <evs_04_0038>`.
