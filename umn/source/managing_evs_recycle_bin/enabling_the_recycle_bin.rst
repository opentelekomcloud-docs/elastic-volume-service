:original_name: evs_01_0065.html

.. _evs_01_0065:

Enabling the Recycle Bin
========================

Scenarios
---------

EVS recycle bin is disabled by default. You need to manually enable it before you can use it.

If the recycle bin is enabled, EVS disks will be moved to the recycle bin upon deletion. This can help protect your disk data from accidental deletions.

Constraints
-----------

-  To learn when EVS disks will be moved to the recycle bin after the recycle bin is enabled, see :ref:`Recycle Bin Rules for Deleted EVS Disks <evs_01_0100__en-us_topic_0000001338775981_en-us_topic_0000001268924210_section10599940534>`.
-  There are no limits on the capacity and quantity of disks in the recycle bin.
-  By default, disks created at least 7 days ago are moved to the recycle bin when unsubscribed. You can customize the value, up to a maximum of 1,000 days.
-  By default, disks in the recycle bin are retained for 7 days, and the maximum retention period is 365 days.

Procedure
---------

#. Sign in to the console.

#. Click |image1| in the upper left corner and select a region.

#. Click |image2| in the upper left corner and choose **Storage** > **Elastic Volume Service**.

   The **Elastic Volume Service** page is displayed.

#. Click the **Recycle Bin** tab.

#. On the **Recycle Bin** tab, click **Enable Recycle Bin** to open the **Configure Recycle Bin Policy** page.


   .. figure:: /_static/images/en-us_image_0000002799013147.png
      :alt: **Figure 1** Enabling the recycle bin

      **Figure 1** Enabling the recycle bin

#. Configure the recycle bin policy.


   .. figure:: /_static/images/en-us_image_0000002810724789.png
      :alt: **Figure 2** Configuring the recycle bin policy

      **Figure 2** Configuring the recycle bin policy

   .. table:: **Table 1** Recycle bin policy parameters

      +--------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                            | Example Value         | Description                                                                                                                                                                                                                                  |
      +======================================+=======================+==============================================================================================================================================================================================================================================+
      | Number of days since disk creation   | 1                     | The disk age threshold for moving a deleted disk to the recycle bin. If a disk has existed longer than this value when you delete it, it is moved to the recycle bin.                                                                        |
      |                                      |                       |                                                                                                                                                                                                                                              |
      |                                      |                       | For example, if you set this parameter to **1**, deleting a disk created less than 1 day ago permanently deletes it, and deleting a disk created more than 1 day ago moves it to the recycle bin, where it is billed on a pay-per-use basis. |
      +--------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Number of days disks can be retained | 10                    | How long a disk stays in the recycle bin. When a disk has been in the recycle bin longer than this value, it is automatically deleted.                                                                                                       |
      |                                      |                       |                                                                                                                                                                                                                                              |
      |                                      |                       | For example, if you set this parameter to **10** days, a disk is kept in the recycle bin for up to 10 days, and then it is permanently deleted and cannot be recovered.                                                                      |
      +--------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**. Deleted or unsubscribed disks that meet the recycle bin policy will be displayed on the **Recycle Bin** tab.

Related Operations
------------------

-  You can :ref:`disable <evs_01_0066>` the recycle bin if you no longer need it.
-  You can customize how many days after disk creation the disks will be moved to the recycle bin when deleted. For details, see :ref:`Configuring a Recycle Bin Policy <evs_01_0203>`.

.. |image1| image:: /_static/images/en-us_image_0237893718.png
.. |image2| image:: /_static/images/en-us_image_0000001933286285.jpg
