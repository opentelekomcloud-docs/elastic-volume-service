:original_name: evs_faq_0046.html

.. _evs_faq_0046:

What Are the Typical Causes of a Snapshot Creation Failure?
===========================================================

A snapshot creation will fail if its source disk is in an intermediate state, such as **Attaching** and **Expanding**, or an abnormal state, such as **Error** and **Restoration failed**.

Ensure that a disk is in the **In-use** or **Available** state before creating a snapshot.
