# Array shape analysis for automatic bug finding

The aim of this project is to produce an automatic bug finding tool for array use
in Fortran code. Fortran is used a lot in natural and physical sciences for writing
large scale numerical models, and remains popular. Arrays are heavily used in this
context for representing data sets and modelling quantities that vary in space and
time. Fortran compilers provide some static checking of array use, but there are a
number of situations which are not checked.

For example, the following program declares an array of size 10, and then calls a 
subroutine (function that has no results) using that array. However, the subroutine
has no requirements on the length of the array, and reads from position 11. The
behaviour here is undefined: this may cause a memory violation or may just read
from uninitialized memory.

    program AssumedSize
      integer, dimension(10) :: arr
      call sub(arr)

      contains

      subroutine sub(arr)
        integer, dimension(*) :: arr
        print *, arr(11)
      end subroutine sub
    end program AssumedSize

Other problems can occur when an array is 'reshaped' but the reshaping information
is not properly propagated. A more thorough treatment of various problems can be
found here: https://github.com/camfort/project-ideas/blob/master/array-problems.pdf.

The aim of this project is to implement a static analysis for Fortran arrays, providing
an automated bug finding tool. We have already developed an analysis framework for Fortran,
called CamFort [0] which can be built upon. This will allow the project to move forward rapidly
without having to spend time building basic components of parsers, lexers, and standard
code analyses. We have a Fortran corpus comprising scientific Fortran packages and well
exceeding one million lines of code. The project can be evaluted on this corpus.

[0] http://camfort.github.io
