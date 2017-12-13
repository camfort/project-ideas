# Automatic sensitivity analysis and verification for numerical programs

A function *f* is said to be *r-sensitive* if given an input `x` and small permutation `c` 
(such that `x+c` is "nearby" to `x`) then:

       f(x)-f(x+c) <= r * c
    
That is, the distance between the output of `f(x)` and `f(x+c)` is bounded about by `r`-times
the permutation `c`. This is a useful notion in numerical models (common in science) because it
gives a bound on how sensitive a program is to errors in the input or round-off error in the
implemented discrete model. Sensitivity can be specialsied to a continuity argument when 
`c` is a very small number and `r=1`: *an infinitesimal change in inputs causes an infinitesimal
in the outputs*.

There has been various recent work on providing sensitivity/continuity analysis for
programming languages. Notable techniques include static analysis for imperative languages
[1, 2]  and type-system-based techniques (coming from the realm of differential privacy)
for functional languages [3,4].

The aim of this project is to implement one of these techniques a top Fortran: a commonly
used imperative language in natural sciences. We have already developed an extensive
analysis framework for Fortran, called CamFort [0] which can be built upon. This will
allow the project to move forward rapidly without having to spend time building basic 
components of parsers, lexers, standard code analyses, and test corpus of real Fortran code.
CamFort also has a deductive framework for expressing invariants and pre-and-post conditions
in code, which forms a starting point for some of the approaches in the literature [1,2].

This will be an active research project, with the opportunity to work with real code from
working scientists in the area of climate science, quantum physics, and biology. The project
can lean towards implementation or towards deeper research. For example, one might try to
extend the techniques of these papers or to provide a rigorous (mathematical) comparison
between the two main approaches in the literature.

[0] http://camfort.github.io
[1] Continuity Analysis of Programs (2010) Chaudhuri et al.  https://www.cs.rice.edu/~sc40/pubs/continuity.pdf
[2] Continuity and robustness of programs (2012) Chaudhuri et al. https://www.cs.rice.edu/~sc40/pubs/p107-chaudhuri.pdf
[3] Type-based Sensitivity Analysis (2013) - Antoni et al. https://pdfs.semanticscholar.org/1e7e/d2f38cf9fdbf35f5ed02d0e1a383ae5f87d6.pdf
[4] A Semantic Account of Metric Preservation (2017) - Amorm et al. https://arxiv.org/pdf/1702.00374.pdf
