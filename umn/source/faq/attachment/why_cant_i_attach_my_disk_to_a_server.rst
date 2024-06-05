:original_name: evs_faq_0025.html

.. _evs_faq_0025:

Why Can't I Attach My Disk to a Server?
=======================================

Symptom
-------

My disk cannot be attached to a server.

Troubleshooting
---------------

Possible causes are listed here in order of their probability.

If the fault persists after you have ruled out one cause, move on to the next one in the list.

.. table:: **Table 1** Troubleshooting

   +---------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Symptom                                                                   | Solution                                                                                                                                                                                        |
   +===========================================================================+=================================================================================================================================================================================================+
   | The target server on the **Attach Disk** page could not be found.         | -  Go to :ref:`Check Whether the Disk and Server Are in the Same AZ <evs_faq_0025__en-us_topic_0000001072682645_en-us_topic_0267670624_section83925230328>`.                                    |
   |                                                                           | -  Cloud servers created from ISO images are only used for OS installation. They have limited functions and cannot have EVS disks attached.                                                     |
   +---------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | The **Attach** button is grayed out.                                      | -  Go to :ref:`Maximum Number of Disks That Can Be Attached to the Server Has Been Reached <evs_faq_0025__en-us_topic_0000001072682645_en-us_topic_0267670624_section129621513133311>`.         |
   |                                                                           | -  Go to :ref:`Check Whether the Disk Has Been Added to a Replication Pair <evs_faq_0025__en-us_topic_0000001072682645_section4732195892910>`.                                                  |
   +---------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | An incorrect OS type warning is displayed when a shared disk is attached. | Go to :ref:`Check Whether the Servers Attached with the Shared Disk Are Running the Same Type of OS <evs_faq_0025__en-us_topic_0000001072682645_en-us_topic_0267670624_section19691130175413>`. |
   +---------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _evs_faq_0025__en-us_topic_0000001072682645_en-us_topic_0267670624_section83925230328:

Check Whether the Disk and Server Are in the Same AZ
----------------------------------------------------

**Symptom**: After you click **Attach**, the target server cannot be found on the **Attach Disk** page.

**Solution**: A disk can only be attached to a server in the same AZ and region. The **Attach Disk** page filters and shows all the servers that the disk can be attached to. Determine whether your disk data is required.

-  If the disk data is no longer needed, delete the disk, and then create a new disk in the AZ where your target server is located.
-  If the disk data is still required, create a new disk with the same data in the target AZ. The procedure is as follows:

   #. Create a backup for the disk.


      .. figure:: /_static/images/en-us_image_0000001622372417.png
         :alt: **Figure 1** Create Backup

         **Figure 1** Create Backup

   #. Create a new disk from this backup. During the creation, select the target AZ. You can also change the settings of **Disk Type** and **Advanced Settings** if needed.


      .. figure:: /_static/images/en-us_image_0000001572095150.png
         :alt: **Figure 2** Create from backup

         **Figure 2** Create from backup

   #. After the disk is created, click **Attach**. Your target server is displayed on the **Attach Disk** page.

.. _evs_faq_0025__en-us_topic_0000001072682645_en-us_topic_0267670624_section129621513133311:

Maximum Number of Disks That Can Be Attached to the Server Has Been Reached
---------------------------------------------------------------------------

**Symptom**: The **Attach** button is grayed out.

**Solution**:

-  Non-shared disk: When you hover the mouse over the **Attach** button, message "This operation can be performed only when the disk is in the Available state" is displayed.

   A non-shared disk can only be attached to one server. If the disk status is **In-use**, the disk has been attached. You can detach the disk, wait until the disk status changes to **Available**, and then attach the disk to the target server.

-  Shared disk: When you hover the mouse over the **Attach** button, message "This operation cannot be performed because the maximum number of servers that a shared disk can be attached to has been reached" is displayed.

   A shared disk can be attached to a maximum of 16 servers, but you can detach the shared disk from one server and attach it to a new one if needed.

.. _evs_faq_0025__en-us_topic_0000001072682645_section4732195892910:

Check Whether the Disk Has Been Added to a Replication Pair
-----------------------------------------------------------

**Symptom**: The **Attach** button is grayed out. When you hover the mouse over the **Attach** button, message "This operation cannot be performed on a disk in a replication pair" is displayed.

**Solution**: Delete the replication pair and attach the disk again.

#. Choose **Storage** > **Storage Disaster Recovery Service**.

   The **Storage Disaster Recovery Service** page is displayed.

#. Locate the protection group containing the disk and click the protection group name.

   The protection group details page is displayed.

#. Click the **Replication Pairs** tab.

   Check that the disk in the **Production Site Disk** column is the target disk.

#. Confirm the information and click **Delete** in the **Operation** column.

#. After the replication pair is deleted, return to the disk list, and the disk can be attached.

.. _evs_faq_0025__en-us_topic_0000001072682645_en-us_topic_0267670624_section19691130175413:

Check Whether the Servers Attached with the Shared Disk Are Running the Same Type of OS
---------------------------------------------------------------------------------------

**Symptom**: After you click **Attach**, the target server cannot be selected on the **Attach Disk** page, and message "A shared disk must be attached to servers with the same OS type" is displayed.

**Solution**: This message indicates that the OS type of the target server is inconsistent with that of the servers attached with the shared disk. You can change the OS type based your service requirements.
