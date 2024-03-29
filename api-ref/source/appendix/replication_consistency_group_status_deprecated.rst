:original_name: evs_04_0043.html

.. _evs_04_0043:

Replication Consistency Group Status (Deprecated)
=================================================

+--------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Replication Consistency Group Status | Description                                                                                                                                                                        |
+======================================+====================================================================================================================================================================================+
| creating                             | The replication consistency group is being created.                                                                                                                                |
+--------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| available                            | The replication consistency group is successfully created and is available for use.                                                                                                |
+--------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| error                                | An error occurs when you try to create a replication consistency group.                                                                                                            |
+--------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| deleting                             | The replication consistency group is being deleted.                                                                                                                                |
+--------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| updating                             | The replication consistency group is being updated. The update includes adding EVS replication pairs to and deleting EVS replication pairs from the replication consistency group. |
+--------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| reversing                            | The replication consistency group is being migrated as planned.                                                                                                                    |
+--------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| error_reversing                      | An error occurs during a planned migration of the replication consistency group.                                                                                                   |
+--------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| failovering                          | The failover of the replication consistency group is in progress.                                                                                                                  |
+--------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| failovered                           | The replication consistency group failover is successful.                                                                                                                          |
+--------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| error_failovering                    | An error occurs during a failover of the replication consistency group.                                                                                                            |
+--------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| error_deleting                       | An error occurs during the deletion of the replication consistency group.                                                                                                          |
+--------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

+--------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Replication Consistency Group Replication Status | Description                                                                                                                                                                          |
+==================================================+======================================================================================================================================================================================+
| active                                           | The replication status of the replication consistency group is normal, and the data in production disks is consistent with the data in DR disks.                                     |
+--------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| active-stopped                                   | The replication status of the replication consistency group is paused, and the data between production disks and DR disks within the group is inconsistent.                          |
+--------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| copying                                          | The data of the replication consistency group is being synchronized.                                                                                                                 |
+--------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| inactive                                         | The replication status of the replication consistency group is paused. The data between production disks and DR disks within the group is inconsistent and needs to be synchronized. |
+--------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| error                                            | The replication status of the replication consistency group becomes abnormal.                                                                                                        |
+--------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
