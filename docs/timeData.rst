TimeData
========

Access data
-----------

.. function:: idx(td::AbstractTimedata)

   Get time index as array.

.. function:: names(td::AbstractTimedata)

   Get column names.

.. function:: idxtype(td::AbstractTimedata)

   Get type of ``idx``.

.. function:: core(td::AbstractTimedata)

   Equal to ``get``, only for ``Timematr`` output will be ``Array{Float}``. 

.. function:: get(td::AbstractTimedata, idx1::Int, idx2::Int)

   Get single entry [idx1, idx2] of TimeData object.

.. function:: get(td::AbstractTimedata)

   Get all entries of TimeData object as Array.

.. function:: complete_cases(td::AbstractTimedata)
              
   Return ``Array{Bool}`` with ``true`` for rows without ``NA`` values.

Show entries
------------

Accessing entries through ``getindex`` methods will always preserve a
rectangular table data structure: the output is an intersection of a
subset of indices with a subset of columns. In contrast, ``showEntries``
methods allow to access data without rectangular structure. This way,
for example, entry (1,2) and entry (2,1) could be jointly accessed,
without simultaneously returning entries (1,1) and (2,2). The output
of ``showEntries`` always is of type ``Timedata``, with columns ``variable``
and ``value``.

.. function:: showEntries(td::AbstractTimedata, f::Function; sort="dates")

   Show all entries where function f returns ``true``. By default,
   return values in row major order: for each date try all variables.
   Column major order can be achieved through ``sort="variables"``.

.. function:: showEntries(td::AbstractTimedata, singleInd::Array{Int}) 

   Show entries given by linear indexing.

.. function:: showEntries(td::AbstractTimedata, rowInds::Array{Int}, colInds::Array{Int})

   Show entries given by subscript indexing.

.. function:: showEntries(td::AbstractTimedata, td2::AbstractTimedata)

   Show entries by element-wise logical indexing.


Editing entries
---------------

.. function:: setNA!(td::AbstractTimedata, rowIdx::Int, colIdx::Int)

   Set entry given by subscript indexing to ``NA``. Throws error for
   objects of type ``Timematr``.

.. function:: setindex!(td::Timedata, value::Any, rowIdx::Int, colIdx::Int)

   Set entry given by subscript indexing to a given value. 

.. function:: setindex!(td::AbstractTimenum, value::Any, rowIdx::Int, colIdx::Int)

   Set entry given by subscript indexing to a given value.

.. function:: impute!(td::AbstractTimedata, with="last")

   Replace ``NA`` with some value. Implemented options are ``last`` to
   use the last available observation, ``next`` to use the next
   available option, ``zero`` to insert a value of 0 for each ``NA``.
   ``single last`` only uses the last observation if there is a single
   ``NA`` in succession. For two or more successive values of ``NA``
   no imputation occurs. A single ``NA`` in the last row will be
   treated as if observations would follow, so that it gets replaced.
   Consecutive occurrences of ``NA`` at the beginning of the sample
   will be left untouched with options ``last`` and ``single last``.
   Same holds for consecutive occurrences of ``NA`` at the end of the
   sample for option ``next``.

Basic functions
---------------

.. function:: size(tn::AbstractTimedata)

.. function:: size(tn::AbstractTimedata, ind::Int)

.. function:: ndims(tn::AbstractTimedata)


Testing object properties
-------------------------

.. function:: isequal(tn::AbstractTimedata, tn2::AbstractTimedata)

   Test for equal indices, names, types and values. ``NA`` is equal to
   ``NA``.

.. function:: ==(tn::AbstractTimedata, tn2::AbstractTimedata)

   Test for equal indices, names, types and values. ``NA`` is not
   counted as equal to ``NA``.


.. function:: isequalElemwise(tn::AbstractTimedata, tn2::AbstractTimedata)

   Element-wise comparison with ``isequal``. Return ``Timedata`` with
   boolean values.

.. function::  issimilar(td1::AbstractTimedata, td2::AbstractTimedata)

   Test for equal meta-data: type, column names and indices.
   
.. function:: isna(td::AbstractTimedata)

   Element-wise testing for ``NA``. Returns boolean values as Timedata
   object.

.. function:: isapprox(tn::AbstractTimedata, tn2::AbstractTimedata)

   Test for equal indices, names, types and approximately equal
   values. Alleviates unit tests for values of type ``Float``.

Formatting functions
--------------------

.. function:: rmDatesOnlyNAs(tn::AbstractTimedata)

   Remove all dates that contain strictly missing values ``NA``.
   Required format, for example, for plotting with Gadfly.

.. function:: datesAsStrings(dats::Array{Date, 1})

   Convert vector of dates into ``Array{ASCIIString, n}``.

.. function:: datesAsStrings(tm::AbstractTimedata)

   Take ``TimeData`` object and convert its vector of dates into
   ``Array(ASCIIString, n)``. 

.. function:: datesAsNumbers(dats::Array{Date, 1})

   Convert vector of dates into ``Array{Float64, n}``.

   .. function:: datesAsNumbers(tm::AbstractTimedata)

   Take ``TimeData`` object and convert its vector of dates into
   numbers: ``Array{Float64, n}`` for ``Date`` and ``DateTime``
   entries.
   

Type preserving functions
-------------------------

.. function:: setNA!(td::AbstractTimedata, rowIdx::Int, colIdx::Int)

   Set a given entry to ``NA``. Could require change of column type to
   ``DataArray``. Throws error for ``Timematr``.

