:original_name: evs_01_0067.html

.. _evs_01_0067:

Recovering Disks from the Recycle Bin
=====================================

Scenarios
---------

During routine data management, you may accidentally delete important disk data, resulting in data loss. When the recycle bin is enabled, deleted disks are moved to the recycle bin to prevent data loss.

Constraints
-----------

-  If your account is restricted, disks in the recycle bin cannot be recovered.

Procedure
---------

#. Sign in to the console.

#. Click |image1| in the upper left corner and select a region.

#. Click |image2| in the upper left corner and choose **Storage** > **Elastic Volume Service**.

   The **Elastic Volume Service** page is displayed.

#. Click the **Recycle Bin** tab.

#. On the **Recycle Bin** tab page, locate the disk you want to recover and click **Recover** in the **Operation** column.

   The **Recover Disk** page is displayed.


   .. figure:: /_static/images/en-us_image_0000002799149185.png
      :alt: **Figure 1** Recover Disk

      **Figure 1** Recover Disk

#. Click **Submit**.

   -  If the recovery succeeds, the disk will be displayed in the disk list, and the disk status is **Available**.
   -  If the recovery fails, the disk remains in the recycle bin, and the disk status changes to **Recovery failed**.

.. |image1| image:: /_static/images/en-us_image_0237893718.png
.. |image2| image:: /_static/images/en-us_image_0000001933286285.jpg
