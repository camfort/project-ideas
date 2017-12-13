# Quantitative analysis of programming patterns in scientific computing

Keywords: programming languages, program analysis, quantitative analysis,
design patterns

Project type: Individual
Difficulty: Challenging
Requirements: Functional programming skills
Resources: None beyond standard computing provision

This project seeks to better understand the prevalent programming
patterns in computational science to help inform future language
designs targeted at aiding scientific computing.

There is currently a lack of quantitative data on programming idioms,
approaches, and needs in science. Many studies suggesting key idioms
are high-level and anecdotal (e.g., [1]). Other studies are too
low-level (at the syntactic- level, e.g., [2, 3, 5]) rather than
taking into account language semantics. The aim of this project is to
develop a programming pattern analysis tool for Fortran that can be
used to analyse whole code-base and extract metrics about the
programming patterns employed.

This project will be build on CamFort, a research infrastructure for
analysing and transforming Fortran code base (see some details in
[4]). Fortran remains a popular language for scientific computing,
partly due to the legacy of long-lived models written in Fortran that
continue to be useful. There is a large amount of scientific computing
code in Fortran available for analysis and I have a corpus of models
(including the Met Office UM, which is about a million lines of code
in length) available as a target for the tool.

In the first instance, the analysis tool will examine the use of
iteration over arrays in terms of their data dependencies (e.g., are
the loops potentially data parallel), side effects (e.g., how easy is
it to make safe loop transformations), and data access patterns (both
reading and writing). The project will require some refinement and
exploration of what can be analysed and tracked, and what this data
might be used for.

Potential results and idioms might be, for example, that X% of
programs have a gather pattern (read a number elements from an array
and write to a single location at a time), with a finite data access
stencil, and a shared portion of data under Y kb of expected
storage. If X% is significant, then this implies we should focus
future language design efforts on supporting such computations as
primitive.

There is already a simple tool for doing some array analysis here:
https://github.com/camfort/array-analyse
with results published recently [6].

[1] K. Asanovic, R. Bodik, et al. The Parallel Computing Laboratory at
U.C. Berkeley: A re- search agenda based on the Berkeley
view. Technical Report UCB/EECS-2008-23, University of California, Mar
2008.

[2] Knuth, Donald E. "An empirical study of FORTRAN programs."
Software: Practice and experience 1.2 (1971): 105-133.

[3] M. M Mendez, J. Overbey, and F. G. Tinetti. Legacy fortran
software: applying syntactic metrics to global climate models. In
XVIII Congreso Argentino de Ciencias de la Computacion, 2012.

[4] http://github.com/camfort

[5] R.-G. Urma and A. Mycroft. Programming language evolution via
source code query languages. In 4th workshop on Evaluation and
usability of programming languages and tools, pages 35-38. ACM, 2012.

[6] D. Orchard, M. Contrastin, M. Danish, A. Rice, Verifying Spatial 
Properties of Array Computations, Proceedings of the ACM on Programming
Languages, OOPSLA(1), 2017
