:original_name: evs_01_0056.html

.. _evs_01_0056:

EVS Three-Copy Redundancy
=========================

What Is the Three-Copy Redundancy?
----------------------------------

The backend storage system of EVS employs three-copy redundancy to guarantee data reliability. With this mechanism, one piece of data is by default divided into multiple 1 MiB data blocks. Each data block is saved in three copies, and these copies are stored on different nodes in the system according to the distributed algorithms.

Three-copy redundancy has the following characteristics:

-  The storage system saves the data copies on different disks of different servers across cabinets, ensuring that services are not interrupted if a physical device fails.
-  The storage system guarantees strong consistency between the data copies.

For example, for data block P1 on physical disk A of server A, the storage system backs up its data to P1'' on physical disk B of server B and to P1' on physical disk C of server C. Data blocks P1, P1', and P1'' are the three copies of the same data block. If physical disk A where P1 resides is faulty, P1' and P1'' can continue providing storage services, ensuring service continuity.


.. figure:: /_static/images/en-us_image_0205534009.png
   :alt: **Figure 1** Three-copy redundancy

   **Figure 1** Three-copy redundancy

How Does the Three-Copy Redundancy Keep Data Consistency?
---------------------------------------------------------

When an application writes a piece of data to the system, the three copies of the data in the storage system must be consistent. When any of the three copies is read by the application later, the data on this copy is consistent with the data previously written to it.

Three-copy redundancy keeps data consistency in the following ways:

-  Data is simultaneously written to the three copies of the data.

   When an application writes data, the storage system writes it to the three copies of the data simultaneously. In addition, the system returns the write success response to the application only after the data has been written to all of the three copies.

-  Storage system automatically restores the damaged copy in the event of a data read failure.

   When an application fails to read data, the system automatically identifies the failure cause. If the data cannot be read from a physical disk sector, the system reads the data from another copy of the data on another node and writes it back to the original disk sector. This ensures the correct number of data copies and data consistency among data copies.

How Does Three-Copy Redundancy Rapidly Rebuild Data?
----------------------------------------------------

Each physical disk in the storage system stores multiple data blocks, whose copies are scattered on the nodes in the system according to certain distribution rules. When a physical server or disk fault is detected, the storage system automatically rebuilds the data. Since the copies of data blocks are scattered on different nodes, the storage system will start the data rebuild on multiple nodes simultaneously during a data restore, with only a small amount of data on each node. In this way, the system eliminates the potential performance bottlenecks that may occur when a large amount of data needs to be rebuilt on a single node, and therefore minimizes the adverse impacts exerted on upper-layer applications.

:ref:`Figure 2 <evs_01_0056__en-us_topic_0127363626_fig5727201319315>` shows the data rebuild process.

.. _evs_01_0056__en-us_topic_0127363626_fig5727201319315:

.. figure:: /_static/images/en-us_image_0197133828.png
   :alt: **Figure 2** Data rebuild process

   **Figure 2** Data rebuild process

:ref:`Figure 3 <evs_01_0056__en-us_topic_0127363626_fig0545141175416>` shows the data rebuild principle. For example, if physical disks on server F are faulty, the data blocks on these physical disks will be rebuilt on the physical disks of other servers.

.. _evs_01_0056__en-us_topic_0127363626_fig0545141175416:

.. figure:: /_static/images/en-us_image_0205534122.png
   :alt: **Figure 3** Data rebuild principle

   **Figure 3** Data rebuild principle

What Are the Differences Between Three-Copy Redundancy, EVS Snapshots, and EVS Backups?
---------------------------------------------------------------------------------------

Three-copy redundancy improves the reliability of the data stored on EVS disks. It is used to tackle data loss or inconsistency caused by physical device faults.

EVS backups and EVS snapshots are used to prevent data loss or data inconsistency caused by incorrect operations, viruses, or hacker attacks. So you are advised to create backups or snapshots to back up the disk data on a timely basis.
