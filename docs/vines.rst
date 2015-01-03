Vines
=====

``Vines`` are basically an array of ``Trees``, stored in a more
concise notation as one single matrix (each tree is given as column
vector in parent notation). ``Trees`` also do not need to be fully
specified: they do not necessarily need to comprise all variables. For
example, when successively building ``Vines``, ``Trees`` are built up
only gradually. If unfinished ``Trees`` get converted to ``Vines``,
missing variables will have undefined values (this might be unstable,
however, in its current version).

Basically, ``Vines`` are a memory efficient way of storing multiple
trees, while any analysis needs to be built on actual ``Trees``
anyways.


Tree lengths
------------

.. function:: length(tr::Tree)

   Number of paths of the tree.

.. function:: maxLen(tr::Tree)

   Number of nodes of longest path.

.. function:: getLengths(tr::Tree)

   Length of each path.

Tree entries
------------

.. function:: getindex(tP::Tree, pathInd::Int, pathNode::Int)
              
   Get single node.

.. function:: getindex(tP::Tree, pathInd::Int)

   Get single path.

.. function:: getindex(tP::Tree, pathInds::Array{Int, 1}, pathNodes::Array{Int, 1})

   Get unique values of multiple entries. Values are sorted.

.. function:: allVals(tP::Tree)

   Get all values occuring in tree together with root node.

.. function:: allPathVals(tP::Tree)

   Get all values occuring in tree paths without root node.

Tree / vine interfaces
----------------------

.. function:: par2tree(parNot::Array{Int, 1})

   Transform single parent notation column to tree.

.. function:: par2tree(parNot::Array{Int, 2})

   Transform parent notation matrix to array of trees.

.. function:: tree2par(tP::Tree, nVars::Int)

   Transform single tree to parent notation vector.

.. function:: tree2par(tPs::Array{Tree, 1}, nVars::Int)

   Transform array of trees to parent notation matrix.

.. function:: vine2trees(vn::Vine)

   Transform ``Vine`` to array of ``Trees``.

.. function:: trees2vine(trs::Array{Tree, 1}, nVars::Int)

   Transform array of ``Trees`` to ``Vine``.
