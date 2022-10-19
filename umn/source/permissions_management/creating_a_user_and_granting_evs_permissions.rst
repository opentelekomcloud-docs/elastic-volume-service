:original_name: evs_01_0089.html

.. _evs_01_0089:

Creating a User and Granting EVS Permissions
============================================

This chapter describes how to use IAM to implement fine-grained permissions control for your EVS resources. With IAM, you can:

-  Create IAM users for employees based on your enterprise's organizational structure. Each IAM user will have their own security credentials for accessing EVS resources.
-  Grant only the permissions required for users to perform a specific task.
-  Entrust an account or cloud service to perform efficient O&M on your EVS resources.

If your account does not require individual IAM users, skip this chapter.

This section describes the procedure for granting permissions (see :ref:`Figure 1 <evs_01_0089__fig15451536531>`).

Prerequisites
-------------

Learn about the permissions (see section "Permissions Management" in the *Elastic Volume Service User Guide*) supported by EVS and choose policies or roles according to your requirements.

Process Flow
------------

.. _evs_01_0089__fig15451536531:

.. figure:: /_static/images/en-us_image_0171882862.png
   :alt: **Figure 1** Process for granting EVS permissions


   **Figure 1** Process for granting EVS permissions

#. .. _evs_01_0089__li10176121316284:

   Create a user group and assign permissions to it.

   Create a user group on the IAM console, and attach the **EVS ReadOnlyAccess** policy to the group.

#. .. _evs_01_0089__li181761413162818:

   Create a user and add it to a user group.

   Create a user on the IAM console and add the user to the group created in :ref:`1 <evs_01_0089__li10176121316284>`.

#. Log in and verify permissions.

   Log in to the EVS console by using the user created in :ref:`2 <evs_01_0089__li181761413162818>`, and verify that the user only has read permissions for EVS.

   -  In **Service List**, choose **Elastic Volume Service**. On the EVS console, click **Create Disk** in the upper right corner. If a message appears indicating that you have insufficient permissions to perform the operation, the **EVS ReadOnlyAccess** policy has already taken effect.
   -  Choose any other service in **Service List**. If a message appears indicating that you have insufficient permissions to access the service, the **EVS ReadOnlyAccess** policy has already taken effect.
