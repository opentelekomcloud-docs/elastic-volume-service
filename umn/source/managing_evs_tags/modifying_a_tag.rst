:original_name: evs_01_0015.html

.. _evs_01_0015:

Modifying a Tag
===============

Scenarios
---------

You can change the value of a tag for an existing disk, but cannot change the key of a tag.

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

Constraints
-----------

-  You can add a maximum of 10 tags for a single EVS disk.
-  Tag keys of the same EVS disk must be unique.

Procedure
---------

#. Sign in to the console.

#. Click |image1| in the upper left corner and select the desired region and project.

#. Choose **Storage** > **Elastic Volume Service**.

   The **Elastic Volume Service** page is displayed.

#. In the disk list, locate the desired disk and click the disk name.

   The disk details page is displayed.

#. Click the **Tags** tab.

#. Locate the target tag and click **Edit** in the **Operation** column.

   The **Edit Tag** page is displayed.

#. Change the value of the tag and click **OK**.

   Return to the tag list. If the tag value is changed, the modification is complete.

.. |image1| image:: /_static/images/en-us_image_0237893718.png
