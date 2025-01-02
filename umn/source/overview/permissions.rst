:original_name: evs_01_0086.html

.. _evs_01_0086:

Permissions
===========

If you need to assign different permissions to employees in your enterprise to access your EVS resources, IAM is a good choice for fine-grained permissions management. IAM provides identity authentication, permissions management, and access control, helping you securely access your cloud resources.

With IAM, you can control access to specific cloud resources. For example, if you want some resource management personnel in your enterprise to view EVS resources but do not want them to delete EVS resources or perform any other high-risk operations, you can grant permission to view EVS resources but not permission to delete them.

If your account does not require IAM for permissions management, you can skip this section.

IAM is a free service. You only pay for the resources in your account.

For more information about IAM, see `IAM Service Overview <https://docs.otc.t-systems.com/usermanual/iam/iam_01_0026.html>`__.

EVS Permissions
---------------

New IAM users do not have any permissions assigned by default. You need to first add them to one or more groups and attach policies or roles to these groups. The users then inherit permissions from the groups and can perform specified operations on cloud services based on the permissions they have been assigned.

EVS is a project-level service deployed for specific regions. To assign EVS permissions to a user group, specify the scope as region-specific projects and select a project for the permissions to take effect. If **All projects** is selected, the permissions will take effect for the user group in all region-specific projects. When accessing EVS, users need to switch to a region where they have been authorized to use EVS.

You can grant users permissions by using roles and policies.

-  Roles: A type of coarse-grained authorization mechanism that defines permissions related to user responsibilities. This mechanism provides only a limited number of service-level roles for authorization. When using roles to grant permissions, you need to also assign other roles on which the permissions depend to take effect. However, roles are not an ideal choice for fine-grained authorization and secure access control.
-  Policies: A type of fine-grained authorization mechanism that defines permissions required to perform operations on specific cloud resources under certain conditions. This mechanism allows for more flexible policy-based authorization, meeting requirements for secure access control. For example, you can grant ECS users only the permissions for managing a certain type of ECSs. Most policies define permissions based on APIs. For the API actions supported by EVS, see section "Permissions Policies and Supported Actions" in the *Elastic Volume Service API Reference*.

:ref:`Table 1 <evs_01_0086__en-us_topic_0171850870_table481412518317>` lists all the system-defined roles and policies supported by EVS.

.. _evs_01_0086__en-us_topic_0171850870_table481412518317:

.. table:: **Table 1** System-defined roles and policies supported by EVS

   +----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+------------+
   | Role/Policy Name     | Description                                                                                                                                              | Type                  | Dependency |
   +======================+==========================================================================================================================================================+=======================+============+
   | EVS FullAccess       | Full permissions for EVS. Users granted these permissions can create, attach, detach, query, and delete EVS resources, and expand capacity of EVS disks. | System-defined policy | None       |
   +----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+------------+
   | EVS ReadOnlyAccess   | Read-only permissions for EVS. Users granted these permissions can view EVS resource data only.                                                          | System-defined policy | None       |
   +----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+------------+
   | Server Administrator | Full permissions for EVS                                                                                                                                 | System-defined role   | None       |
   +----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+------------+

.. note::

   The **EVS Admin** and **EVS FullAccess** roles have the same permissions, and **EVS Admin** will be deprecated later. The **EVS Viewer** and **EVS ReadOnlyAccess** roles have the same permissions, and **EVS Viewer** will be deprecated later.

:ref:`Table 2 <evs_01_0086__en-us_topic_0171850870_table470371811355>` lists the common operations supported by each system-defined policy of EVS. Select the policies as required.

.. _evs_01_0086__en-us_topic_0171850870_table470371811355:

.. table:: **Table 2** Common operations supported by each system-defined policy of EVS

   ================================ ============== ==================
   Operation                        EVS FullAccess EVS ReadOnlyAccess
   ================================ ============== ==================
   Creating disks                   Y              x
   Viewing the disk list            Y              Y
   Viewing disk details             Y              Y
   Attaching disks                  Y              x
   Detaching disks                  Y              x
   Deleting disks                   Y              x
   Expanding disk capacities        Y              x
   Creating snapshots               Y              x
   Deleting snapshots               Y              x
   Rolling back data from snapshots Y              x
   Creating disks from snapshots    Y              x
   Adding tags for disks            Y              x
   Modifying tags                   Y              x
   Deleting tags                    Y              x
   Searching for disks by tag       Y              Y
   Changing disk names              Y              x
   ================================ ============== ==================

Helpful Links
-------------

-  `IAM Service Overview <https://docs.otc.t-systems.com/usermanual/iam/iam_01_0026.html>`__

-  :ref:`Creating a User and Granting EVS Permissions <evs_01_0089>`
-  "Permissions Policies and Supported Actions" in the *Elastic Volume Service API Reference*
