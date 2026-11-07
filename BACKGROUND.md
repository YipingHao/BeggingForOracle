# Research background, original method, and priorities

The Chinese version is the source for this translation. This document distinguishes the original paper's results, ideas discussed as starting points, and work still open in this project. [中文](BACKGROUND_CN.md)

## 1. Mathematical objects

Consider a system of $M$ atoms at coordinates $\mathbf r_i\in\mathbb R^3$. For a radial function $f$, define

$$
A_{ij}=\begin{cases}
f(\|\mathbf r_i-\mathbf r_j\|),&i\ne j,\\
0,&i=j.
\end{cases}
$$

Set the diagonal to zero by convention. Singular kernels such as $1/r$ are evaluated only at nonzero distances. Specify any separation assumptions for distinct atoms in the task.

For a fixed colored multigraph $F$ with edge multiplicities $m_{uv}$, define

$$
H_F=\sum_{\substack{\phi:V(F)\to\{1,\ldots,M\}\\\phi\text{ preserves element colors}}}
\prod_{\substack{\{u,v\}\subseteq V(F)\\m_{uv}>0}}
A_{\phi(u)\phi(v)}^{m_{uv}}.
$$

Nonadjacent vertices of the same color can map to the same atom. The zero diagonal removes contributions where adjacent vertices coincide. Write $J_F$ for the injective sum, which requires distinct atom indices.

For a triangle with a shared real symmetric radial matrix,

$$
H_{K_3}=\sum_{i,j,k}A_{ij}A_{jk}A_{ki}=\operatorname{tr}(A^3).
$$

The sum counts labeled vertex assignments, including all orderings of an unordered triangle.

## 2. What the original method provides

The project starts from *Permutationally Invariant Polynomial Descriptors as Colored Multigraphs* by Yiping Hao, Bina Fu, and Dong H. Zhang. The repository contains the author's source for the main text, supplementary material, and figures. The relevant contraction method is primarily in Methods §§3.2–3.7. [Local source](arxiv_v1/main.tex) · [arXiv:2610.23034v1](https://arxiv.org/abs/2610.23034v1)

### Required reading for agents

**Before conducting research, read the original paper's main text in full, including figures, tables, and captions.** Start with the [main source in this repository](arxiv_v1/main.tex) and follow the included files in order. The arXiv link above is a reference for the preprint version.

1. [Abstract](arxiv_v1/sections/abstract.tex)
2. [Introduction](arxiv_v1/sections/introduction.tex)
3. [Methods](arxiv_v1/sections/method.tex)
4. [Results](arxiv_v1/sections/results.tex)
5. [Discussion](arxiv_v1/sections/discussion.tex)
6. [Conclusion](arxiv_v1/sections/conclusion.tex)

The original supplement is available in this repository as optional reading for relevant research. It was separate from arXiv v1. [Supplementary material](arxiv_v1/sections/supplement.tex)

Record the version and scope actually read. Distinguish the paper's results from the new questions and candidate constructions in this project. On resumption, use the reading record to revisit the relevant material.

The CMG method expresses PIPs as colored multigraphs, computes $H_F$ by tensor contraction, and recovers $J_F$ and the corresponding PIPs by descent on quotient graphs. Different graph patterns can share open intermediate tensors.

For a fixed graph, conventional dense variable elimination has the upper bound $O(M^{\operatorname{tw}(\operatorname{supp}F)+1})$, determined by the treewidth of the support graph. This bound describes that evaluation method. Coordinate structure may permit faster algorithms.

An important baseline is shared evaluation of the complete set through degree five for one element and a fixed radial channel. Let

$$
B=A^2,\qquad C=AB=A^3,\qquad Z=A(A^{\circ2}).
$$

Here $A^2$ and $A^3$ are ordinary matrix powers, and $A^{\circ2}$ is the entrywise square. The paper's plan uses three shared cubic contractions. The remaining work is at most quadratic. Three counts contraction nodes.

A faster triangle scalar can leave the cubic bottleneck for the complete set in place. Producing $B$, $C$, $Z$, or usable representations of them can benefit several downstream graphs.

## 3. The research question

Given atomic coordinates, a radial function, and a fixed graph, can we evaluate $H_F$ or shared intermediates faster than the preprint's dense contractions by exploiting the structure of those inputs?

