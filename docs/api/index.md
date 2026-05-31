---
generator: doxide
---


# C++ API Documentation



## Types

| Name | Description |
| ---- | ----------- |
| [Problem](Problem.md) | A brief description of your class. |
| [Filter](Filter.md) |  |
| [Workspace](Workspace.md) | Contains all elements computed during each solver iteration, including current solution estimates, KKT residual terms and hessians, and Newton step The workspace is initialized in Solver::set_problem() after the problem dimensions are known, and is updated during each iteration of the solver, minimizing allocations, though more work needs to be done to fully leverage this.  |
| [SolveResult](SolveResult.md) | A brief description of your class. |
| [Solver](Solver.md) |  |

