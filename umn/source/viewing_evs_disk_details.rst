:original_name: evs_01_0093.html

.. _evs_01_0093:

Viewing EVS Disk Details
========================

Scenarios
---------

This section describes how to view disk details, including the disk status and specifications. Two methods are as follows:

-  :ref:`Viewing Disk Details from the EVS Console <evs_01_0093__en-us_topic_0173687780_section242672414158>`
-  :ref:`Viewing Disk Details from the Cloud Server Console <evs_01_0093__en-us_topic_0173687780_section1558615712151>`

See :ref:`EVS Disk Status <evs_01_0093__en-us_topic_0173687780_section9662151014912>` to learn more about disk statuses.

.. _evs_01_0093__en-us_topic_0173687780_section242672414158:

Viewing Disk Details from the EVS Console
-----------------------------------------

#. Log in to the console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click |image2| in the upper left corner and choose **Storage** > **Elastic Volume Service**.

   The **Elastic Volume Service** page is displayed.

#. In the disk list, view disk information including the disk status, type, size, function, and device type.

   You can filter disks by project, status, disk name, or tag.


   .. figure:: /_static/images/en-us_image_0000001622204197.png
      :alt: **Figure 1** Viewing the disk list

      **Figure 1** Viewing the disk list

#. In the disk list, locate the desired disk and click the disk name.

   The disk details page is displayed for you to view the disk details.


   .. figure:: /_static/images/en-us_image_0000001571725570.png
      :alt: **Figure 2** Disk details page

      **Figure 2** Disk details page

#. (Optional) Export disk information.

   Click |image3| in the upper right corner of the list to export disk information.

.. _evs_01_0093__en-us_topic_0173687780_section1558615712151:

Viewing Disk Details from the Cloud Server Console
--------------------------------------------------

#. Log in to the console.

#. Click |image4| in the upper left corner and select the desired region and project.

#. Choose **Compute** > **Elastic Cloud Server**.

   The **Elastic Cloud Server** page is displayed.

#. In the server list, locate the desired server by server name and click the name.

   The server details page is displayed.

#. On the **Disks** tab, click |image5| in front of the row containing the target disk. In the unfolded area, click the disk ID.

   The disk details page is displayed for you to view the disk details.


   .. figure:: /_static/images/en-us_image_0000001571725570.png
      :alt: **Figure 3** Disk details page

      **Figure 3** Disk details page

.. _evs_01_0093__en-us_topic_0173687780_section9662151014912:

EVS Disk Status
---------------

.. table:: **Table 1** EVS disk status details

   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------+
   | Status                | Description                                                                                                                                      | Allowed Operation                                      |
   +=======================+==================================================================================================================================================+========================================================+
   | In-use                | The EVS disk has been attached to a server and is in use.                                                                                        | -  Detaching                                           |
   |                       |                                                                                                                                                  | -  Creating backups                                    |
   |                       |                                                                                                                                                  | -  Expanding capacity                                  |
   |                       |                                                                                                                                                  |                                                        |
   |                       |                                                                                                                                                  |    .. note::                                           |
   |                       |                                                                                                                                                  |                                                        |
   |                       |                                                                                                                                                  |       A shared **In-use** EVS disk can be attached.    |
   |                       |                                                                                                                                                  |                                                        |
   |                       |                                                                                                                                                  |       A shared **In-use** EVS disk cannot be expanded. |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------+
   | Available             | The EVS disk has not been attached to any server, so you can attach it.                                                                          | -  Attaching                                           |
   |                       |                                                                                                                                                  | -  Expanding capacity                                  |
   |                       |                                                                                                                                                  | -  Deleting                                            |
   |                       |                                                                                                                                                  | -  Creating backups                                    |
   |                       |                                                                                                                                                  | -  Rolling back data to EVS disks using snapshots      |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------+
   | Creating              | The EVS disk is being created.                                                                                                                   | ``-``                                                  |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------+
   | Attaching             | The EVS disk is being attached to a server.                                                                                                      | ``-``                                                  |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------+
   | Detaching             | The EVS disk is being detached from a server.                                                                                                    | ``-``                                                  |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------+
   | Deleting              | The EVS disk is being deleted.                                                                                                                   | ``-``                                                  |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------+
   | Restoring             | A backup is being used to restore the EVS disk.                                                                                                  | ``-``                                                  |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------+
   | Expanding             | The capacity of the EVS disk is being expanded.                                                                                                  | ``-``                                                  |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------+
   | Uploading             | Data on the EVS disk is being uploaded to an image. This status occurs when you create an image from a server.                                   | ``-``                                                  |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------+
   | Downloading           | Data is being downloaded from an image to the EVS disk. This status occurs when you create a server.                                             | ``-``                                                  |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------+
   | Error                 | An error occurs when you try to create an EVS disk.                                                                                              | Deleting                                               |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------+
   | Deletion failed       | An error occurs when you try to delete the EVS disk.                                                                                             | None                                                   |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------+
   | Expansion failed      | An error occurs when you try to expand the capacity of the EVS disk.                                                                             | Deleting                                               |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------+
   | Restoration failed    | An error occurs when you try to restore the EVS disk from a backup.                                                                              | Deleting                                               |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------+
   | Rolling back          | Data on the EVS disk is being restored from a snapshot.                                                                                          | ``-``                                                  |
   |                       |                                                                                                                                                  |                                                        |
   |                       | .. note::                                                                                                                                        |                                                        |
   |                       |                                                                                                                                                  |                                                        |
   |                       |    -  When you roll back data from a snapshot, you can only roll back data to the source EVS disk. Rollback to a specific disk is not supported. |                                                        |
   |                       |    -  A snapshot can only be used for rollback when its source disk is in the **Available** or **Rollback failed** state.                        |                                                        |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------+
   | Rollback failed       | An error occurs when the EVS disk data is rolled back from a snapshot.                                                                           | -  Deleting                                            |
   |                       |                                                                                                                                                  | -  Rolling back data to EVS disks using snapshots      |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------+
   | Awaiting transfer     | The EVS disk is awaiting for a transfer.                                                                                                         | ``-``                                                  |
   +-----------------------+--------------------------------------------------------------------------------------------------------------------------------------------------+--------------------------------------------------------+


.. figure:: /_static/images/en-us_image_0000001896813650.png
   :alt: **Figure 4** Change between some of EVS disk statuses

   **Figure 4** Change between some of EVS disk statuses

.. note::

   If an EVS disk status is **Error**, **Deletion failed**, **Expansion failed**, **Restoration failed**, or **Rollback failed**, you can rectify the error by referring to :ref:`What Should I Do If an Error Occurs on My EVS Disk? <evs_faq_0014>`

.. |image1| image:: /_static/images/en-us_image_0237893718.png
.. |image2| image:: /_static/images/en-us_image_0000001933286285.jpg
.. |image3| image:: /_static/images/en-us_image_0000001130404567.png
.. |image4| image:: /_static/images/en-us_image_0237893718.png
.. |image5| image:: /_static/images/en-us_image_0000001083456418.png
