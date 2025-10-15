:original_name: evs_03_0001.html

.. _evs_03_0001:

Overview
========

This document describes how to call the Elastic Volume Service (EVS) APIs to use various EVS functions.

This chapter describes the concepts related to EVS to help you quickly understand the service.

Elastic Volume Service
----------------------

EVS offers scalable block storage for cloud servers. With high reliability, high performance, and a variety of specifications, EVS disks can be used for distributed file systems, development and test environments, data warehouses, and high-performance computing (HPC) applications.

EVS disks are sometimes just referred to as disks in this document.

.. _evs_03_0001__section394673794715:

Basic Concepts
--------------

-  Region

   A region is a physical data center, which is completely isolated to improve fault tolerance and stability. After a resource is created, its region cannot be changed.

-  AZ

   An availability zone (AZ) is a physical location where resources use independent power supplies and networks. A region contains one or more AZs that are physically isolated but interconnected through internal networks. Because AZs are isolated from each other, any fault that occurs in an AZ will not affect other AZs.

-  Project

   A project is used to group and isolate OpenStack resources, such as computing, storage, and network resources. A project can either be a department or a project team. You can access the Identity and Access Management (IAM) service with a security administrator to create projects in a region and perform isolated management of resources.

-  Image

   An image must contain an OS and can also contain application software (such as database software) and software configuration.

   Images can be public or private. Public images are provided by the system by default, and private images are manually created by users. You can create system disks using a public or private image.

-  EVS snapshot

   An EVS snapshot is a complete copy or image of the disk data at a specific point in time. Snapshots can be used as a disaster recovery (DR) approach, and you can use snapshots to fully restore data to the time when the snapshot was taken.

-  EVS backup

   EVS disks are backed up using Cloud Backup and Recovery (CBR). You can create backups for your disks on the console without stopping servers. If data is lost or damaged due to virus invasions, accidental deletions, or software/hardware faults, you can use backups to restore data, guaranteeing your data integrity and security.
