# Getting Started in Python

First, follow the steps on the [Installation](../../getting_started/installation) page for building and installing the Python bindings into a Python virtual environment.

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
```python
solver = marble.Solver()
solver.setup(Q, q, 
             J_eq=J_eq, b_eq=b_eq, J_ineq=J_ineq, b_ineq=b_ineq, 
             L=L, l=l, R=R, r=r, **settings)
results = solver.solve()
```

Consider the following simple example:

$$
\begin{align}
    \min_{x_{1:4}} \quad & x^\top x \\
    \text{subject to} \quad & x_1 = 1 \\
    &x_2 \geq 1 \\
    &0 \leq (x_3 + 1) \perp (x_4 - 1) \geq 0
\end{align}
$$

We can transcribe and solve this problem using Marble with Python using the following code: 

```python
import numpy as np
import marble

Q = 2.0 * np.eye(4)
q = np.zeros(4)

J_eq,   b_eq   = [[1.0, 0.0, 0.0, 0.0]], [-1.0]   # x[1] == 1
J_ineq, b_ineq = [[0.0, 1.0, 0.0, 0.0]], [-1.0]   # x[2] >= 1
L, l           = [[0.0, 0.0, 1.0, 0.0]], [1.0]    # x[3] + 1
R, r           = [[0.0, 0.0, 0.0, 1.0]], [-1.0]   # x[4] - 1

solver = marble.Solver()
solver.setup(Q, q, 0.0,
             J_eq=J_eq, b_eq=b_eq, J_ineq=J_ineq, b_ineq=b_ineq,
             L=L, l=l, R=R, r=r, verbosity=1)
results = solver.solve()

z = np.asarray(results.z)
```

You can run this same example inside the Marble repository. First, create a new virtual environment in the `Marble/python` directory:

```bash
cd /path/to/Marble/python
python -m venv .venv       # create new virtual env
source .venv/bin/activate  # activate virtual env
```

Then, install the Marble python bindings with:
```bash
pip install .
```

With the virtual environment activated, you can run the test with:
```bash
python /path/to/Marble/python/examples/simple_test.py
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