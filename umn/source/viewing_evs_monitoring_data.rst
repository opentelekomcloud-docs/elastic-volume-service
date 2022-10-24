:original_name: evs_01_0044.html

.. _evs_01_0044:

Viewing EVS Monitoring Data
===========================

Description
-----------

This section describes monitored metrics reported by EVS to Cloud Eye as well as their namespaces and dimensions. You can use console or APIs provided by Cloud Eye to query the metrics of the monitored objects and alarms generated for EVS.

Namespace
---------

SYS.EVS

Metrics
-------

.. table:: **Table 1** EVS metrics

   +---------------------------------+----------------------+----------------------------------------------------------------+-----------------+------------------+------------------------------+
   | Metric ID                       | Metric Name          | Description                                                    | Value Range     | Monitored Object | Monitoring Period (Raw Data) |
   +=================================+======================+================================================================+=================+==================+==============================+
   | disk_device_read_bytes_rate     | Disk Read Bandwidth  | Number of bytes read from the monitored disk per second        | >= 0 bytes/s    | EVS disk         | 5 minutes                    |
   |                                 |                      |                                                                |                 |                  |                              |
   |                                 |                      | Unit: Bytes/s                                                  |                 |                  |                              |
   +---------------------------------+----------------------+----------------------------------------------------------------+-----------------+------------------+------------------------------+
   | disk_device_write_bytes_rate    | Disk Write Bandwidth | Number of bytes written to the monitored disk per second       | >= 0 bytes/s    | EVS disk         | 5 minutes                    |
   |                                 |                      |                                                                |                 |                  |                              |
   |                                 |                      | Unit: Bytes/s                                                  |                 |                  |                              |
   +---------------------------------+----------------------+----------------------------------------------------------------+-----------------+------------------+------------------------------+
   | disk_device_read_requests_rate  | Disk Read IOPS       | Number of read requests sent to the monitored disk per second  | >= 0 Requests/s | EVS disk         | 5 minutes                    |
   |                                 |                      |                                                                |                 |                  |                              |
   |                                 |                      | Unit: Requests/s                                               |                 |                  |                              |
   +---------------------------------+----------------------+----------------------------------------------------------------+-----------------+------------------+------------------------------+
   | disk_device_write_requests_rate | Disk Write IOPS      | Number of write requests sent to the monitored disk per second | >= 0 Requests/s | EVS disk         | 5 minutes                    |
   |                                 |                      |                                                                |                 |                  |                              |
   |                                 |                      | Unit: Requests/s                                               |                 |                  |                              |
   +---------------------------------+----------------------+----------------------------------------------------------------+-----------------+------------------+------------------------------+

Dimension
---------

+-----------+---------------------------------------------------------------------------------------------------------+
| Key       | Value                                                                                                   |
+===========+=========================================================================================================+
| disk_name | Server ID-drive letter, for example, 6f3c6f91-4b24-4e1b-b7d1-a94ac1cb011d-vda (vda is the drive letter) |
+-----------+---------------------------------------------------------------------------------------------------------+

Viewing Monitoring Data
-----------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Under **Storage**, click **Elastic Volume Service**.

   The disk list page is displayed.

#. In the EVS disk list, click the name of the disk you want to view the monitoring data.

   The disk details page is displayed.

#. On the **Attachments** tab, locate the row that contains the server and click **View Monitoring Data** in the **Operation** column.

   The monitoring graphs page is displayed.

#. You can view the disk monitoring data by metric or monitored duration.

   For more information about Cloud Eye, see the *Cloud Eye User Guide*.

.. |image1| image:: /_static/images/en-us_image_0237893718.png
