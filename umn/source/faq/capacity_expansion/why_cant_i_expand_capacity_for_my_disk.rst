:original_name: evs_faq_0074.html

.. _evs_faq_0074:

Why Can't I Expand Capacity for My Disk?
========================================

Symptom
-------

Capacity expansion is not allowed for the disk.

Troubleshooting
---------------

Possible causes are listed here in order of their probability.

If the fault persists after you have ruled out one cause, move on to the next one in the list.

.. table:: **Table 1** Troubleshooting

   +----------------------------------------------+--------------------------------------------------------------------------------------------------------------------+
   | Possible Cause                               | Solution                                                                                                           |
   +==============================================+====================================================================================================================+
   | A shared disk is still attached to a server. | See :ref:`Shared Disk Is Still Attached to a Server <evs_faq_0074__en-us_topic_0256121776_section15399333143519>`. |
   +----------------------------------------------+--------------------------------------------------------------------------------------------------------------------+

.. _evs_faq_0074__en-us_topic_0256121776_section15399333143519:

Shared Disk Is Still Attached to a Server
-----------------------------------------

**Symptom**: The **Expand Capacity** button is grayed out. When you attempt to click the capacity expansion button, the following hover tip is displayed: This operation can be performed only when the shared disk is in the Available state.

**Solution**: Detach the disk from all servers. If the **Expand Capacity** button becomes available, you can expand the disk capacity.
