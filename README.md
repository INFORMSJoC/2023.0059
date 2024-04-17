[![INFORMS Journal on Computing Logo](https://INFORMSJoC.github.io/logos/INFORMS_Journal_on_Computing_Header.jpg)](https://pubsonline.informs.org/journal/ijoc)

# Ranking decomposition for the discrete ordered median problem

This archive is distributed in association with the [INFORMS Journal on
Computing](https://pubsonline.informs.org/journal/ijoc) under the [MIT License](LICENSE).

The software and data in this repository are a snapshot of the software and data that were used in the research reported on in the paper Ranking decomposition for the discrete ordered median problem by M. Cherkesly, C. Contardo, and M. Gruson.


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
julia> data = generate_euclidean(10, 5, 1000, 1000, :pmedian; seed = seed)
```
2. Optionally, you can modify the lambda vector, executing for instance
```julia
julia> data = modify_lambda(data, :T1)
```
3. Create a parameters object. The default constructor uses `GLPK` as MILP solver
```julia
julia> params = default_parameters()
```
4. Solve the problem instance using our method
```julia
julia> res = DiscreteOrderedMedian.bnb(data, params)
```

## Results

The [results](results) folder provides detailed results for the aggregate data reported in the paper.
