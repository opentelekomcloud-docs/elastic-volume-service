:original_name: evs_01_0024.html

.. _evs_01_0024:

Creating a DR ECS (Deprecated)
==============================

Scenarios
---------

Before you create an EVS replication pair, create a DR ECS in the secondary AZ for the production ECS. The DR ECS parameters must be consistent with those of the production ECS. The parameters include the ECS specifications and the parameters of the production ECS's EVS disks, subnet, and security group.

If a large number of physical resources in the primary AZ are faulty due to force majeure, you can attach DR disks in the secondary AZ to DR ECSs and use DR disks to ensure the service availability and continuity.

.. note::

   EVS replication APIs have been deprecated. If you need to use the replication function, see `Storage Disaster Recovery Service User Guide <https://docs.otc.t-systems.com/en-us/usermanual/sdrs/en-us_topic_0125068221.html>`__ and `Storage Disaster Recovery Service API Reference <https://docs.otc.t-systems.com/en-us/api/sdrs/sdrs_01_0000.html>`__.

Procedure
---------

#. Log in to the console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Choose **Compute** > **Elastic Cloud Server**.

   The **Elastic Cloud Server** page is displayed.

#. Click the name of the production ECS.

   The ECS details page is displayed.

#. Take note of the production ECS information, including the ECS specifications, details of the EVS disks attached to the ECS, private IP address, and security group, as shown in :ref:`Table 1 <evs_01_0024__en-us_topic_0080271666_table8510771171728>`.

   .. note::

      The listed parameter values are for reference only.

   .. _evs_01_0024__en-us_topic_0080271666_table8510771171728:

   .. table:: **Table 1** Information to be collected

      +-----------------------+-----------------------+---------------------------------+
      | Production Resource   | Parameter             | Example Value                   |
      +=======================+=======================+=================================+
      | ECS                   | VPC                   | vpc-001                         |
      +-----------------------+-----------------------+---------------------------------+
      |                       | ECS type              | General-purpose                 |
      +-----------------------+-----------------------+---------------------------------+
      |                       | Specification         | s2.xlarge.2                     |
      +-----------------------+-----------------------+---------------------------------+
      |                       | vCPU                  | 4 cores                         |
      +-----------------------+-----------------------+---------------------------------+
      |                       | Memory                | 8 GiB                           |
      +-----------------------+-----------------------+---------------------------------+
      |                       | Image                 | CentOS 7.2 64bit                |
      +-----------------------+-----------------------+---------------------------------+
      |                       | AZ                    | AZ1                             |
      +-----------------------+-----------------------+---------------------------------+
      | EVS disk              | Quantity              | -  System disk: 1               |
      |                       |                       | -  Data disk: 1                 |
      +-----------------------+-----------------------+---------------------------------+
      |                       | Capacity              | -  System disk: 500 GiB         |
      |                       |                       | -  Data disk: 2,000 GiB         |
      +-----------------------+-----------------------+---------------------------------+
      |                       | Disk type             | -  System disk: common I/O      |
      |                       |                       | -  Data disk: ultra-high I/O    |
      +-----------------------+-----------------------+---------------------------------+
      |                       | Disk sharing          | -  System disk: non-shared disk |
      |                       |                       | -  Data disk: non-shared disk   |
      +-----------------------+-----------------------+---------------------------------+
      |                       | Device type           | -  System disk: VBD             |
      |                       |                       | -  Data disk: SCSI              |
      +-----------------------+-----------------------+---------------------------------+
      | Others                | Private IP address    | 192.168.12.2                    |
      +-----------------------+-----------------------+---------------------------------+
      |                       | Security group        | Sys-default                     |
      +-----------------------+-----------------------+---------------------------------+
      |                       | Virtual IP address    | 192.168.12.23                   |
      +-----------------------+-----------------------+---------------------------------+

#. Create the DR ECS using the information of the production ECS.

   For details, see **Creating an ECS** in the *Elastic Cloud Server User Guide*.

   .. important::

      Check the parameter values carefully and ensure that information of the DR ECS and production ECS is consistent.

#. After the DR ECS has been created, locate the DR ECS and stop it.

   Stopping the DR ECS prevents it from being incorrectly used.

   .. note::

      When the DR ECS is not stopped and its system disk is used to create an EVS replication pair, the DR ECS status will change to **REBUILDING**. In this state, you cannot stop the DR ECS, detach EVS disks from it, or expand its EVS disks.

.. |image1| image:: /_static/images/en-us_image_0237893718.png
