:original_name: evs_faq_0095.html

.. _evs_faq_0095:

What Does the "reserveVolume" Trace Mean in CTS?
================================================

Before an EVS disk is attached, the system will call the reserveVolume EVS API to check whether the disk can be attached. If it can be attached, the system then changes the disk status to **attaching** to avoid conflicts with other operations.
