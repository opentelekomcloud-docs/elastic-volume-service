:original_name: evs_04_0023.html

.. _evs_04_0023:

Introduction
============

This chapter describes fine-grained permissions management for your EVS resources. If your account does not need individual IAM users, you can skip this chapter.

By default, new IAM users do not have permissions assigned. You need to add a user to one or more groups, and attach permissions policies or roles to these groups. Users inherit permissions from the groups to which they are added and can perform specified operations on cloud services based on the permissions.

You can grant users permissions by using roles and policies. Roles are a type of coarse-grained authorization mechanism that defines permissions related to user responsibilities. Policies define API-based permissions for operations on specific resources under certain conditions, allowing for more fine-grained, secure access control of cloud resources.

.. note::

   Policy-based authorization is useful if you want to allow or deny the access to an API.

An account has all the permissions required to call all APIs, but IAM users must be assigned the required permissions. The permissions required for calling an API are determined by the actions supported by the API. Only users who have been granted permissions allowing the actions can call the API successfully. For example, if an IAM user queries EVS disks using an API, the user must have been granted permissions that allow the **evs:volumes:list** action.

Supported Actions
-----------------

EVS provides system-defined policies that can be directly used in IAM. You can also create custom policies and use them to supplement system-defined policies, implementing more refined access control. Operations supported by policies are specific to APIs. The following are common concepts related to policies:

-  Permission: A statement in a policy that allows or denies certain operations.
-  API: REST APIs that can be called by a user who has been granted specific permissions.
-  Action: Specific operations that are allowed or denied.
-  Dependent actions: When assigning an action to users, you also need to assign dependent permissions for that action to take effect.
-  IAM projects: Type of projects for which an action will take effect.

EVS supports the following actions that can be defined in custom policies:

-  API version query actions (:ref:`API Version Query <evs_04_0024>`), including actions supported by EVS version query APIs, such as the APIs for querying API versions.
-  Disk actions (:ref:`Disk <evs_04_0025>`), including actions supported by EVS disk APIs, such as the APIs for creating a disk, querying disks, deleting a disk, and updating a disk.
-  Actions of disk actions (:ref:`Disk Action <evs_04_0026>`), including actions supported by EVS disk actions, such as the APIs for expanding the capacity of a disk, exporting a disk as an image, and setting read-only flag for a disk.
-  Snapshot actions (:ref:`Snapshot <evs_04_0027>`), including actions supported by EVS snapshot APIs, such as the APIs for creating a snapshot, querying snapshots, updating a snapshot, and deleting a snapshot.
-  Tag actions (:ref:`Tag <evs_04_0028>`), including actions supported by EVS tag APIs, such as the APIs for deleting tags by key, batch adding tags, batch deleting tags, and querying tags.
-  Disk transfer actions (:ref:`Disk Transfer <evs_04_0029>`), including actions supported by EVS disk transfer APIs, such as the APIs for creating a disk transfer, querying disk transfers, accepting a disk transfer, and deleting a disk transfer.
