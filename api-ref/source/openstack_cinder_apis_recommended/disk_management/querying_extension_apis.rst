:original_name: evs_04_2080.html

.. _evs_04_2080:

Querying Extension APIs
=======================

Function
--------

This API is used to query extension APIs.

URI
---

-  URI format

   GET /v2/{project_id}/extensions

-  Parameter description

   ========== ========= =========================
   Parameter  Mandatory Description
   ========== ========= =========================
   project_id Yes       Specifies the project ID.
   ========== ========= =========================

Request
-------

-  Example request

   .. code-block:: text

      GET https://{endpoint}/v2/{project_id}/extensions

Response
--------

-  Parameter description

   +------------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Type   | Description                                                                                                                                      |
   +============+========+==================================================================================================================================================+
   | extensions | list   | Specifies the extension APIs. For details, see :ref:`Parameters in the extensions field <evs_04_2080__li35330737222812>`.                        |
   +------------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------+
   | error      | Object | Specifies the error message returned when an error occurs. For details, see :ref:`Parameters in the error field <evs_04_2080__li0419202382514>`. |
   +------------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_2080__li35330737222812:

   Parameters in the **extensions** field

   +-----------------------+--------------------------+---------------------------------------------+
   | Parameter             | Type                     | Description                                 |
   +=======================+==========================+=============================================+
   | updated               | String                   | Specifies the last update time.             |
   |                       |                          |                                             |
   |                       |                          | Time format: UTC YYYY-MM-DDTHH:MM:SS.+XX.XX |
   +-----------------------+--------------------------+---------------------------------------------+
   | description           | String                   | Specifies the description.                  |
   +-----------------------+--------------------------+---------------------------------------------+
   | links                 | list<map<String,String>> | The reserved field.                         |
   +-----------------------+--------------------------+---------------------------------------------+
   | alias                 | String                   | Specifies the extension parameter alias.    |
   +-----------------------+--------------------------+---------------------------------------------+
   | name                  | String                   | Specifies the extension parameter name.     |
   +-----------------------+--------------------------+---------------------------------------------+

