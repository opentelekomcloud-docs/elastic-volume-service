:original_name: evs_02_0020.html

.. _evs_02_0020:

Configuring Automatic Start of the RAID Array at Server Startup
===============================================================

Scenarios
---------

This section shows how to add RAID array information, such as the device name and UUID to the mdadm configuration file. In this case, the RAID array can be started by querying information in the configuration file when the system starts.

In this example, the ECS runs CentOS Stream 9. Configurations vary depending on the OS running on the ECS. This section is used for reference only. For the detailed operations and differences, see the corresponding OS documents.

Procedure
---------

#. Log in to the ECS as user **root**.

#. .. _evs_02_0020__li1820454151114:

   Run the following command to view the RAID array information:

   **mdadm --detail --scan**

   Information similar to the following is displayed:

   .. code-block:: console

      [root@ecs-raid10 ~]# mdadm --detail --scan
      ARRAY /dev/md0 metadata=1.2 name=ecs-raid10.novalocal:0 UUID=f400dbf9:60d211d9:e006e07b:98f8758c

#. .. _evs_02_0020__li18556171971518:

   Perform the following operations to add information of the new RAID array to the mdadm file:

   a. Run the following command to open the **mdadm.conf** file:

      **vi /etc/mdadm.conf**

   b. Press **i** to enter editing mode.

   c. Add the following information to the end of the file:

      .. code-block::

         DEVICE /dev/vdb /dev/vdc /dev/vdd /dev/vde
         ARRAY /dev/md0 metadata=1.2 name=ecs-raid10.novalocal:0 UUID=f400dbf9:60d211d9:e006e07b:98f8758c

      Description:

      -  DEVICE line: Indicates the device names of the disks that set up the RAID array. Multiple device names are separated with spaces.
      -  ARRAY line: Indicates RAID array information. Input the RAID array information obtained in :ref:`2 <evs_02_0020__li1820454151114>`.

      .. note::

         The preceding information is used for reference only. Add RAID array information based on the site information.

   d. Press **Esc**, enter **:wq!**, and press **Enter**.

      The system saves the modifications and exits the vi editor.

#. Run the following command to check whether the **mdadm.conf** file is modified:

   **more /etc/mdadm.conf**

   Information similar to the following is displayed:

   .. code-block:: console

      [root@ecs-raid10 ~]# more /etc/mdadm.conf
      DEVICE /dev/vdb /dev/vdc /dev/vdd /dev/vde
      ARRAY /dev/md0 metadata=1.2 name=ecs-raid10.novalocal:0 UUID=f400dbf9:60d211d9:e006e07b:98f8758c

   If the information added in :ref:`3 <evs_02_0020__li18556171971518>` is displayed, the file is successfully modified.