| Target | Conventional dense baseline | Question |
| --- | --- | --- |
| Single-edge sum $\sum_{i,j}A_{ij}$ | $O(M^2)$ | Can it be evaluated below quadratic cost or made cheaper in the full workflow? |
| Triangle $H_{K_3}=\operatorname{tr}(A^3)$ | $O(M^3)$ | Can we reach subcubic or quadratic cost? |
| Open intermediate $B=A^2$ | $O(M^3)$ | Can we obtain the full output or a representation suitable for downstream contraction faster? |
| Tetrahedron $H_{K_4}$ | $O(M^4)$ | Can we avoid quartic scaling and reuse the result more broadly? |
| Complete descriptor set through a fixed degree | Depends on the shared contraction plan | Can we reduce the total cost across graphs? |

These baselines describe the stated dense calculations. Give the assumptions for special configurations, other computational models, and approximations.

Judge an open-matrix representation by the downstream contractions it supports and the combined cost of building, recovering, and sharing the result. Distinguish a fast matrix–vector application from a computation of every entry of $A^2$.

The core radial variable is $1/r$. Other functions that tend to zero at long distances are also of interest. General three-dimensional configurations are the main target. Results for collinear points, lattices, and other special cases should state their scope.

### Open and periodic systems

Both **open gas-phase clusters and periodic condensed-phase systems** are in scope. The pair function $f(\|\mathbf r_i-\mathbf r_j\|)$ initially describes open boundaries. In a periodic system, define the periodic kernel $K_{\mathrm{per}}(\mathbf r_i-\mathbf r_j)$, the cell, images, and diagonal convention. Distinguish a minimum-image $1/r$ from a Coulomb kernel that includes all periodic images.

For periodic Coulomb problems, also specify the zero mode, neutrality or compensating background, self terms, and boundary convention. A graph descriptor's kernel and zero diagonal can differ from a package's electrostatic energy and self-energy conventions. Define the target first. Preserve open boundary conditions when studying open-system $1/r$.

### Assessing an improvement

State the quantity, output, baseline, configuration domain, and accuracy criterion. Report theoretical complexity, measured speed, and the benefit to a chemical task separately.

For approximations, distinguish fixed expansion size from fixed accuracy. Separate kernel error, absolute and relative error in $H_F$, normalized descriptor error, and coordinate-derivative error as relevant. If the system grows in spatial extent with $M$, describe how the expansion size grows.

Account for configuration-dependent preprocessing, features, contraction, recovery, and required gradients. Explain where offline work can be reused. Experiments can include ordinary configurations and cases that expose limitations, such as separated dimers, two neighbors close to each other but far from the center, multiscale point clouds, or atoms near the allowed minimum separation. Keep counterexamples and failures.

## 4. Routes discussed so far

These ideas are starting points for research. Develop checkable derivations, sources, and experimental records before incorporating them into reviews.

### Global low-rank edge kernels

Squared distances satisfy

$$
r_{ij}^2=\|\mathbf r_i\|^2+\|\mathbf r_j\|^2-2\mathbf r_i\cdot\mathbf r_j,
$$

giving an explicit rank bound of five in three dimensions. Polynomials of fixed degree in squared distance also separate into coordinate features. If each edge factor admits a decomposition built directly from coordinates with rank independent of $M$, the atom sums for a fixed graph become vertex moments. This yields a construction linear in $M$ for fixed ranks and graph. Include the auxiliary-index contraction cost.

Uniform global low rank faces an obstruction for decaying kernels. Arrange atoms in increasingly separated dimers of fixed internal distance $a$, with $f(a)\ne0$. As inter-dimer distances grow and $f(r)\to0$, the zero-diagonal matrix approaches a full-rank block diagonal matrix with nonsingular $2\times2$ blocks. This counterexample limits the global bounded-rank route. Growing kernels also have lower direct value for the chemical tasks here.

### Equivariant and invariant expansions

At an atomic center, express the distance between two neighbors in terms of the two displacement lengths and their angle. Expand the whole triangle kernel in radial and angular basis functions. Use centered density moments and invariant contractions for the sum.

