:original_name: evs_01_0044.html

.. _evs_01_0044:

Viewing Basic EVS Monitoring Data
=================================

Description
-----------

This section describes monitored metrics reported by EVS to Cloud Eye as well as their namespaces and dimensions. You can use the console or APIs provided by Cloud Eye to query the metrics of the monitored objects and alarms generated for EVS.

Namespace
---------

SYS.EVS

Metrics
-------

.. table:: **Table 1** EVS metrics

   +---------------------------------------+---------------------------------------+------------------------------------------------------------------------------------------------------------------------+-------------------+------------------+----------------------+
   | Metric ID                             | Metric Name                           | Description                                                                                                            | Value Range       | Monitored Object | Monitoring Period    |
   +=======================================+=======================================+========================================================================================================================+===================+==================+======================+
   | disk_device_read_bytes_rate           | Disk Read Bandwidth                   | Number of bytes read from the monitored disk per second                                                                | >= 0 bytes/s      | EVS disk         | 5 minutes in average |
   |                                       |                                       |                                                                                                                        |                   |                  |                      |
   |                                       |                                       | Unit: Bytes/s                                                                                                          |                   |                  |                      |
   +---------------------------------------+---------------------------------------+------------------------------------------------------------------------------------------------------------------------+-------------------+------------------+----------------------+
   | disk_device_write_bytes_rate          | Disk Write Bandwidth                  | Number of bytes written to the monitored disk per second                                                               | >= 0 bytes/s      | EVS disk         | 5 minutes in average |
   |                                       |                                       |                                                                                                                        |                   |                  |                      |
   |                                       |                                       | Unit: Bytes/s                                                                                                          |                   |                  |                      |
   +---------------------------------------+---------------------------------------+------------------------------------------------------------------------------------------------------------------------+-------------------+------------------+----------------------+
   | disk_device_read_requests_rate        | Disk Read IOPS                        | Number of read requests sent to the monitored disk per second                                                          | >= 0 Requests/s   | EVS disk         | 5 minutes in average |
   |                                       |                                       |                                                                                                                        |                   |                  |                      |
   |                                       |                                       | Unit: Requests/s                                                                                                       |                   |                  |                      |
   +---------------------------------------+---------------------------------------+------------------------------------------------------------------------------------------------------------------------+-------------------+------------------+----------------------+
   | disk_device_write_requests_rate       | Disk Write IOPS                       | Number of write requests sent to the monitored disk per second                                                         | >= 0 Requests/s   | EVS disk         | 5 minutes in average |
   |                                       |                                       |                                                                                                                        |                   |                  |                      |
   |                                       |                                       | Unit: Requests/s                                                                                                       |                   |                  |                      |
   +---------------------------------------+---------------------------------------+------------------------------------------------------------------------------------------------------------------------+-------------------+------------------+----------------------+
   | disk_device_queue_length              | Average Queue Length                  | Average number of read or write requests waiting for processing in the monitoring period for the monitored disk        | >= 0 Counts       | EVS disk         | 5 minutes in average |
   |                                       |                                       |                                                                                                                        |                   |                  |                      |
   |                                       |                                       | Unit: Count                                                                                                            |                   |                  |                      |
   +---------------------------------------+---------------------------------------+------------------------------------------------------------------------------------------------------------------------+-------------------+------------------+----------------------+
   | disk_device_io_util                   | Disk I/O Utilization                  | Percentage of time spent during which read and write requests were sent to the monitored disk in the monitoring period | 0-100%            | EVS disk         | 5 minutes in average |
   |                                       |                                       |                                                                                                                        |                   |                  |                      |
   |                                       |                                       | Unit: Percent                                                                                                          |                   |                  |                      |
   +---------------------------------------+---------------------------------------+------------------------------------------------------------------------------------------------------------------------+-------------------+------------------+----------------------+
   | disk_device_write_bytes_per_operation | Avg Disk Bytes Per Write              | Average number of bytes transmitted per I/O write for the monitored disk in the monitoring period                      | >= 0 KiB/op       | EVS disk         | 5 minutes in average |
   |                                       |                                       |                                                                                                                        |                   |                  |                      |
   |                                       |                                       | Unit: Kbyte/operation                                                                                                  |                   |                  |                      |
   +---------------------------------------+---------------------------------------+------------------------------------------------------------------------------------------------------------------------+-------------------+------------------+----------------------+
   | disk_device_read_bytes_per_operation  | Avg Disk Bytes Per Read               | Average number of bytes transmitted per I/O read for the monitored disk in the monitoring period                       | >= 0 KiB/op       | EVS disk         | 5 minutes in average |
   |                                       |                                       |                                                                                                                        |                   |                  |                      |
   |                                       |                                       | Unit: Kbyte/operation                                                                                                  |                   |                  |                      |
   +---------------------------------------+---------------------------------------+------------------------------------------------------------------------------------------------------------------------+-------------------+------------------+----------------------+
   | disk_device_write_await               | Disk Write Await                      | Average await time per I/O write for the monitored disk in the monitoring period                                       | >= 0 ms/operation | EVS disk         | 5 minutes in average |
   |                                       |                                       |                                                                                                                        |                   |                  |                      |
   |                                       |                                       | Unit: ms/operation                                                                                                     |                   |                  |                      |
   +---------------------------------------+---------------------------------------+------------------------------------------------------------------------------------------------------------------------+-------------------+------------------+----------------------+
   | disk_device_read_await                | Disk Read Await                       | Average await time per I/O read for the monitored disk in the monitoring period                                        | >= 0 ms/operation | EVS disk         | 5 minutes in average |
   |                                       |                                       |                                                                                                                        |                   |                  |                      |
   |                                       |                                       | Unit: ms/operation                                                                                                     |                   |                  |                      |
   +---------------------------------------+---------------------------------------+------------------------------------------------------------------------------------------------------------------------+-------------------+------------------+----------------------+
   | disk_device_io_svctm                  | Disk I/O Service Time                 | Average service time per I/O read or write for the monitored disk in the monitoring period                             | >= 0 ms/operation | EVS disk         | 5 minutes in average |
   |                                       |                                       |                                                                                                                        |                   |                  |                      |
   |                                       |                                       | Unit: ms/operation                                                                                                     |                   |                  |                      |
   +---------------------------------------+---------------------------------------+------------------------------------------------------------------------------------------------------------------------+-------------------+------------------+----------------------+
   | disk_device_io_iops_qos_num           | IOPS Upper Limit Reached (Count)      | Number of times that the IOPS of the monitored disk has reached the upper limit                                        | >= 0 Counts       | EVS disk         | 5 minutes in average |
   |                                       |                                       |                                                                                                                        |                   |                  |                      |
   |                                       |                                       | Unit: Count                                                                                                            |                   |                  |                      |
   +---------------------------------------+---------------------------------------+------------------------------------------------------------------------------------------------------------------------+-------------------+------------------+----------------------+
   | disk_device_io_iobw_qos_num           | Bandwidth Upper Limit Reached (Count) | Number of times that the bandwidth of the monitored disk has reached the upper limit                                   | >= 0 Counts       | EVS disk         | 5 minutes in average |
   |                                       |                                       |                                                                                                                        |                   |                  |                      |
   |                                       |                                       | Unit: Count                                                                                                            |                   |                  |                      |
   +---------------------------------------+---------------------------------------+------------------------------------------------------------------------------------------------------------------------+-------------------+------------------+----------------------+

Dimension
---------

+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------+
| Key                               | Value                                                                                                                                                 |
+===================================+=======================================================================================================================================================+
| disk_name                         | *Server ID*\ ``-``\ *drive letter*, for example, **6f3c6f91-4b24-4e1b-b7d1-a94ac1cb011d-vda** (vda is the drive letter)                               |
|                                   |                                                                                                                                                       |
|                                   | *Server ID*\ ``-``\ **volume**\ ``-``\ *Volume ID*, for example, **6f3c6f91-4b24-4e1b-b7d1-a94ac1cb011d-volume-31f45764-38b3-44ad-aaca-4015c83371e6** |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------+

Viewing Monitoring Data
-----------------------

#. Log in to the console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Choose **Storage** > **Elastic Volume Service**.

   The **Elastic Volume Service** page is displayed.

#. In the EVS disk list, click the name of the disk you want to view the monitoring data.

   The disk details page is displayed.

#. On the **Attachments** tab, locate the row that contains the server and click **View Monitoring Data** in the **Operation** column.

   The monitoring graphs page is displayed.

#. View the disk monitoring data by metric or monitored duration.

   For more information about Cloud Eye, see the *Cloud Eye User Guide*.

.. |image1| image:: /_static/images/en-us_image_0237893718.png
