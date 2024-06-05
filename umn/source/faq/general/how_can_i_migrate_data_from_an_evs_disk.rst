:original_name: evs_faq_0059.html

.. _evs_faq_0059:

How Can I Migrate Data from an EVS Disk?
========================================

Data migration involves the following scenarios:

-  Cross-AZ data migration: Disk data can be migrated from one AZ to another through disk backups. You can create backups for your disks using the CBR service, and then use these backups to create new disks in the target AZ. For details, see sections "Creating a Cloud Disk Backup" and "Using a Backup to Create a Disk" in the *Cloud Backup and Recovery User Guide*.
-  Cross-region data migration: You can create a data disk image from the data disk in the current region and replicate the image to the other region. Then you can use the data disk image to create data disks in that other region. For details, see section "Creating a Data Disk Image from an ECS" in the *Image Management Service User Guide*.
-  Cross-account data migration: You can create a data disk image from the data disk under one account and then share the image with another account. Then you can use the data disk image under that second account to create data disks. For details, see section "Creating a Data Disk Image from an ECS" in the *Image Management Service User Guide*.
