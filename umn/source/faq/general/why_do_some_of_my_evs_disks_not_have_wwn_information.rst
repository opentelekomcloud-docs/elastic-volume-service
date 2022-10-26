:original_name: evs_faq_0021.html

.. _evs_faq_0021:

Why Do Some of My EVS Disks Not Have WWN Information?
=====================================================

EVS disks have two device types: VBD and SCSI. WWNs are used as the unique identifiers for SCSI EVS disks, and VBD EVS disks do not have WWNs.

You can view the WWN of a SCSI EVS disk on the management console. The details are as follows:

-  If the SCSI EVS disk is brand new, you can view the disk WWN on the disk details page.

   :ref:`Figure 1 <evs_faq_0021__fig10936527101715>` shows the query result.

   .. _evs_faq_0021__fig10936527101715:

   .. figure:: /_static/images/en-us_image_0107917672.png
      :alt: **Figure 1** Queried WWN information

      **Figure 1** Queried WWN information

-  If the SCSI EVS disk was created before the WWN feature rollout, the disk WWN will fail to be obtained.

   :ref:`Figure 2 <evs_faq_0021__fig1293431911208>` shows the query result.

   .. _evs_faq_0021__fig1293431911208:

   .. figure:: /_static/images/en-us_image_0107919973.png
      :alt: **Figure 2** No WWN information

      **Figure 2** No WWN information
