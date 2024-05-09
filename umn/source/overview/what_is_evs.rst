:original_name: en-us_topic_0014580741.html

.. _en-us_topic_0014580741:

What Is EVS?
============

Overview
--------

Elastic Volume Service (EVS) offers scalable block storage for cloud servers. With high reliability, high performance, and a variety of specifications, EVS disks can be used for distributed file systems, development and test environments, data warehouses, and high-performance computing (HPC) applications. Cloud servers that EVS supports include Elastic Cloud Servers (ECSs) and BMS.

EVS disks are similar to hard disks in PCs. They must be attached to servers for use and cannot be used alone. You can initialize EVS disks, create file systems on them, and store data persistently on them.

EVS disks are sometimes just referred to as disks in this document.


.. figure:: /_static/images/en-us_image_0205523160.png
   :alt: **Figure 1** EVS architecture

   **Figure 1** EVS architecture

EVS Advantages
--------------

EVS has the following advantages:

.. table:: **Table 1** EVS advantages

   +-------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------+
   | Advantage                     | Description                                                                                                                                                                                                                      | Related Knowledge                                          |
   +===============================+==================================================================================================================================================================================================================================+============================================================+
   | Various disk types            | EVS provides a variety of disk types for you to choose from, and EVS disks can be used as data disks and system disks for servers. You can select an appropriate disk type that best suits your budget and service requirements. | :ref:`Disk Types and Performance <en-us_topic_0014580744>` |
   +-------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------+
   | Elastic scalability           | The EVS disk capacity ranges from 10 GiB to 32 TiB. When it no longer meets your needs, you can expand the disk capacity up to 32 TiB in increments of 1 GiB, without interrupting your applications.                            | :ref:`Expansion Overview <evs_01_0006>`                    |
   +-------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------+
   |                               | Besides the disk capacity limit, the additional space you can add cannot exceed the remaining quota. You can increase the quota if the remaining quota is insufficient.                                                          | :ref:`Manage EVS Quotas <evs_01_0069>`                     |
   +-------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------+
   | High security and reliability | Both system disks and data disks support data encryption to ensure data security.                                                                                                                                                | :ref:`EVS Encryption <evs_01_0001>`                        |
   +-------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------+
   |                               | Data protection functions, such as backups and snapshots, safeguard the disk data, preventing incorrect data caused by application exceptions or attacks.                                                                        | :ref:`EVS Backup <evs_01_0021>`                            |
   |                               |                                                                                                                                                                                                                                  |                                                            |
   |                               |                                                                                                                                                                                                                                  | :ref:`EVS Snapshot <en-us_topic_0066809008>`               |
   +-------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------+
   | Real-time monitoring          | On Cloud Eye, you can monitor the disk health and operating status at any time.                                                                                                                                                  | :ref:`Viewing EVS Monitoring Data <evs_01_0044>`           |
   +-------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------+

Differences Among EVS, SFS, and OBS
-----------------------------------

There are currently three types of storage available for you to choose from: EVS, Scalable File Service (SFS), and Object Storage Service (OBS). See their differences in the following table.

.. table:: **Table 2** Differences among EVS, SFS, and OBS

   +-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------+
   | Service         | Overall Introduction                                                                                                                                                                                                                                | Typical Application Scenarios                                                           | Storage Capacity                                                                                                  |
   +=================+=====================================================================================================================================================================================================================================================+=========================================================================================+===================================================================================================================+
   | EVS             | EVS provides scalable block storage that features high reliability, high performance, and a variety of specifications for servers.                                                                                                                  | -  Enterprise office applications                                                       | EVS disks start at 10 GiB and can be expanded as required in 1 GiB increments to up to 32 TiB.                    |
   |                 |                                                                                                                                                                                                                                                     | -  Development and testing                                                              |                                                                                                                   |
   |                 |                                                                                                                                                                                                                                                     | -  Enterprise applications, including SAP, Microsoft Exchange, and Microsoft SharePoint |                                                                                                                   |
   |                 |                                                                                                                                                                                                                                                     | -  Distributed file systems                                                             |                                                                                                                   |
   |                 |                                                                                                                                                                                                                                                     | -  Various databases, including MongoDB, Oracle, SQL Server, MySQL, and PostgreSQL      |                                                                                                                   |
   +-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------+
   | SFS             | SFS provides completely hosted shared file storage for cloud servers. Compatible with the Network File System (NFS) protocol, SFS is expandable to petabytes and seamlessly handles data-intensive and bandwidth-intensive applications.            | -  HPC scenarios, such as gene sequencing, animation rendering, and CAD/CAE             | SFS storage capacity is available on demand and can be expanded to a maximum of 2 PiB.                            |
   |                 |                                                                                                                                                                                                                                                     | -  File sharing                                                                         |                                                                                                                   |
   |                 |                                                                                                                                                                                                                                                     | -  Media processing                                                                     |                                                                                                                   |
   |                 |                                                                                                                                                                                                                                                     | -  Content management and web services                                                  |                                                                                                                   |
   |                 |                                                                                                                                                                                                                                                     | -  Offline file backup                                                                  |                                                                                                                   |
   +-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------+
   | OBS             | OBS provides cloud storage for unstructured data, such as files, pictures, and videos. With multiple options for migration to the cloud, OBS provides low-cost, reliable storage access for massive data and supports online multimedia processing. | -  Enterprise backup and archive                                                        | OBS has limitless storage capacity, and storage resources are available for linear and nearly infinite expansion. |
   |                 |                                                                                                                                                                                                                                                     | -  Big data analysis                                                                    |                                                                                                                   |
   |                 |                                                                                                                                                                                                                                                     | -  Enterprise cloud box                                                                 |                                                                                                                   |
   |                 |                                                                                                                                                                                                                                                     | -  Static website hosting                                                               |                                                                                                                   |
   |                 |                                                                                                                                                                                                                                                     | -  Cloud-native applications                                                            |                                                                                                                   |
   +-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------+

Methods of Access
-----------------

The public cloud system provides a web-based management console and HTTPS-based APIs for you to access the EVS service.

-  APIs

   Use APIs if you need to integrate EVS into a third-party system for secondary development. For details, see *Elastic Volume Service API Reference*.

-  Management console

   Use the management console if you do not need to integrate EVS with a third-party system. Log in to the management console and choose **Elastic Volume Service** from the service list.

User Permissions
----------------

Users with resource management permissions can control the operations performed on cloud service resources. For EVS, a user with the Server Administrator permission can perform operations on EVS resources, including creating disks, deleting disks, and creating snapshots.

For details about user permissions, see `Permissions <https://docs.otc.t-systems.com/en-us/permissions/index.html>`__.

Project
-------

A project is used to group and isolate OpenStack resources, including compute, storage, and network resources. A project can be a department or a project team. You can access IAM with a security administrator to create projects in a region and perform isolated management of resources. For details about projects, see `Managing Projects <https://docs.otc.t-systems.com/en-us/usermanual/iam/en-us_topic_0066738518.html>`__.
