:original_name: evs_faq_0061.html

.. _evs_faq_0061:

Can I Transfer the Data Disk Capacity to a System Disk?
=======================================================

Sorry, you cannot.

Currently, the capacity of an EVS disk cannot be transferred to another disk. Multiple EVS disks cannot be combined into a single, larger disk, either.

**Common Scenarios**

#. You want to expand the system disk capacity, but created a new data disk.
#. You want to expand the system disk capacity, but expanded the data disk capacity.

**Recommended Solution**

-  If you do not need the data on the data disk, you can just delete the data disk, and then :ref:`expand the system disk <evs_01_0059>`.
-  If you need the data on the data disk, you can create a small-capacity data disk, copy data from the original data disk to the new data disk, and then expand the system disk capacity.

   #. Back up the data disk using the CBR service or by creating a snapshot.

      For details about backups, see section "Managing EVS Backups" in the *Elastic Volume Service User Guide*. For details about snapshots, see :ref:`Creating an EVS Snapshot <evs_01_2721>`.

   #. Create a new data disk with the desired capacity and attach it to the server. After initializing the disk, copy the data from the original data disk to the new data disk.

   #. Confirm that the services on the new data disk are available. Then, delete the original data disk, and delete the created backup.

   #. Expand the system disk capacity by referring to :ref:`Expanding EVS Disk Capacity <evs_01_0059>`.
