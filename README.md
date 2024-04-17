[![INFORMS Journal on Computing Logo](https://INFORMSJoC.github.io/logos/INFORMS_Journal_on_Computing_Header.jpg)](https://pubsonline.informs.org/journal/ijoc)

# Ranking decomposition for the discrete ordered median problem

This archive is distributed in association with the [INFORMS Journal on
Computing](https://pubsonline.informs.org/journal/ijoc) under the [MIT License](LICENSE).

The software and data in this repository are a snapshot of the software and data that were used in the research reported in the paper Ranking decomposition for the discrete ordered median problem by M. Cherkesly, C. Contardo, and M. Gruson. The upstream repository (including a potentially more up-to-date version of this code) can be found at https://github.com/claud10cv/DiscreteOrderedMedian.jl. This snapshot has been built from [this commit](https://github.com/claud10cv/DiscreteOrderedMedian.jl/commit/26775fbe2124b092416e392dfb4727f018135798)


## Cite

To cite the contents of this repository, please cite both the paper and this repo, using their respective DOIs.

https://doi.org/10.1287/ijoc.2023.0059

https://doi.org/10.1287/ijoc.2023.0059.cd

Below is the BibTex for citing this snapshot of the respoitory.

```
@article{ranking2024ijoc,
  author =        { M. Cherkesly and C. Contardo and M. Gruson },
  publisher =     {INFORMS Journal on Computing},
  title =         { Ranking decomposition for the discrete ordered median problem },
  year =          {2024},
  doi =           {10.1287/ijoc.2023.0059.cd},
  url =           {https://github.com/INFORMSJoC/2023.0059},
  note =          {Available for download at https://github.com/INFORMSJoC/2023.0059},
}
```

## Description

This repository provides the source code, data files and detailed results as reported in the article.

The main folders are 'data', 'results', 'src' and 'test'.
- '[data](data)': This folder includes discrete ordered median instances.
- '[results](results)': This folder contains an excel file with detailed computational results.
- '[src](src)': The source code.
- '[test](test)': Tests.


## Installation

To install this Julia package, simply execute from a Julia Pkg REPL (by pressing `]` within a regular Julia REPL) the following:
```julia
(@v1.10) pkg> add https://github.com/INFORMSJoC/2023.0059
```

## Testing

You can test this method by executing from a Julia Pkg REPL (by pressing `]` within a regular Julia REPL) the following:
```julia
(@v1.10) pkg> test DiscreteOrderedMedian
```

## Basic Usage

1. Create a random instance using the generator provided in our code (alternatively, we also provide file readers for the two sets of instances in the folder '[data](data)'):
```julia
julia> data = generate_euclidean(10, 5, 1000, 1000, :pmedian; seed = 0)
julia> data = generate_euclidean(10, 5, 1000, 1000, :pmedian; seed = 0)
```
2. Optionally, you can modify the lambda vector, executing for instance
```julia
julia> data = modify_lambda(data, :T1)
```
3. Create a parameters object. The default constructor uses `HiGHS` as MILP solver
```julia
julia> params = default_parameters()
```
4. Solve the problem instance using our method
```julia
julia> res = bnb(data, params)
```

## Note on the choice of the MILP solver

This package leaves the user the freedom to specify one of the the following four solvers for the solution of the MILPs: `CPLEX`, `Gurobi`, `HiGHS`, and `GLPK`. Our package includes `HiGHS` as dependency and therefore uses it as default. In `optimizer.jl` you will find functions to be able to specify the other three solvers. To be able to reproduce the results in the manuscript, you need access to a license of `CPLEX` v22.1 (free for academics). The following workflow allows to run our method using `CPLEX` as underlying MILP solver:
```julia
julia> using DiscreteOrderedMedian
julia> using CPLEX
julia> data = generate_euclidean(10, 5, 1000, 1000, :pmedian; seed = 0)
julia> opt_data = cplex_optimizer_data(CPLEX.Optimizer)
julia> params = default_parameters_with_optimizer_data(opt_data)
julia> res = bnb(data, params)
```

## Results

The [results](results) folder provides detailed results for the aggregate data reported in the paper.
