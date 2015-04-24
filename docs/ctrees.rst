Conditioning trees
==================

There are a series of different representations of .. _conditioning
trees: http://cgroll.github.io/copula_theory/rvines/condTrees.html.

CTree types
-----------

Representation as array of individual paths to leaf nodes.

**CTreePaths**: 
	:root: `Int`
	:paths: `Array{Array{Int, 1}, 1}`

Parent reference notation, where entry `ii` denotes the single parent
of node `ii`.

**CTreeParRef**: 
   :tree: `Array{Int, 1}`


**CTreeAdja**


Tree dimensions
---------------

.. function:: width(tr::CTree)

   Number of paths / leaf nodes of tree.

.. function:: maxDepth(tr::CTree)

   Number of nodes of longest path.

.. function:: getDepths(tr::CTree)

   Length of each path to leaf nodes.

Tree entries
------------

.. function:: getindex()

   Yet to be defined correctly! Differs for different implementations.

.. function:: allNodes(tr::CTree)

   `Array{Int, 1}` of all occurring nodes in sorted order.

.. function:: allPathNodes(tr::CTree)

   `Array{Int, 1}` of all occurring nodes except root in sorted order.

   
