:original_name: evs_01_0203.html

.. _evs_01_0203:

Configuring a Recycle Bin Policy
================================

Scenarios
---------

After enabling the recycle bin, you can define a recycle bin policy to determine when deleted disks are moved to the bin.

.. note::

   If you have configured scaling policies for your workloads, the system may frequently delete EVS disks. At the same time, if you have also enabled EVS recycle bin, but do not want these frequently deleted disks to be moved to the bin, you can configure an appropriate recycle bin policy to reduce unintended costs.

   Example scenarios:

   -  Scenario 1: You have used Auto Scaling to dynamically scale services. The system may frequently delete disks based on the configured scaling policy.
   -  Scenario 2: You have used Cloud Container Engine (CCE) to run workloads. The system may frequently delete disks based on the configured container scaling policy.

   These examples are for your reference only. You can configure an appropriate policy based on your own service scenario.

Constraints
-----------

-  By default, disks created at least 7 days ago are moved to the recycle bin when unsubscribed. You can customize the value, up to a maximum of 1,000 days.
-  By default, disks in the recycle bin are retained for 7 days, and the maximum retention period is 365 days.
-  When the OS of a server is reinstalled, a new system disk will be created to replace the original one. EVS determines whether to move the original disk to the recycle bin by comparing the number of days passed since disk creation with the days configured in the recycle bin policy.

Procedure
---------

#. Sign in to the console.

#. Click |image1| in the upper left corner and select a region.

#. Click |image2| in the upper left corner and choose **Storage** > **Elastic Volume Service**.

   The **Elastic Volume Service** page is displayed.

#. Click the **Recycle Bin** tab.

#. In the upper right corner of the **Recycle Bin** tab page, click **Modify Policy**.

   The **Configure Recycle Bin Policy** page is displayed.

#. Configure the recycle bin policy.


   .. figure:: /_static/images/en-us_image_0000002810724789.png
      :alt: **Figure 1** Configuring the recycle bin policy

      **Figure 1** Configuring the recycle bin policy

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

#. Click **OK**. Disks that you delete afterward are handled according to this policy: moved to the recycle bin and permanently deleted when they expire.

Related Operations
------------------

You can manually :ref:`recover <evs_01_0067>` or :ref:`permanently delete <evs_01_0068>` disks in the recycle bin.

.. |image1| image:: /_static/images/en-us_image_0237893718.png
.. |image2| image:: /_static/images/en-us_image_0000001933286285.jpg
