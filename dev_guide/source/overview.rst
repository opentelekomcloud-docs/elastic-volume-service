:original_name: evs_03_0001.html

.. _evs_03_0001:

Overview
========

This document describes how to call the Elastic Volume Service (EVS) APIs to use various EVS functions.

This chapter describes the concepts related to EVS to help you quickly understand the service.

Elastic Volume Service
----------------------

EVS offers scalable block storage for servers. With high reliability, high performance, and rich specifications, EVS disks can be used for distributed file systems, development and test environments, data warehouse applications, and high-performance computing (HPC) scenarios to meet diverse service requirements.

EVS disks are also referred to as disks in this document.

Basic Concepts
--------------

-  AZ

   An availability zone (AZ) is a physical location where resources use independent power supply and networks within a region. An AZ is insulated from failures in other AZs and provides inexpensive, low-latency network connectivity to other AZs in the same regions. A region can have more than one AZ. AZs are physically isolated but interconnected through an internal network.

-  Project

   A project is used to group and isolate OpenStack resources, such as computing, storage, and network resources. A project can either be a department or a project team. You can access the Identity and Access Management (IAM) service with a security administrator to create projects in a region and perform isolated management of resources.

-  Image

   An image must contain an OS and can also contain application software (such as database software) and software configuration.

   Images can be public or private. Public images are provided by the system by default, and private images are manually created by users. You can create system disks using a public or private image.

-  EVS snapshot

   An EVS snapshot is a complete copy or image of the disk data at a specific time point. As a major disaster recovery (DR) approach, you can use a snapshot to completely restore the data to the time point when the snapshot was created.

-  EVS disk backup

   The EVS implements the backup function through Cloud Backup and Recovery (CBR). CBR allows you to create backups for EVS disks on the management console without stopping the servers. When data loss or data damage occurred due to virus invasion, misoperations, or software and hardware faults, you can use backups to restore the data, maximizing your data correctness and security.
