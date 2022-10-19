:original_name: en-us_topic_0014580741.html

.. _en-us_topic_0014580741:

What Is EVS?
============

Overview
--------

Elastic Volume Service (EVS) offers scalable block storage for cloud servers. With high reliability, high performance, and rich specifications, EVS disks can be used for distributed file systems, development and testing environments, data warehouse applications, and high-performance computing (HPC) scenarios to meet diverse service requirements. Servers that EVS supports include Elastic Cloud Servers (ECSs) and Bare Metal Servers (BMSs).

EVS disks are sometimes just referred to as disks in this document.

.. _en-us_topic_0014580741__fig1392425915011:

.. figure:: /_static/images/en-us_image_0205523160.png
   :alt: **Figure 1** EVS architecture


   **Figure 1** EVS architecture

EVS Advantages
--------------

EVS has the following advantages:

-  Various disk types

   EVS provides various disk types for you to choose from, and EVS disks can be used as data disks and system disks for servers. You may select the disk type based on your budget and service requirements.

-  Elastic scalability

   The EVS disk capacity ranges from 10 GB to 32 TB. When it no longer meets your needs, you can expand the disk capacity up to 32 TB in increments of 1 GB, without interrupting your applications.

   Besides the disk capacity limit, the additional space you can add cannot exceed the remaining quota. You can increase the quota if the remaining quota is insufficient.

-  High security and reliability

   -  Both system disks and data disks support data encryption to ensure data security.
   -  Data protection functions, such as backups and snapshots, safeguard the disk data, preventing incorrect data caused by application exceptions or attacks.

-  Real-time monitoring

   On Cloud Eye, you can monitor the disk health and operating status at any time.

Differences Among EVS, SFS, and OBS
-----------------------------------

Currently, there are three data storage services available for you to choose from: EVS, Scalable File Service (SFS), and Object Storage Service (OBS). The differences are described in the following table.

.. table:: **Table 1** Differences among EVS, SFS, and OBS

   +-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------+
   | Service         | Overall Introduction                                                                                                                                                                                                                                | Typical Application Scenarios                                                           | Storage Capacity                                                                                                       |
   +=================+=====================================================================================================================================================================================================================================================+=========================================================================================+========================================================================================================================+
   | EVS             | EVS provides scalable block storage that features high reliability, high performance, and rich specifications for servers.                                                                                                                          | -  Enterprise office applications                                                       | EVS disks start at 10 GB and can be expanded as required in 1 GB increments to up to 32 TB.                            |
   |                 |                                                                                                                                                                                                                                                     | -  Development and testing                                                              |                                                                                                                        |
   |                 |                                                                                                                                                                                                                                                     | -  Enterprise applications, including SAP, Microsoft Exchange, and Microsoft SharePoint |                                                                                                                        |
   |                 |                                                                                                                                                                                                                                                     | -  Distributed file systems                                                             |                                                                                                                        |
   |                 |                                                                                                                                                                                                                                                     | -  Various databases, including MongoDB, Oracle, SQL Server, MySQL, and PostgreSQL      |                                                                                                                        |
   +-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------+
   | SFS             | SFS provides completely hosted sharable file storage for ECSs. Compatible with the Network File System (NFS) protocol, SFS is expandable to petabytes and seamlessly handles data-intensive and bandwidth-intensive applications.                   | -  HPC scenarios, such as gene sequencing, animation rendering, and CAD/CAE             | SFS storage capacity is available on demand and can be expanded to 10 PB at most.                                      |
   |                 |                                                                                                                                                                                                                                                     | -  File sharing                                                                         |                                                                                                                        |
   |                 |                                                                                                                                                                                                                                                     | -  Media processing                                                                     |                                                                                                                        |
   |                 |                                                                                                                                                                                                                                                     | -  Content management and web services                                                  |                                                                                                                        |
   |                 |                                                                                                                                                                                                                                                     | -  Offline file backup                                                                  |                                                                                                                        |
   +-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------+
   | OBS             | OBS provides cloud storage for unstructured data, such as files, pictures, and videos. With multiple options for migration to the cloud, OBS provides low-cost, reliable storage access for massive data and supports online multimedia processing. | -  Enterprise backup and archive                                                        | OBS provides limitless storage capacity, and storage resources are available for linear and nearly infinite expansion. |
   |                 |                                                                                                                                                                                                                                                     | -  Big data analysis                                                                    |                                                                                                                        |
   |                 |                                                                                                                                                                                                                                                     | -  Enterprise cloud box                                                                 |                                                                                                                        |
   |                 |                                                                                                                                                                                                                                                     | -  Static website hosting                                                               |                                                                                                                        |
   |                 |                                                                                                                                                                                                                                                     | -  Native cloud applications                                                            |                                                                                                                        |
   +-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------+

User Permissions
----------------

Users with resource management permissions can control the operations performed on cloud service resources. For EVS, a user with the Server Administrator permission can perform operations on EVS resources, including creating disks, deleting disks, and creating snapshots.

For details about user permissions, see `Permissions <https://docs.otc.t-systems.com/en-us/permissions/index.html>`__.

Project
-------

A project is used to group and isolate OpenStack resources, including compute, storage, and network resources. A project can be a department or a project team. You can access IAM with a security administrator to create projects in a region and perform isolated management of resources. For details about projects, see `Managing Projects <https://docs.otc.t-systems.com/en-us/usermanual/iam/en-us_topic_0066738518.html>`__.
