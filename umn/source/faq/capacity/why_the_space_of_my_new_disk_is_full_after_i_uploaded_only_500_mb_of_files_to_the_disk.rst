:original_name: evs_faq_280807.html

.. _evs_faq_280807:

Why the Space of My New Disk Is Full After I Uploaded Only 500 MB of Files to the Disk?
=======================================================================================

Troubleshoot this issue by performing the following steps:

#. Check whether the disk partition usage is 100% or almost 100%.

   .. code-block::

      df -h


   .. figure:: /_static/images/en-us_image_0000002278805664.png
      :alt: **Figure 1** Checking the partition usage

      **Figure 1** Checking the partition usage

   In this example, the **/dev/vda1** partition usage is 100%.

#. Check the disk space usage.

   .. code-block::

      df -i


   .. figure:: /_static/images/en-us_image_0000002313495213.png
      :alt: **Figure 2** Checking the disk space usage

      **Figure 2** Checking the disk space usage

   In this example, the disk space usage is low.

#. Check the deleted process files in the system.

   .. code-block::

      lsof | grep deleted


   .. figure:: /_static/images/en-us_image_0000002313462189.png
      :alt: **Figure 3** Checking the deleted process files in the system

      **Figure 3** Checking the deleted process files in the system

   Roughly calculate the total size of the deleted files based on the returned command output. If it is almost the same as the used space of the disk, the disk space may be used up by the deleted processes that have not been released.

#. Go to the location of a deleted file to check whether the file is still there.

   .. code-block::

      ll /tmp/

   Note that variable */tmp/* in the command indicates the path of the deleted file.

#. If the file is not there, run the following command to terminate the process, or restart the server to release the used space.

   .. code-block::

      kill -9 PID

   Note that variable *PID* in the command indicates the process ID.

#. Check that the process is terminated.

   .. code-block::

      lsof | grep deleted

#. Check that the disk partition usage is no longer 100%.

   .. code-block::

      df -h
