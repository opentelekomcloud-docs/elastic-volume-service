:original_name: evs_01_0025.html

.. _evs_01_0025:

Collecting ECS Information (Deprecated)
=======================================

Scenarios
---------

This section is used to guide users to collect the production ECS and DR ECS information, including the ECS IDs and the IDs of the EVS disks attached the ECSs.

Two EVS disks form an EVS replication pair. Therefore, the production disk ID, DR disk ID, and EVS replication pair ID can be used to identify disks and the EVS replication pair.

.. note::

   EVS replication APIs have been deprecated. If you need to use the replication function, see `Storage Disaster Recovery Service User Guide <https://docs.otc.t-systems.com/en-us/usermanual/sdrs/en-us_topic_0125068221.html>`__ and `Storage Disaster Recovery Service API Reference <https://docs.otc.t-systems.com/en-us/api/sdrs/sdrs_01_0000.html>`__.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Under **Computing**, click **Elastic Cloud Server**.

   The **Elastic Cloud Server** page is displayed.

#. .. _evs_01_0025__li23677833165924:

   Click the name of the production ECS.

   The ECS details page is displayed.

#. .. _evs_01_0025__li3726148311399:

   Perform the following operations to take note of the production ECS information:

   a. Take note of the production ECS ID.

      Example ID: 4686b400-5a53-42f9-96f6-d2fe32bb9542

   b. Click the **Disks** tab. Click |image2| to view the details of the corresponding disk and take note of all the production disk IDs.

      You need to take note of the IDs of all the system disks and data disks attached to the production ECS.

      Example ID: ce86f381-99dc-422c-bb10-8014604cf5b9

   c. Click the **NICs** tab. Click |image3| to view the private IP address, elastic IP address (EIP), virtual IP address, and MAC address of a production NIC and take note of the private IP addresses, EIPs, virtual IP addresses, and MAC addresses of all NICs accordingly.

      You need to take note of IP addresses of all NICs bound to the production ECS.

      Example addresses: 192.168.xx.xx, 10.154.xx.xx, 192.168.xx.xx, {mac}

      .. note::

         Replace **{mac}** with the MAC address during operation.

#. Take note of the DR ECS information. For details, see :ref:`4 <evs_01_0025__li23677833165924>` to :ref:`5 <evs_01_0025__li3726148311399>`.

.. |image1| image:: /_static/images/en-us_image_0237893718.png

.. |image2| image:: /_static/images/en-us_image_0238263421.jpg

.. |image3| image:: /_static/images/en-us_image_0238263421.jpg

