# Getting Started in Julia

First, follow the steps on the [Installation](../../getting_started/installation) page for building and installing the Julia bindings into a Julia environment.

## Setting Up Problems

Marble solves QPCCs of the following form

$$
\begin{align}
    \min_{z, s, t} \quad &\frac{1}{2} z^\top Qz+q^\top z \\
    \text{subject to} \quad &J_{eq}z + b_{eq} = 0 \\
    &J_{ineq}z + b_{ineq} \geq 0 \\
    &0 \leq Lz + l \perp Rz + r \geq 0
\end{align}
$$

through the following syntax:
```julia
solver = Marble.Solver()
Marble.setup!(solver, Q, q, 
              J_eq=J_eq, b_eq=b_eq, J_ineq=J_ineq, b_ineq=b_ineq, 
              L=L, l=l, R=R, r=r; settings...)
results = Marble.solve!(solver)
```

Marble can also take problems constructed using JuMP, which is often much easier for complicated problems. Consider the following simple example:

$$
\begin{align}
    \min_{x_{1:4}} \quad & x^\top x \\
    \text{subject to} \quad & x_1 = 1 \\
    &x_2 \geq 1 \\
    &0 \leq (x_3 + 1) \perp (x_4 - 1) \geq 0
\end{align}
$$

We can easily transcribe and solve this problem using JuMP by specifying the indices of variables or constraints which appear in the complementarity constraint:

```julia
using Marble
using JuMP, NLPModelsJuMP

# Construct problem using JuMP
model = JuMP.Model()

@variable(model, x[1:4])
@objective(model, Min, x'*x)

# Equality and inequality constraints
@constraint(model, x[1] == 1)
@constraint(model, x[2] >= 1)

# For complementarities, we define each inequality and then specify indices
# for the complementarity pairs
@constraint(model, x3_comp, x[3] + 1 >= 0)
@constraint(model, x4_comp, x[4] - 1 >= 0)
comps = con_con_complementarities(model, [x3_comp,], [x4_comp,])

solver = Marble.Solver()
Marble.setup!(solver, model, first.(comps), last.(comps), [(:con, :con),]; verbosity = 1)
results = Marble.solve!(solver)
z = Marble.z(results)
```

You can run this same example inside the Marble repository. First, instantiate the environment in `Marble/julia/examples` and `dev` the Marble package. 

You can do so by running the following commands from the root of the Marble repository:

```bash
cd julia/examples  # navigate to examples directory
julia --project=.  # enter Julia REPL
```

Inside the Julia REPL, activate the package manager by typing `]` and execute the following commands:
```
]            # activate package manager
dev ..       # install the Marble julia package one directory above julia/examples/
instantiate
```

Once done, run: 
```bash
julia --project=/path/to/Marble/julia/examples /path/to/Marble/julia/examples/simple_test.jl
```

The last part of the output should look like:

```
Solver CONVERGED             45 iters (19 outer, 26 inner),  26 factorizations.
Final  ||kkt||=3.12e-16  ||eq||=0.00e+00  ||ineq||=0.00e+00  ||comp||=6.10e-06  obj=3.000018e+00

[1.0, 1.000003051754603, 6.103478372774856e-6, 1.0000061034905794]
3.000018310574183
[0.0]
[0.0]
[6.103527831912719e-6]
```