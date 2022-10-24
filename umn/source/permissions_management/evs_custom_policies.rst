:original_name: evs_01_0090.html

.. _evs_01_0090:

EVS Custom Policies
===================

Custom policies can be created to supplement the system-defined policies of EVS. For the actions supported for custom policies, see section "Permissions Policies and Supported Actions" in the *Elastic Volume Service API Reference*.

You can create custom policies in either of the following ways:

-  Visual editor: Select cloud services, actions, resources, and request conditions. This does not require knowledge of policy syntax.


   .. figure:: /_static/images/en-us_image_0000001242362390.jpg
      :alt: **Figure 1** Create Custom Policy

      **Figure 1** Create Custom Policy

-  JSON: Edit JSON policies from scratch or based on an existing policy.

   For operation details, see section "Creating a Custom Policy" in the *Identity and Access Management User Guide*. The following section contains examples of common EVS custom policies.

Example Custom Policies
-----------------------

-  Example 1: Allowing users to create disks.

   .. code-block::

      {
              "Version": "1.1",
              "Statement": [
                      {
                              "Action": [
                                      "evs:volumes:list",
                                      "evs:volumes:get",
                                      "evs:quotas:get",
                                      "evs:volumeTags:list",
                                      "evs:types:get",
                                      "evs:volumes:create",
                                      "ecs:cloudServerFlavors:get",
                                      "ecs:cloudServers:list",
                                      "bss:balance:view",
                                      "bss:order:pay",
                                      "bss:order:update"
                              ],
                              "Effect": "Allow"
                      }
              ]
      }

-  Example 2: Denying disk deletion

   A policy with only "Deny" permissions must be used in conjunction with other policies to take effect. If the permissions assigned to a user contain both "Allow" and "Deny", the "Deny" permissions take precedence over the "Allow" permissions.

   The following method can be used if you need to assign permissions of the **EVS FullAccess** policy to a user but you want to prevent the user from deleting EVS disks. Create a custom policy for denying disk deletion, and attach both policies to the group to which the user belongs. Then, the user can perform all operations on disks except deleting disks. The following is an example of a deny policy:

   .. code-block::

      {
              "Version": "1.1",
              "Statement": [
                      {
                              "Effect": "Deny",
                              "Action": [
                                      "evs:volumes:delete"
                              ]
                      }
              ]
      }
