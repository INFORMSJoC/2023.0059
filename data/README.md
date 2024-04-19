# DOMPInstances
Benchmark Datasets for the Discrete Ordered Median Problem used in Cherkesly, Contardo and Gruson (2023)

## Folder names
1.  Folder D20 contains the dataset proposed in Deleplanque et al 2020 (INFORMS Journal on Computing)
2.  Folder CCG23 contains newly generated instances with high magnitudes for the distances and weight vectors

## Filenames
Every file is named `dompXpYvZ.domp` where `X = # of nodes (n)`, `Y = # of facilities to locate (p)`, `Z = Instance number (typically a number between 1 and 10)`

## File structure
```markdown
NAME : "Name of the instance"
COMMENT : "Origin of the instance"
TYPE : DOMP
DIMENSION : "Number of nodes (n)"
DISPLAY_DATA_TYPE : NO_DISPLAY
OPEN_FACILITIES : "Number of open facilities (p)"
COST_SECTION : "Cost matrix D"
LAMBDA_SECTON : "Weight vector λ"
```
