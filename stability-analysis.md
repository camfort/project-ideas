# Automated stability analysis for numerical code.

Numerical stability (in the context of approximate soultions to
differential equations) is the property of the solution algorithm that
approximation error at one time step does not cause error at the next
step to grow. Said another way, the variation in the result (the
error) is bounded as the step size (in time and space) tends to zero.

For linear systems of PDEs, one technique for assessing stability is
the von Neumann analysis [1] which can be used to find constraints on
the discretisation size in order to give a stable solution.  The
technique essentially is to take the approximation for some function f
and substitute the terms of f with the error function which is
approximated by a finite Fourier series. With some simplification and solving,
these leads to bounds on the discretisation sizes.

An automatic stability analysis ought to be possible via overloading along with
some simplification/solution procedure.

1. overload the numerical algorithm
2. instantiate for some 'error' numerals (see the approach of Automatic Differentation).
3. spit out an equation for error in terms of Fourier series
4. [simplification, may need custom procedure, I have some ideas]
5. feed to some real number checker
6. check constraint against steps sizes in the program
7. report on success or error (with bound information).

This would provide an automated procedure for stablity checks that could allow
the researcher to experiment with different parameters and permutations of their algorithm.
There is some existing work in the literature to take a starting point
[2].

We have already developed an extensive analysis framework for Fortran,
called CamFort [0] which can be built upon. This will allow the
project to move forward rapidly without having to spend time building
basic components of parsers, lexers, standard code analyses, and test
corpus of real Fortran code.

This project relates to automatic sensitivity analysis in its
philosophy
(https://github.com/camfort/project-ideas/blob/master/automatic-sensitivity-analysis.md)
but the resulting technique will likely be quite different.

[0] http://camfort.github.io

[1] https://en.wikipedia.org/wiki/Von_Neumann_stability_analysis

[2] "A Framework for the Automation of Generalized Stability Theory" -
Farrell et al.  http://epubs.siam.org/doi/abs/10.1137/120900745
