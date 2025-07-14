:original_name: evs_01_0014.html

.. _evs_01_0014:

Adding a Tag
============

Scenarios
---------

You can add tags for an existing EVS disk. You can also add tags when creating a disk. For details, see :ref:`Creating an EVS Disk <en-us_topic_0021738346>`.

Tag Rules
---------

A tag consists of a tag key and a tag value. Tag rules are described as follows: (Tag rules vary depending on regions. See the rules displayed on the console.)

First set of rules:

-  A tag key can contain a maximum of 36 characters. It can contain only letters, digits, special characters (.-_), and Unicode characters.
-  A tag value can contain a maximum of 43 characters. It can contain only letters, digits, special characters (.-_), and Unicode characters.

Second set of rules:

-  A tag key can contain a maximum of 36 characters. It cannot contain special characters ``(=*<>\\,|/)`` or start or end with spaces.
-  A tag value can contain a maximum of 43 characters. It cannot contain special characters ``(=*<>\\,|/)`` or start or end with spaces.

Third set of rules:

-  A tag key can contain a maximum of 128 characters. It cannot contain special characters ``(*<>\\/,|),`` start with **\_sys\_**, or start or end with spaces.
-  A tag value can contain a maximum of 255 characters. It cannot contain special characters ``(*<>\\,|)`` or start or end with spaces.

Notes and Constraints
---------------------

-  You can add a maximum of 10tags for a single EVS disk.
-  Tag keys of the same EVS disk must be unique.

Procedure
---------

#. Log in to the console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Click |image2| in the upper left corner and choose **Storage** > **Elastic Volume Service**.

   The **Elastic Volume Service** page is displayed.

#. In the disk list, locate the desired disk and click the disk name.

   The disk details page is displayed.

#. Click the **Tags** tab.

#. Click **Add Tag**.

   The **Add Tag** page is displayed.

#. Enter a key and a value for a tag and click **OK**.

   -  Tag key: This parameter is mandatory.
   -  Tag value: This parameter is optional.

   The **Tags** tab is displayed, and you can view the newly added tag.

.. |image1| image:: /_static/images/en-us_image_0237893718.png
.. |image2| image:: /_static/images/en-us_image_0000001933286285.jpg
