TimeData
========

Statistics functions
--------------------

.. function:: movAvg(tm::AbstractTimematr, nPeriods::Integer)

   Calculate moving average.

I/O
---

.. function:: readTimedata(filename::String)

   Load csv and parse date column as  ``idx``.

.. function:: writeTimedata(filename::String, td::AbstractTimedata)

   Write TimeData object to csv file.
