:original_name: evs_01_0014.html

.. _evs_01_0014:

Adding a Tag
============

Scenarios
---------

You can add a tag for an existing EVS disk. You can also add tags during the disk creation. For details, see :ref:`Create an EVS Disk <en-us_topic_0021738346>`.

-  A tag is composed of a key-value pair.

   -  Key:

      -  Must be unique for each resource.
      -  Can contain a maximum of 36 characters.
      -  Can contain only digits, letters, hyphens (-), and underscores (_).

   -  Value:

      -  Can contain a maximum of 43 characters.
      -  Can contain only digits, letters, hyphens (-), and underscores (_).

-  A maximum of 10 tags can be added for an EVS disk.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Under **Storage**, click **Elastic Volume Service**.

   The disk list page is displayed.

#. In the disk list, locate the desired disk and click the disk name.

   The disk details page is displayed.

#. Click the **Tags** tab.

#. Click **Add Tag**.

   The **Add Tag** page is displayed.

#. Enter a key and a value for a tag and click **OK**.

   -  **Key**: This parameter is mandatory.
   -  **Value**: This parameter is optional.

   The **Tags** tab is displayed, and you can view the newly added tag.

.. |image1| image:: /_static/images/en-us_image_0237893718.png
