:original_name: evs_01_0060.html

.. _evs_01_0060:

EVS Replication Operation Procedure (Deprecated)
================================================

For the EVS replication concepts, see :ref:`EVS Replication (Deprecated) <evs_01_0020>`. This chapter describes the basic functions and operations of EVS replication. :ref:`Figure 1 <evs_01_0060__en-us_topic_0129841799_en-us_topic_0080271663_fig1868775620529>` shows the operation procedure.

#. Performing pre-configuration operations before using EVS replication: Create DR servers, configure the virtual IP address for servers, and collect server information.

#. Creating EVS replication pairs: Specify production disks in the primary AZ and DR disks in the secondary AZ to create EVS replication pairs.

#. Creating replication consistency groups: Specify EVS replication pairs to create replication consistency groups.

#. After EVS replication pairs and replication consistency groups are created, you can perform the following operations as required:

   -  Updating a replication consistency group:

      a. Pause the replication consistency group if the group status is not paused.
      b. Add or remove EVS replication pairs from the replication consistency group.
      c. Synchronize the data in EVS replication pairs of the replication consistency group.

   -  Performing a planned migration: Switch the secondary AZ to the primary AZ and enable resources such as the DR servers and DR disks in the secondary AZ.
   -  Performing a failover:

      a. If a fault occurred in the primary AZ, switch the secondary AZ to the primary AZ and enable the resources such as the DR servers and DR disks in the secondary AZ.
      b. After the fault in the faulty AZ has been restored, reprotect the replication consistency group to enable the restored resources in the faulty AZ to function as DR servers and DR disks.

   -  Expanding EVS disks in a replication consistency group: Expand EVS disks in one or multiple EVS replication pairs of the replication consistency group.

   .. _evs_01_0060__en-us_topic_0129841799_en-us_topic_0080271663_fig1868775620529:

   .. figure:: /_static/images/en-us_image_0000002301567706.png
      :alt: **Figure 1** Operation procedure (EVS replication)

      **Figure 1** Operation procedure (EVS replication)

   .. note::

      EVS replication APIs have been deprecated. If you need to use the replication function, see `Storage Disaster Recovery Service User Guide <https://docs.otc.t-systems.com/en-us/usermanual/sdrs/en-us_topic_0125068221.html>`__ and `Storage Disaster Recovery Service API Reference <https://docs.otc.t-systems.com/en-us/api/sdrs/sdrs_01_0000.html>`__.
