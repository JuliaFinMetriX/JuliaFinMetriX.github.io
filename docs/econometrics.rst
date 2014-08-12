Econometrics
============

Return calculation
------------------

.. function:: disc2log(tm::AbstractTimenum; percent = false) 

   Convert discrete net returns to logarithmic returns.

.. function:: log2disc(tm::AbstractTimenum; percent = false)

   Convert logarithmic returns to discrete net returns.

.. function:: price2ret(tm::AbstractTimematr; log = true)

   Convert prices to returns.

.. function:: price2ret(tn::AbstractTimenum; log = true)

   Convert prices to returns with possibly occurring missing
   observations (NAs).
   
.. function:: ret2price(tm::AbstractTimematr; log = true)

   Convert returns to prices.

.. function:: ret2price(tn::AbstractTimenum; log = true)

   Convert returns to prices with possibly occurring missing
   observations (NAs).
