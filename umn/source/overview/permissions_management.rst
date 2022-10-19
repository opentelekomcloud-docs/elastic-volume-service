:original_name: evs_01_0086.html

.. _evs_01_0086:

Permissions Management
======================

If you need to assign different permissions to employees in your enterprise to access your EVS resources, IAM is a good choice for fine-grained permissions management. IAM provides identity authentication, permissions management, and access control, helping you secure access to your cloud resources.

With IAM, you can use your cloud account to create IAM users for your employees, and assign permissions to the users to control their access to specific resource types. For example, some management personnel in your enterprise need to view EVS resources but should not be allowed to delete the resources or perform any high-risk operations. In this scenario, you can create IAM users for the management personnel and grant them only the permissions required for viewing EVS resources.

If your account does not need individual IAM users for permissions management, you may skip this chapter.

IAM can be used free of charge. You pay only for the resources in your account. For more information about IAM, see section "Service Overview" in the *Identity and Access Management User Guide*.

EVS Permissions
---------------

By default, new IAM users do not have permissions assigned. You need to add a user to one or more groups, and attach permissions policies or roles to these groups. Users inherit permissions from the groups to which they are added and can perform specified operations on cloud services based on the permissions.

EVS is a project-level service deployed and accessed in specific physical regions. To assign EVS permissions to a user group, specify the scope as region-specific projects and select projects for the permissions to take effect. If **All projects** is selected, the permissions will take effect for the user group in all region-specific projects. When accessing EVS, the users need to switch to a region where they have been authorized to use this service. When accessing EVS, users need to switch to a region where they have been authorized to use EVS.

You can grant users permissions by using roles and policies.

-  Roles: A type of coarse-grained authorization mechanism that defines permissions related to user responsibilities. This mechanism provides only a limited number of service-level roles for authorization. When using roles to grant permissions, you need to also assign other roles on which the permissions depend to take effect. However, roles are not an ideal choice for fine-grained authorization and secure access control.
-  Policies: A type of fine-grained authorization mechanism that defines permissions required to perform operations on specific cloud resources under certain conditions. This mechanism allows for more flexible policy-based authorization, meeting requirements for secure access control. For example, you can grant ECS users only the permissions for managing a certain type of ECSs. Most policies define permissions based on APIs. For the API actions supported by EVS, see section "Permissions Policies and Supported Actions" in the *Elastic Volume Service API Reference*.

:ref:`Table 1 <evs_01_0086__table481412518317>` lists all the system-defined roles and policies supported by EVS.

.. _evs_01_0086__table481412518317:

.. table:: **Table 1** System-defined roles and policies supported by EVS

   +----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+------------+
   | Role/Policy Name     | Description                                                                                                                                              | Type                  | Dependency |
   +======================+==========================================================================================================================================================+=======================+============+
   | EVS FullAccess       | Full permissions for EVS. Users granted these permissions can create, attach, detach, query, and delete EVS resources, and expand capacity of EVS disks. | System-defined policy | None       |
   +----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+------------+
   | EVS ReadOnlyAccess   | Read-only permissions for EVS. Users granted these permissions can view EVS resource data only.                                                          | System-defined policy | None       |
   +----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+------------+
   | Server Administrator | Full permissions for EVS                                                                                                                                 | System role           | None       |
   +----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+------------+

.. note::

   The **EVS Admin** and **EVS FullAccess** roles have the same permissions, and **EVS Admin** will be deprecated later. The **EVS Viewer** and **EVS ReadOnlyAccess** roles have the same permissions, and **EVS Viewer** will be deprecated later.

:ref:`Table 2 <evs_01_0086__table470371811355>` lists the common operations supported by each system-defined policy or role of EVS. Select the policies or roles as required.

.. _evs_01_0086__table470371811355:

.. table:: **Table 2** Common operations supported by each system-defined policy or role of EVS

   ============================= ============== ==================
   Operation                     EVS FullAccess EVS ReadOnlyAccess
   ============================= ============== ==================
   Creating disks                Y              x
   Viewing disk list             Y              Y
   Viewing disk details          Y              Y
   Attaching disks               Y              x
   Detaching disks               Y              x
   Deleting disks                Y              x
   Expanding disk capacities     Y              x
   Creating snapshots            Y              x
   Deleting snapshots            Y              x
   Rolling back snapshot data    Y              x
   Creating disks from snapshots Y              x
   Adding tags for disks         Y              x
   Modifying tags                Y              x
   Deleting tags                 Y              x
   Searching for disks by tag    Y              Y
   ============================= ============== ==================
