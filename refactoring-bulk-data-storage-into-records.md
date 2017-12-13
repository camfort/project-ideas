# Refactoring bulk data storage into record types
 - Keywords: programming languages, refactoring, program analysis, program transformation
 - Requirements: Functional programming skills
 - Resources: None beyond standard computing provision

In early imperative programming languages, arrays were the only structured data type beyond primitive types like floats, integers, and booleans. A common programming pattern emulated the structure type notion of a record type (a labelled variant) using arrays as a store with a set of integer variables as keys. For example, the following Fortran code defines an array d of three elements, where the integer variables x, y and z are used as record projections:

Code:

     integer :: x = 1
     integer :: y = 2
     integer :: z = 3
     real, dimension(3) :: d
     real :: sum
     sum = d(x) + d(y) + d(z)

The last line sums the fields of the record.
These manual record encodings quickly become unwieldy, requiring significant programmer effort to ensure that projections are used correctly and do not overlap. A common pattern is to read in a large number of parameters from a file (hundreds or even thousands), with a corresponding large collection of projection variables. Further, we have seen cases where these arrays are large and unwieldy yet could be decomposed into more meaningful subsets based on projection variable usage in the program: some subsets of projection variables are used disjointly or with small amounts of overlapping use.
In this work, we present an automatic program analysis and transformation procedure for converting the manual record pattern into structure record types. We prototype this in the context of Fortran, where the modern Fortran feature of derived data types provides record types. For the above example, this becomes:

Code:

     type D
        real :: x
        real :: y
        real :: z
     end type D
     type(D) d
     sum = d%x + d%y + d%z

The aim of this project is to extend the CamFort refactoring tool (http://github.com/camfort/camfort, written in Haskell) to support the above refactoring.
Some design choices/considerations are how to deal with:
- Granularity
- Naming
- Aliasing

As part of the project you will collaborate with an active research team spanning the University of Kent and the University of Cambridge. There is an option to publish your work- so this is a good project if you are considering doing a PhD.
