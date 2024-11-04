:original_name: evs_02_0017.html

.. _evs_02_0017:

Creating an ECS
===============

Scenarios
---------

This section shows how to create an ECS. In this example, one ECS needs to be created. For details about the ECS parameter configurations, see :ref:`Resource Planning <evs_02_0015>`.

Procedure
---------

#. Log in to the management console.

#. Under **Computing**, click **Elastic Cloud Server**.

   The **Elastic Cloud Server** page is displayed.

#. Click **Create ECS**.

   For details, see the *Elastic Cloud Server User Guide*.

   Configure the following parameters as planned:

   -  **Image**: Select **CentOS** and choose **Standard_CentOS_Stream-9_latest(6GB)**.

   -  **EIP**: An EIP is mandatory if the ECS needs to access the public network. In this example, the multiple devices admin (mdadm) tool needs to be installed. Therefore, an EIP must be configured. Assign an EIP or configure an existing one based on the environment condition.

      :ref:`Figure 1 <evs_02_0017__fig95671448155112>` shows how to assign a new EIP.

      .. _evs_02_0017__fig95671448155112:

      .. figure:: /_static/images/en-us_image_0139687404.png
         :alt: **Figure 1** Configuring EIP

         **Figure 1** Configuring EIP

   :ref:`Table 1 <evs_02_0017__table1464613260492>` shows the ECS parameter configurations.

   .. _evs_02_0017__table1464613260492:

   .. table:: **Table 1** ECS parameter configurations

      +------------------------------+----------------------------------------------------+-----------------+
      | ECS Parameter Configurations |                                                    | Quantity        |
      +==============================+====================================================+=================+
      | Specifications               | General computing \| s2.medium.2 \| 1 vCPU \| 2 GB | 1               |
      +------------------------------+----------------------------------------------------+-----------------+
      | Image                        | CentOS Stream 9                                    |                 |                 
      +------------------------------+----------------------------------------------------+-----------------+
      | System disk                  | High I/O, 40 GB                                    |                 |                 
      +------------------------------+----------------------------------------------------+-----------------+
      | VPC                          | vpc-1a55                                           |                 |                 
      +------------------------------+----------------------------------------------------+-----------------+
      | Security group               | Sys-default                                        |                 |             
      +------------------------------+----------------------------------------------------+-----------------+
      | NIC                          | subnet-1a55(192.168.1.0/24)                        |                 |                 
      +------------------------------+----------------------------------------------------+-----------------+
      | EIP                          | EIP: Auto Assign (Dynamic BGP)                     |                 |                 
      |                              |                                                    |                 |                 
      |                              | Bandwidth Size: 5 Mbit/s                           |                 |                 
      +------------------------------+----------------------------------------------------+-----------------+
      | ECS Name                     | ecs-raid10                                         |                 |                 
      +------------------------------+----------------------------------------------------+-----------------+
