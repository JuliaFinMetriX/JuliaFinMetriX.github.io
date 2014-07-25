TimeData
========

Access data
-----------

.. function:: idx(tn::AbstractTimedata)

   Get time index as array.

.. function:: names(tn::AbstractTimedata)

   Get column names.

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

.. function:: writemime(io::IO, ::MIME"text/html",
              td::AbstractTimedata)

   Timedata display function in ijulia.

.. function:: writemime(io::IO, ::MIME"text/html",
              tm::AbstractTimematr)

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
---

For the case of monotonically increasing index values, join operations
can be speeded up. The following join implementations exist. All
return a Timedata object.

.. function:: joinSortedIdx_inner(td1::AbstractTimedata,
              td2::AbstractTimedata)

   Inner join of object indices.

.. function:: joinSortedIdx_left(td1::AbstractTimedata,
              td2::AbstractTimedata)

   Left join of object indices.
   
.. function:: joinSortedIdx_right(td1::AbstractTimedata,
              td2::AbstractTimedata)

   Right join of object indices.

.. function:: joinSortedIdx_outer(td1::AbstractTimedata,
              td2::AbstractTimedata)
              
   Outer join of object indices.