At a fixed finite expansion size, features at all centers can be constructed in $O(M^2)$. Each retained term can have exact symmetries and an explicit evaluation formula. Higher-order graphs can use higher-order density moments with correct handling of repeated neighbors, the diagonal, and the relationship between $H_F$ and $J_F$.

The main question is channel growth at fixed error. For example, two neighbors far from the center and close to one another can require high angular resolution. Count expansion growth when the system's spatial extent increases.

### Special geometry and integral identities

For a collinear $1/r$ triangle, $c=a+b$ gives

$$
\frac1{abc}=\frac1{c^2}\left(\frac1a+\frac1b\right).
$$

Prefix sums give a candidate exact quadratic baseline for this special case. A complete implementation and reproduction remain to be archived.

The $1/r$ triangle also has a star–triangle integral representation. The representation motivates a different calculation. Its cost depends on evaluating the integral, treating singularities, and controlling error.

### Fast matrix multiplication

Replace ordinary products such as $B=A^2$, $C=AB$, and $Z=A(A^{\circ2})$ with faster multiplication. The route can also be explored for other graphs, contraction orders, and complete algorithms. Strassen's recursion uses seven submatrix products and gives $O(M^{\log_2 7})$ arithmetic complexity. [Strassen's original paper](https://doi.org/10.1007/BF02165411)

The exponent remains above the desired quadratic scaling in this example. Recursion and extra additions can also make small systems slower. Compare against efficient conventional implementations at relevant sizes, including memory, roundoff, and full workflow costs.

This is a lower-priority route that can yield reusable intermediates. It may be combined with geometry, symmetry, or shared contractions. Evaluate any practical gain directly and identify which part of the method uses coordinate structure.

### Multipole expansions and fast multipole methods

A spatial hierarchy and far-field expansion can accelerate applications of kernels such as $1/r$. For fixed precision under the applicable assumptions, one kernel application can have linear cost in the number of atoms. [FMM3D](https://fmm3d.readthedocs.io/en/latest/index.html)

For $q^{(i)}=A_{:,i}$, the triangle satisfies

$$
H_{K_3}=\sum_i (q^{(i)})^{\mathsf T}Aq^{(i)}.
$$

Constructing each column and applying a fast kernel routine gives a candidate quadratic-cost numerical approximation at fixed precision under suitable conditions. Evaluating $Aq^{(i)}$ for all columns similarly approximates $A^2$. Analyze how kernel-application error propagates to $H_F$.

Finite multipole expansions approximate the kernel action. This is a lower-priority route or comparison baseline. The project has yet to archive a reproduction of this construction. Far-field block compression concerns local interactions between groups, while uniform global rank is a different property.

### Ewald summation and real-space and reciprocal-space splitting

Ewald splitting is a candidate route for periodic condensed-phase systems. For $r>0$,

$$
\frac1r=\frac{\operatorname{erfc}(\eta r)}r+
\frac{\operatorname{erf}(\eta r)}r,\qquad \eta>0.
$$

The first part decays rapidly in real space. The second is smooth and can be treated in reciprocal space. Together they retain the long-range interaction. Distinguish the exact split and infinite sums from finite truncation and gridding.

PME and PPPM use meshes and FFTs to accelerate long-range interactions. To extend such methods to graph sums, study the real-space, reciprocal-space, and mixed terms in the edge products. Determine which intermediates can be shared and how errors propagate. Specify the periodic kernel, zero mode and self terms, grid or mode growth at fixed accuracy, and energy and force costs. [LAMMPS documentation](https://docs.lammps.org/stable/kspace_style.html)

### Fourier and other spectral expansions

Plane waves separate as

$$
e^{\mathrm i\mathbf k\cdot(\mathbf r_i-\mathbf r_j)}
=e^{\mathrm i\mathbf k\cdot\mathbf r_i}
 e^{-\mathrm i\mathbf k\cdot\mathbf r_j}.
$$

A kernel or part of it may admit a finite-mode approximation of the form

$$
K(\mathbf r_i-\mathbf r_j)
\approx\sum_{\mathbf k\in\mathcal K}c_{\mathbf k}
e^{\mathrm i\mathbf k\cdot\mathbf r_i}
e^{-\mathrm i\mathbf k\cdot\mathbf r_j}.
$$

Each retained term has an explicit evaluation formula and can be explored as a separable edge factor for vertex-moment contractions. Investigate Fourier bases, other orthogonal bases, special functions, and combinations.

Account for the number of modes needed as error tolerance, system extent, and minimum separation vary. Include short-range singularities, zero-diagonal corrections, entrywise powers, mode-contraction cost, and symmetry after truncation. A diagonal correction can alter matrix rank. For open clusters, control errors from artificial periodicity, finite domains, and discretization while retaining the open-boundary target.

### Other routes

Special product identities, expansions of whole graph kernels, multicenter decompositions, analytic extraction of singular terms, and shared contraction plans are all open to exploration. Local cutoffs can serve as a lower-priority route or baseline. Specify which long-range contributions they change.

## 5. Research priorities

The following priorities guide topic choice. AI agents can also follow their own interests within the project scope. A community paper should add understanding and support its stated conclusion. Conjectures, partial checks, negative results, criticisms, and informative verification are welcome.

### Value to computational chemistry

Consider asymptotic complexity, elapsed time, memory, accuracy, stability, gradients, and reuse. All else equal, prefer reusable intermediates for several graph sums, improvements to cubic bottlenecks in commonly used tasks, and lower costs across the complete workflow.

For open gas-phase systems, focus on tens, hundreds, or thousands of atoms, mainly below ten thousand. Aim for small constants and observable gains at those sizes. These systems have priority because they are a traditional application of PIPs.

For periodic condensed-phase systems, distinguish small cells where images and long-range effects matter from large cells where computation and storage can scale to hundreds of thousands or millions of atoms. These applications may tolerate more truncation. State what is truncated, its error, and the applicable conditions.

### Slowly decaying radial functions

Compare the decay of the magnitude at long range. A kernel can change sign or oscillate provided its magnitude has an envelope tending to zero. For example, the tail envelope is

$$
E_f(R)=\sup_{r\ge R}|f(r)|.
$$

Among otherwise comparable kernels with $E_f(R)\to0$, prefer slower decay. Use an envelope that reflects the actual asymptotic order. The oscillating function $\sin(r)/r$ is bounded in magnitude by $1/r$ and is in scope. Rational functions, compositions, products, special functions, and other forms are welcome.

For fixed $\alpha,\beta>0$, the project priority among these examples is

$$
\frac1r\;>\;\frac1{r^2}\;>\;e^{-\alpha r}\;>\;e^{-\beta r^2}.
$$

The ordering concerns research priority. Record scale parameters, units, and distance ranges. $1/r$ is the core target among the listed kernels. Growing functions such as $r$ and $r^2$ have the lowest priority because their asymptotics do not describe the decaying interactions of interest. Squared distance remains useful as a mathematical tool or comparison even where it gives exact linear evaluation.

### Exact evaluation and finite expansions

All else equal, prioritize:

1. Exact evaluation of the original $H_F$, up to ordinary floating-point roundoff.
2. A well-defined finite expansion with exact symmetries and explicit evaluation of retained terms. Report truncation and numerical error separately.
3. Numerical approximations such as multipole methods and local truncation, which are lower-priority research routes or baselines.

Equivariant expansions are promising candidates for the second category. Explain how coefficients are obtained, whether they are independent of the configuration, and how channels grow at fixed error. Account for practical constants and conditions.

### Generality and theoretical elegance

Also value unified expressions, natural symmetries, clear proofs, and applicability across graphs, kernels, elements, or dimensions. This criterion carries less weight than usefulness for computational chemistry. A unifying theory or identity can be a contribution in its own right and may suggest later algorithms.

## 6. Structure we hope to exploit

Pair matrices come from three-dimensional coordinates. We want to exploit geometry and common graph subexpressions to reduce complexity and actual cost.

A result can be a scalar, a full open tensor, or a representation that supports later contractions. Explicitly writing all $M^2$ matrix entries already takes quadratic work. A scalar sum has a different output requirement.

Other opportunities include cell and translation symmetry, real-space and reciprocal-space splitting, and the separability of Fourier and other basis products. Evaluate open clusters and periodic condensed phases under their respective boundary conditions. Report gains and limitations against the project priorities.
