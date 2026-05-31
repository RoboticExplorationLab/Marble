# Getting Started in Julia
Marble solves QPCCs of the following form

$$
\begin{align}
    \min_{z, s, t} \quad &\frac{1}{2} z^\top Qz+g^\top z \\
    \text{subject to} \quad &J_{eq}z + b_{eq} = 0 \\
    &J_{ineq}z + b_{ineq} \geq 0 \\
    &Lz + l = s \\
    &Rz + r = t \\
    &0 \leq s \perp t \geq 0 
\end{align}
$$

through the following syntax
```
solver = Marble.Solver()
Marble.setup!(solver, Q, q, 
            J_eq=J_eq, b_eq=b_eq, J_ineq=J_ineq, b_ineq=b_ineq, 
            L=L, l=l, R=R, r=r; settings...)
results = Marble.solve!(solver)
```

Marble can also take problems constructed using JuMP, which is often much easier for complicated problems. You just need to specify the complementarity indices, like in the following example

```
# Construct a simple test problem using JuMP minimizing x'x
# where x[1] = 1
#       x[2] ≥ 1
#       0 ≤ (x[3] + 1) ⟂ (x[4] - 1) ≥ 0 --> solution is x[3] = 0, x[4] = 1
using Pkg; Pkg.activate(@__DIR__)
using Revise
using JuMP, Marble, NLPModelsJuMP

# Construct problem using JuMP
model = JuMP.Model()

@variable(model, x[1:4])
@objective(model, Min, x'*x)
@constraint(model, x[1] == 1)
@constraint(model, x[2] >= 1)

# For complementarities, we define each inequality and then specify indices
# for the complementarity pairs
@constraint(model, x3_comp, x[3] + 1 >= 0) # x3_comp a constraint variable
@constraint(model, x4_comp, x[4] - 1 >= 0)
comps = con_con_complementarities(model, [x3_comp,], [x4_comp,])

solver = Marble.Solver()
Marble.setup!(solver, model, first.(comps), last.(comps), [(:con, :con),]; verbosity = 1)
results = Marble.solve!(solver)
z = Marble.z(results)
```

The rest of this page will guide you through installing Marble in Julia and running the example above. 

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
To run the examples, first instantiate the environment in `julia/examples` and `dev` the Marble package. An example in the REPL package manager (accessible by entering the REPl and hitting `]`) is below:

```
(@v1.11) pkg> activate .
(examples) pkg> dev ..
(examples) pkg> instantiate
```

Once done, run `julia simple_test.jl`. The last part of the output should look like
```
Solver CONVERGED             45 iters (19 outer, 26 inner),  26 factorizations.
Final  ||kkt||=3.12e-16  ||eq||=0.00e+00  ||ineq||=0.00e+00  ||comp||=6.10e-06  obj=3.000018e+00

[1.0, 1.000003051754603, 6.103478372774856e-6, 1.0000061034905794]
3.000018310574183
[0.0]
[0.0]
[6.103527831912719e-6]
```
