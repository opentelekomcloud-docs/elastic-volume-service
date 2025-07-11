:original_name: evs_02_0010.html

.. _evs_02_0010:

How Do I Clean Up My Disk Space on a Windows Server?
====================================================

Scenarios
---------

When the EVS disk space on a server is insufficient, the server running speed will be affected, which will further affect user experience. You can clean up the disk space using either of the following methods:

-  :ref:`Cleaning Up Disk Space Using the System Built-in Cleanup Tool <evs_02_0010__en-us_topic_0000001878349930_section8667185543115>`

The following example uses a Windows Server 2016 server to illustrate how to clean up disk space on a server. In addition, you are advised to do the following to save disk space:

-  Periodically compress and save the files that are not frequently used.
-  Periodically use the disk cleanup tool to clean up disk space, delete unnecessary files, and clean up the recycle bin.
-  Uninstall unnecessary programs to release disk space.

.. _evs_02_0010__en-us_topic_0000001878349930_section8667185543115:

Cleaning Up Disk Space Using the System Built-in Cleanup Tool
-------------------------------------------------------------

#. On the server desktop, click the start icon in the lower left corner.

   The start menu is displayed.

#. In the navigation pane on the left, choose **Windows Administrative Tools** > **Disk Cleanup**.

   The **Disk Cleanup: Drive Selection** window is displayed.


   .. figure:: /_static/images/en-us_image_0137059230.png
      :alt: **Figure 1** Disk Cleanup: Drive Selection

      **Figure 1** Disk Cleanup: Drive Selection

#. Select the target disk from the drop-down list. In this example, disk (C:) is selected.

   The **Disk Cleanup** window is displayed, and the system automatically calculates the space that can be freed on disk (C:).


   .. figure:: /_static/images/en-us_image_0137060651.png
      :alt: **Figure 2** Disk Cleanup

      **Figure 2** Disk Cleanup

#. After the automatic calculation is complete, select the files to be deleted on the displayed window and click **OK**.

   A confirmation dialog box is displayed.


   .. figure:: /_static/images/en-us_image_0137061042.png
      :alt: **Figure 3** Deletion confirmation

      **Figure 3** Deletion confirmation

#. Click **Delete Files** to clean up the disk space.

Uninstalling Unnecessary Programs on Control Panel
--------------------------------------------------

#. On the server desktop, click the start icon in the lower left corner.

   The start menu is displayed.

#. In the navigation pane on the left, choose **Windows System** > **Control Panel**.

   The **All Control Panel Items** window is displayed.


   .. figure:: /_static/images/en-us_image_0137062325.png
      :alt: **Figure 4** All Control Panel Items

      **Figure 4** All Control Panel Items

#. In the list, select **Programs and Features**.

   The **Programs and Features** window is displayed.


   .. figure:: /_static/images/en-us_image_0137062384.png
      :alt: **Figure 5** Programs and Features

      **Figure 5** Programs and Features

#. In the program list, right-click the program to be uninstalled and choose **Uninstall** from the shortcut menu.

   A confirmation dialog box is displayed.


   .. figure:: /_static/images/en-us_image_0137062392.png
      :alt: **Figure 6** Uninstallation confirmation

      **Figure 6** Uninstallation confirmation

#. Click **Yes** to uninstall the program.
