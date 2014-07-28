Econometrics
============

Return calculation
------------------

.. function:: disc2log(tm::AbstractTimenum; percent = F) 

   Convert discrete net returns to logarithmic returns.

.. function:: log2disc(tm::AbstractTimenum; percent = F)

   Convert logarithmic returns to discrete net returns.

.. function:: price2ret(tm::AbstractTimematr; log = T)

   Convert prices to returns.

.. function:: price2ret(tn::AbstractTimenum; log = T)

   Convert prices to returns with possibly occurring missing
   observations (NAs).
   
.. function:: ret2price(tm::AbstractTimematr; log = T)

   Convert returns to prices.

.. function:: ret2price(tn::AbstractTimenum; log = T)

   Convert returns to prices with possibly occurring missing
   observations (NAs).
