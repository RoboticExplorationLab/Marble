# Getting Started in Julia
## Prerequisites

| Dependencies
|---|
| CMake ≥ 3.28 |
| Eigen3 | 
| nlohmann-json | 
| Julia ≥ 1.9 + CxxWrap.jl | 

!!! warning 
    CMake will compile using your default Julia version and global environment. You can install CxxWrap.jl into the environment using
    ```bash
    julia -e 'using Pkg; Pkg.add("CxxWrap")'
    ```
    We are working on updating this so that it uses the package environment.

## Install Guide
Once you have the prerequisites installed, clone the [Marble](https://github.com/MarbleSolver/RCQP) repository and in the root directory for the repository run
```bash
cmake --preset julia
cmake --build --preset julia
```

## Running Examples

