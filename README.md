[![INFORMS Journal on Computing Logo](https://INFORMSJoC.github.io/logos/INFORMS_Journal_on_Computing_Header.jpg)](https://pubsonline.informs.org/journal/ijoc)

# FrankWolfe.jl

This archive is distributed in association with the [INFORMS Journal on
Computing](https://pubsonline.informs.org/journal/ijoc) under the [MIT License](LICENSE).

The software and data in this repository are a snapshot of the software and data
that were used in the research reported on in the paper 
[FrankWolfe.jl: a high-performance and flexible toolbox for Frank-Wolfe algorithms and Conditional Gradients](https://arxiv.org/abs/2104.06675) by 
M. Besançon, A. Carderera, and S. Pokutta. The snapshot is based on 
[this SHA](https://github.com/ZIB-IOL/FrankWolfe.jl/commit/f8fbdf9e2074eb72c51aedb9018280bcd930f5f6) 
in the development repository. 

**Important: This code is being developed on an on-going basis at 
https://github.com/ZIB-IOL/FrankWolfe.jl. Please go there if you would like to
get a more recent version or would like support**

## Cite

To cite this software, please cite the [paper](https://doi.org/10.1287/ijoc.2019.0934) using its DOI and the software itself, using its DOI.

Below is the BibTex for citing this version of the code.

```
@article{FrankWolfe.jl,
TODO
}  
```

# FrankWolfe.jl

This package is a toolbox for algorithms related to Frank-Wolfe or conditional gradients,
meant to solve problems of the type:

```
min_{x in C} f(x)
```
where `C` is a compact convex set for which a Linear Minimization Oracle (LMO) is defined
and `f` is a differentiable function for which the gradient is provided.

The main entry point is the `frank_wolfe` function running the algorithm.

```julia
FrankWolfe.frank_wolfe(f, grad!, lmo, x0, max_iteration=1000, verbose=true)
```

where `f(x)` is the objective function, `grad!(storage, x)` is the inplace gradient.
`lmo` is a structure implementing the Linear Minimization Oracle interface presented below
and encoding the constraints.

## Installation

The most recent release is available via the julia package manager, e.g., with

```julia
using Pkg
Pkg.add("FrankWolfe")
```

or the master branch:

```julia
Pkg.add(url="https://github.com/ZIB-IOL/FrankWolfe.jl", rev="master")
```

## Linear Minimization Oracles (LMO)

Several oracles are implemented, all are subtypes of `LinearMinimizationOracle`
and implement the method:

```julia
compute_extreme_point(lmo::LMO, direction; kwargs...) -> v
```

which takes a minimization direction and returns the point `v` minimizing in the direction
over the set represented by the LMO.

## Noteworthy examples

See the `/examples` folder. All examples run on the test environment using [TestEnv.jl](https://github.com/JuliaTesting/TestEnv.jl).

## Documentation

Extended documentation, contribution guide and examples are available at https://zib-iol.github.io/FrankWolfe.jl/dev/.
