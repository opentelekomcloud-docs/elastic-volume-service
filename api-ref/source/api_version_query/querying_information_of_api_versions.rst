:original_name: evs_04_0020.html

.. _evs_04_0020:

Querying Information of API Versions
====================================

Function
--------

This API is used to query information of API versions.

URI
---

-  URI format

   GET /

Request
-------

-  Example request

   .. code-block:: text

      GET https://{endpoint}/

Response
--------

-  Parameter description

   +-----------+------------------+----------------------------------------------------------------------------------------------------------------------+
   | Parameter | Type             | Description                                                                                                          |
   +===========+==================+======================================================================================================================+
   | versions  | Array of objects | Specifies the API versions. For details, see :ref:`Parameters in the versions field <evs_04_0020__li8787321201856>`. |
   +-----------+------------------+----------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_0020__li8787321201856:

   Parameters in the **versions** field

   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                         |
   +=======================+=======================+=====================================================================================================================================================+
   | min_version           | String                | Specifies the minimum microversion supported. If this version does not support microversions, the value is an empty string.                         |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
   | media-types           | Array of objects      | Specifies the request message type of the API version. For details, see :ref:`Parameters in the media-types field <evs_04_0020__li16162726152446>`. |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
   | links                 | Array of objects      | Specifies the URI of the API version. For details, see :ref:`Parameters in the links field <evs_04_0020__li2542907152450>`.                         |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
   | id                    | String                | Specifies the ID of the API version.                                                                                                                |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
   | updated               | String                | Specifies the last time when the API version was updated.                                                                                           |
   |                       |                       |                                                                                                                                                     |
   |                       |                       | Time format: UTC YYYY-MM-DDTHH:MM:SS.XXXXXX                                                                                                         |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
   | version               | String                | Specifies the maximum microversion supported. If this version does not support microversions, the value is an empty string.                         |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+
   | status                | String                | Specifies the API version status. The value can be as follows:                                                                                      |
   |                       |                       |                                                                                                                                                     |
   |                       |                       | -  **CURRENT**: EVS custom APIs provide multiple versions. For the APIs offering same functions, you are recommended to use the v2 APIs.            |
   |                       |                       | -  **SUPPORTED**: indicates an earlier version which is still supported.                                                                            |
   |                       |                       | -  **DEPRECATED**: indicates a deprecated version that may be deleted later.                                                                        |
   +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------+

-  .. _evs_04_0020__li16162726152446:

   Parameters in the **media-types** field

   ========= ====== ============================
   Parameter Type   Description
   ========= ====== ============================
   type      String Specifies the response type.
   base      String Specifies the text type.
   ========= ====== ============================

-  .. _evs_04_0020__li2542907152450:

   Parameters in the **links** field

   ========= ====== ======================================
   Parameter Type   Description
   ========= ====== ======================================
   rel       String Specifies the domain name description.
   href      String Specifies the domain name.
   type      String Specifies the response type.
   ========= ====== ======================================

-  Example response

   .. code-block::

      {
          "versions": [
              {
                  "min_version": "",
                  "media-types": [
                      {
                          "type": "application/vnd.openstack.volume+json;version=1",
                          "base": "application/json"
                      },
                      {
                          "type": "application/vnd.openstack.volume+xml;version=1",
                          "base": "application/xml"
                      }
                  ],
                  "links": [
                      {
                          "rel": "describedby",
                          "href": "http://docs.openstack.org/",
                          "type": "text/html"
                      },
                      {
                          "rel": "self",
                          "href": "https://evs.localdomain.com/v1"
                      }
                  ],
                  "id": "v1.0",
                  "updated": "2014-06-28T12:20:21Z",
                  "version": "",
                  "status": "SUPPORTED"
              },
              {
                  "min_version": "",
                  "media-types": [
                      {
                          "type": "application/vnd.openstack.volume+json;version=1",
                          "base": "application/json"
                      },
                      {
                          "type": "application/vnd.openstack.volume+xml;version=1",
                          "base": "application/xml"
                      }
                  ],
                  "links": [
                      {
                          "rel": "describedby",
                          "href": "http://docs.openstack.org/",
                          "type": "text/html"
                      },
                      {
                          "rel": "self",
                          "href": "https://evs.localdomain.com/v2"
                      }
                  ],
                  "id": "v2.0",
                  "updated": "2014-06-28T12:20:21Z",
                  "version": "",
                  "status": "SUPPORTED"
              },
              {
                  "min_version": "3.0",
                  "media-types": [
                      {
                          "type": "application/vnd.openstack.volume+json;version=1",
                          "base": "application/json"
                      },
                      {
                          "type": "application/vnd.openstack.volume+xml;version=1",
                          "base": "application/xml"
                      }
                  ],
                  "links": [
                      {
                          "rel": "describedby",
                          "href": "http://docs.openstack.org/",
                          "type": "text/html"
                      },
                      {
                          "rel": "self",
                          "href": "https://evs.localdomain.com/v3"
                      }
                  ],
                  "id": "v3.0",
                  "updated": "2016-02-08T12:20:21Z",
                  "version": "3.0",
                  "status": "CURRENT"
              }
          ]
      }

Status Codes
------------

-  Normal

   300

Error Codes
-----------

For details, see :ref:`Error Codes <evs_04_0038>`.