.. function:: hcat(inst::AbstractTimedata, inst2::AbstractTimedata)

   Horizontal concatenation of TimeData objects. Requires objects to
   be of equal type with completely equal time indices. Result will be
   of same type as input arguments.

.. function:: hcat(inst::AbstractTimedata...)

   Variable argument extension of ``hcat``.

.. function:: vcat(inst::AbstractTimedata, inst2::AbstractTimedata)

   Vertical concatenation of TimeData objects. Requires objects to be
   of equal type with equal column names and equal time index types.
   Result will be of same type as input arguments.

.. function:: vcat(inst::AbstractTimedata...)

   Variable argument extension of ``vcat``.

.. function:: flipud(inst::AbstractTimedata)

   Flip ``TimeData`` object upside down.
   
.. function:: narm(td::AbstractTimedata)

   Return copy of td with all rows removed that were containing ``NA``.


Conversion functions
-------------------
   
.. function:: asArrayOfEqualDimensions(arr::Array,
              td::AbstractTimedata)

   Extend row or column vector to two-dimensional array through
   copying values.

.. function:: asTd(arr::Array, td::Timedata)

   Extend  row or column vector to size of ``Timedata`` object similar
   to ``repmat`` and return it as ``Timedata`` object with equal index and
   names. 

.. function:: asTn(arr::Array, td::Timenum)

   Extend  row or column vector to size of ``Timenum`` object similar
   to ``repmat`` and return it as ``Timenum`` object with equal index and
   names.

.. function:: asTm(arr::Array, td::Timematr)

   Extend  row or column vector to size of ``Timematr`` object similar
   to ``repmat`` and return it as ``Timematr`` object with equal index and
   names.

   

DataFrame extensions
--------------------

.. function:: composeDataFrame(vals, nams)

   Compose DataFrame from Array and column names.

.. function:: round(df::DataFrame, nDgts::Int)

   Return DataFrame with rounded values. DataFrame entries must be
   numeric.

.. function:: round(df::DataFrame)

   Return DataFrame with values rounded to two significant digits.
   DataFrame entries must be numeric.

.. function:: @roundDf(expr::Expr)

   Display rounded DataFrame. Works with non numeric values also.

Display functions
------------------

.. function:: display(tn::AbstractTimedata)

   Timedata display function in standard REPL.

.. function:: writemime(io::IO, ::MIME"text/html", td::AbstractTimedata)

   Timedata display function in ijulia.

.. function:: writemime(io::IO, ::MIME"text/html", tm::AbstractTimematr)

   Timematr display function in ijulia. Values are rounded due to
   parsimony.

.. function:: @table(title::String, expr::Union(Expr, Symbol))
              
   Display expression or symbol in HTML with blue title header.


.. function:: str(tn::AbstractTimedata)

   More detailled display function similar to R syntax.

Statistics functions
--------------------

.. function:: mean(tm::AbstractTimematr, dim::Int = 1)

   Return mean column values as DataFrame.

.. function:: rowmeans(tm::AbstractTimematr)

   Return mean row values as Timematr.

.. function:: prod(tm::AbstractTimematr, dim::Int = 1)

   Return product of column values as DataFrame.

.. function:: rowprods(tm::AbstractTimematr)

   Return product of row values as Timematr.

.. function:: sum(tm::AbstractTimematr, dim::Int = 1)

   Return sum of columns as DataFrame.

.. function:: rowsums(tm::AbstractTimematr)

   Return sum of rows as Timematr.

.. function:: cov(tm::AbstractTimematr)

   Return covariance matrix as DataFrame.

.. function:: cor(tm::AbstractTimematr)

   Return correlation matrix as DataFrame.

.. function:: std(tm::AbstractTimematr)

   Return empirical standard deviation for each column as DataFrame.

.. function:: std(tm::AbstractTimematr, dim::Integer)

   Return empirical standard deviation for each column as DataFrame.

.. function:: minimum(tm::AbstractTimematr)

   Return minimum value as single value.

.. function:: minimum(tm::AbstractTimematr, dim::Integer)

   Return minimum values of each column as DataFrame.

.. function:: cumsum(tm::AbstractTimematr, dim::Integer)

   Calculate cumulative sums column-wise and return result as
   Timematr.

.. function:: cumprod(tm::AbstractTimematr, dim::Integer)

   Calculate cumulative products column-wise and return result as
   Timematr.
   
.. function:: rowstds(tm::AbstractTimematr)

   Return empirical standard deviation for each row as Timematr.

.. function:: geomMean(x::AbstractTimematr; percent = true)

   Calculate geometric mean for AbstractTimedata.

.. function:: geomMean(x; percent = true)

   Calculate geometric mean for Array.
   
.. function:: movAvg(tm::AbstractTimematr, nPeriods::Integer)

   Calculate moving average.

I/O
---

.. function:: readTimedata(filename::String)

   Load csv and parse date column as  ``idx``.

.. function:: writeTimedata(filename::String, td::AbstractTimedata)

   Write TimeData object to csv file.

Join functions
--------------

For the case of monotonically increasing index values, join operations
can be speeded up. The following join implementations exist. All
return a Timedata object.

.. function:: joinSortedIdx_inner(td1::AbstractTimedata, td2::AbstractTimedata)

   Inner join of object indices.

.. function:: joinSortedIdx_left(td1::AbstractTimedata, td2::AbstractTimedata)

   Left join of object indices.
   
.. function:: joinSortedIdx_right(td1::AbstractTimedata, td2::AbstractTimedata)

   Right join of object indices.

.. function:: joinSortedIdx_outer(td1::AbstractTimedata, td2::AbstractTimedata)
              
   Outer join of object indices.
