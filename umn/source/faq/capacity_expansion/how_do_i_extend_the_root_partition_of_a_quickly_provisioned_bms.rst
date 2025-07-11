:original_name: evs_faq_0082.html

.. _evs_faq_0082:

How Do I Extend the Root Partition of a Quickly Provisioned BMS?
================================================================

Scenarios
---------

If the root partition of your quickly provisioned BMS is too small, extend the root partition by referring to the following procedure.

This example uses CentOS 7.3 and system disk, **/dev/sdf**. The way you allocate additional space depends on the OS. This example is used for reference only. For detailed operations and differences, see the corresponding OS documents.

In this example, the initial size of the BMS system disk (**sdf**) is 40 GiB and needs to be expanded to 140 GiB. The initial disk partitions are as follows:

|image1|

Procedure
---------

#. Log in to the EVS console and expand the system disk capacity to 140 GiB.

#. Log in to the BMS and run the following command to view the system disk capacity:

   **lsblk**

   Information similar to the following is displayed:

   |image2|

   The system disk (**sdf**) has been expanded from 40 GiB to 140 GiB. The **sdf4** partition (64 MiB) is the configdriver partition that stores the BMS configuration information.

#. Run the following command to back up the configdriver partition:

   **dd if=/dev/sdf4 of=/root/configdriver.img**

   Information similar to the following is displayed:

   |image3|

#. Run the following command and delete the configdriver partition:

   **fdisk /dev/sdf**

   |image4|

#. Run the **partprobe** command to update the partition information.

   If partition configdriver has been deleted, information similar to the following is displayed:

   |image5|

#. Recreate the configdriver partition with 100 MB.

   If the available sectors range from 83755008 to 293601279, set 293401279 (293601279 - 200000) as the new partition's start sector and 293601279 (default value) as the end sector.

   |image6|

   Run the **partprobe** command to update the partition information.

   |image7|

#. Run the following command to extend the root partition:

   **growpart /dev/sdf 3**

   Information similar to the following is displayed:

   |image8|

   Run the **lsblk** command to view the new root partition size.

   |image9|

#. Run the following command to extend the file system of the root partition:

   **resize2fs /dev/sdf3**

   Information similar to the following is displayed:

   |image10|

#. Run the following command to restore the content of the configdriver partition:

   **dd if=/root/configdriver.img of=/dev/sdf4**

   Information similar to the following is displayed:

   |image11|

   |image12|

   The root partition of the quickly provisioned BMS has been extended.

.. |image1| image:: /_static/images/en-us_image_0000002183122749.png
.. |image2| image:: /_static/images/en-us_image_0000002147881898.png
.. |image3| image:: /_static/images/en-us_image_0000002183201105.png
.. |image4| image:: /_static/images/en-us_image_0000002147723794.png
.. |image5| image:: /_static/images/en-us_image_0000002183122753.png
.. |image6| image:: /_static/images/en-us_image_0000002147881902.png
.. |image7| image:: /_static/images/en-us_image_0000002183201109.png
.. |image8| image:: /_static/images/en-us_image_0000002147723798.png
.. |image9| image:: /_static/images/en-us_image_0000002147881910.png
.. |image10| image:: /_static/images/en-us_image_0000002183201117.png
.. |image11| image:: /_static/images/en-us_image_0000002147723818.png
.. |image12| image:: /_static/images/en-us_image_0000002183122769.png