-  .. _evs_04_2080__li0419202382514:

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
          "extensions": [
              {
                  "updated": "2013-04-18T00:00:00+00:00",
                  "name": "SchedulerHints",
                  "links": [ ],
                  "alias": "OS-SCH-HNT",
                  "description": "Pass arbitrary key/value pairs to the scheduler."
              },
              {
                  "updated": "2011-06-29T00:00:00+00:00",
                  "name": "Hosts",
                  "links": [ ],
                  "alias": "os-hosts",
                  "description": "Admin-only host administration."
              },
              {
                  "updated": "2011-11-03T00:00:00+00:00",
                  "name": "VolumeTenantAttribute",
                  "links": [ ],
                  "alias": "os-vol-tenant-attr",
                  "description": "Expose the internal project_id as an attribute of a volume."
              },
              {
                  "updated": "2011-08-08T00:00:00+00:00",
                  "name": "Quotas",
                  "links": [ ],
                  "alias": "os-quota-sets",
                  "description": "Quota management support."
              },
              {
                  "updated": "2011-08-24T00:00:00+00:00",
                  "name": "TypesManage",
                  "links": [ ],
                  "alias": "os-types-manage",
                  "description": "Types manage support."
              },
              {
                  "updated": "2013-07-10T00:00:00+00:00",
                  "name": "VolumeEncryptionMetadata",
                  "links": [ ],
                  "alias": "os-volume-encryption-metadata",
                  "description": "Volume encryption metadata retrieval support."
              },
              {
                  "updated": "2012-12-12T00:00:00+00:00",
                  "name": "Backups",
                  "links": [ ],
                  "alias": "backups",
                  "description": "Backups support."
              },
              {
                  "updated": "2013-07-16T00:00:00+00:00",
                  "name": "SnapshotActions",
                  "links": [ ],
                  "alias": "os-snapshot-actions",
                  "description": "Enable snapshot manager actions."
              },
              {
                  "updated": "2012-05-31T00:00:00+00:00",
                  "name": "VolumeActions",
                  "links": [ ],
                  "alias": "os-volume-actions",
                  "description": "Enable volume actions
          "
              },
              {
                  "updated": "2013-10-03T00:00:00+00:00",
                  "name": "UsedLimits",
                  "links": [ ],
                  "alias": "os-used-limits",
                  "description": "Provide data on limited resources that are being used."
              },
              {
                  "updated": "2012-05-31T00:00:00+00:00",
                  "name": "VolumeUnmanage",
                  "links": [ ],
                  "alias": "os-volume-unmanage",
                  "description": "Enable volume unmanage operation."
              },
              {
                  "updated": "2011-11-03T00:00:00+00:00",
                  "name": "VolumeHostAttribute",
                  "links": [ ],
                  "alias": "os-vol-host-attr",
                  "description": "Expose host as an attribute of a volume."
              },
              {
                  "updated": "2013-07-01T00:00:00+00:00",
                  "name": "VolumeTypeEncryption",
                  "links": [ ],
                  "alias": "encryption",
                  "description": "Encryption support for volume types."
              },
              {
                  "updated": "2013-06-27T00:00:00+00:00",
                  "name": "AvailabilityZones",
                  "links": [ ],
                  "alias": "os-availability-zone",
                  "description": "Describe Availability Zones."
              },
              {
                  "updated": "2013-08-02T00:00:00+00:00",
                  "name": "Qos_specs_manage",
                  "links": [ ],
                  "alias": "qos-specs",
                  "description": "QoS specs support."
              },
              {
                  "updated": "2011-08-24T00:00:00+00:00",
                  "name": "TypesExtraSpecs",
                  "links": [ ],
                  "alias": "os-types-extra-specs",
                  "description": "Type extra specs support."
              },
              {
                  "updated": "2013-08-08T00:00:00+00:00",
                  "name": "VolumeMigStatusAttribute",
                  "links": [ ],
                  "alias": "os-vol-mig-status-attr",
                  "description": "Expose migration_status as an attribute of a volume."
              },
              {
                  "updated": "2012-08-13T00:00:00+00:00",
                  "name": "CreateVolumeExtension",
                  "links": [ ],
                  "alias": "os-image-create",
                  "description": "Allow creating a volume from an image in the Create Volume v1 API."
              },
              {
                  "updated": "2014-01-10T00:00:00-00:00",
                  "name": "ExtendedServices",
                  "links": [ ],
                  "alias": "os-extended-services",
                  "description": "Extended services support."
              },
              {
                  "updated": "2012-06-19T00:00:00+00:00",
                  "name": "ExtendedSnapshotAttributes",
                  "links": [ ],
                  "alias": "os-extended-snapshot-attributes",
                  "description": "Extended SnapshotAttributes support."
              },
              {
                  "updated": "2012-12-07T00:00:00+00:00",
                  "name": "VolumeImageMetadata",
                  "links": [ ],
                  "alias": "os-vol-image-meta",
                  "description": "Show image metadata associated with the volume."
              },
              {
                  "updated": "2012-03-12T00:00:00+00:00",
                  "name": "QuotaClasses",
                  "links": [ ],
                  "alias": "os-quota-class-sets",
                  "description": "Quota classes management support."
              },
              {
                  "updated": "2013-05-29T00:00:00+00:00",
                  "name": "VolumeTransfer",
                  "links": [ ],
                  "alias": "os-volume-transfer",
                  "description": "Volume transfer management support."
              },
              {
                  "updated": "2014-02-10T00:00:00+00:00",
                  "name": "VolumeManage",
                  "links": [ ],
                  "alias": "os-volume-manage",
                  "description": "Allows existing backend storage to be 'managed' by Cinder."
              },
              {
                  "updated": "2012-08-25T00:00:00+00:00",
                  "name": "AdminActions",
                  "links": [ ],
                  "alias": "os-admin-actions",
                  "description": "Enable admin actions."
              },
              {
                  "updated": "2012-10-28T00:00:00-00:00",
                  "name": "Services",
                  "links": [ ],
                  "alias": "os-services",
                  "description": "Services support."
              }
          ]
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
          "badRequest": {
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
