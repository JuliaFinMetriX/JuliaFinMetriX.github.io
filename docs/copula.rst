Copulas
=======

ParamPC_MAT
-----------

.. function:: getVineCPPId(nam::Symbol)

   Get VineCPP copula ID for copula name.

.. function:: getVineCPPId(cop::ParamPC_MAT)

   Get VineCPP copula ID for ``ParamPC_MAT`` copula object.

.. function:: getCopNam(ii::Int)

   Get VineCPP copula name as ``Symbol`` for given VineCPP ID.

.. function:: getCopType(ii::Int)

   Get VineCPP copula type for given VineCPP ID.

Utilities
---------

.. function:: checkSameLength(u1::FloatVec, u2::FloatVec)

   Check whether two ``Array{Float, 1}`` have the same length.


.. function:: getFamAndParams(cop::ParamPC_MAT)

   Get the VineCPP copula ID and the parameters corresponding to a
   ``ParamPC_MAT`` copula. Both parameters and ID are transformed to
   ``Array{Float64, 1}`` and ``Float64`` respectively.

.. function:: params(cop::ParamPC_MAT)

   Get the parameters of a ``ParamPC_MAT`` copula.
