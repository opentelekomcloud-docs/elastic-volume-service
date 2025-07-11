:original_name: evs_01_0089.html

.. _evs_01_0089:

Creating a User and Granting EVS Permissions
============================================

You can use IAM for fine-grained permissions control for your EVS resources. With IAM, you can:

-  Create IAM users for personnel based on your enterprise's organizational structure. Each IAM user has their own identity credentials for accessing EVS resources.
-  Grant only the permissions required for users to perform a specific task.
-  Entrust an account or cloud service to perform efficient O&M on your EVS resources.

If your account does not require individual IAM users, you may skip over this section.

This section describes the procedure for granting permissions (see :ref:`Figure 1 <evs_01_0089__en-us_topic_0171882195_fig15451536531>`).

Prerequisites
-------------

Before granting permissions to user groups, learn about system-defined permissions in "Service Overview" > "Permissions" of the Elastic Volume Service.

Process Flow
------------

.. _evs_01_0089__en-us_topic_0171882195_fig15451536531:

.. figure:: /_static/images/en-us_image_0000002301562770.png
   :alt: **Figure 1** Process for granting EVS permissions

   **Figure 1** Process for granting EVS permissions

#. .. _evs_01_0089__en-us_topic_0171882195_li10176121316284:

   On the IAM console, create a user group and grant it permissions (**EVS ReadOnlyAccess** as an example).

#. Create an IAM user and add it to the created user group.

   Create a user on the IAM console and add the user to the group created in :ref:`1 <evs_01_0089__en-us_topic_0171882195_li10176121316284>`.

#. Log in as the IAM user and verify permissions.

   In the authorized region, perform the following operations:

   -  Choose **Service List** > **Elastic Volume Service**. Then click **Create Disk** on the EVS console. If a message appears indicating that you have insufficient permissions to perform the operation, the **EVS ReadOnlyAccess** policy is in effect.
   -  Choose another service from **Service List**. If a message appears indicating that you have insufficient permissions to access the service, the **EVS ReadOnlyAccess** policy is in effect.
