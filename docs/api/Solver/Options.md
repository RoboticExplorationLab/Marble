---
generator: doxide
---


# Options

**struct Options**

Solver options


## Variables

| Name | Description |
| ---- | ----------- |
| [convergence_kkt_norm](#convergence_kkt_norm) | KKT Inf norm must be less than this value for convergence  |
| [convergence_eq_violation](#convergence_eq_violation) | Equality constraint violation Inf norm must be less than this value for convergence  |
| [convergence_ineq_violation](#convergence_ineq_violation) | Inequality constraint violation Inf norm must be less than this value for convergence  |
| [convergence_comp_violation](#convergence_comp_violation) | Complementarity constraint violation Inf norm must be less than this value for convergence  |
| [outer_step_kkt_norm](#outer_step_kkt_norm) | KKT Inf norm must be less than this value to take an outer step in the algorithm  |
| [penalty_initial](#penalty_initial) | Initial AL penalty parameter  |
| [penalty_max](#penalty_max) | Maximum AL penalty parameter  |
| [penalty_scaling](#penalty_scaling) | AL penalty parameter scaling factor, multiplies current penalty parameter  |
| [relaxation_initial](#relaxation_initial) | Initial relaxation parameter for complementarity and inequality constraints  |
| [relaxation_min](#relaxation_min) | Minimum relaxation parameter for complementarity and inequality constraints  |
| [relaxation_scaling](#relaxation_scaling) | Relaxation parameter scaling factor, multiplies current relaxation parameter  |
| [max_iters](#max_iters) | Maximum number of iterations for the solver, iterations refers to outer + inner iterations  |
| [max_iters_linesearch](#max_iters_linesearch) | Maximum number of iterations for the filter linesearch  |
| [gamma_objective](#gamma_objective) | (filter) Sufficient progress parameter for objective value decrease  |
| [gamma_constraint](#gamma_constraint) | (filter) Sufficient progress parameter for constraint violation decrease  |
| [ruiz_iterations](#ruiz_iterations) | Number of ruiz iterations for scaling  |
| [output_dir](#output_dir) | Output directory for solution and solve information  |
| [verbosity](#verbosity) | Verbosity level: 0=silent, 1=per-iteration table + footer  |
| [print_every](#print_every) | Print a row every N iterations (only used when verbosity >= 1)  |
| [debug](#debug) | Write a JSONL debug log with iterates and solver state (one JSON object per line)  |
| [debug_output_path](#debug_output_path) | Path to the debug log file (used when debug=true)  |
| [debug_log_every](#debug_log_every) | Log every N iterations (1 = every iteration)  |

## Variable Details

### convergence_comp_violation<a name="convergence_comp_violation"></a>

!!! variable "double convergence_comp_violation"

    Complementarity constraint violation Inf norm must be less than this value for convergence
    

### convergence_eq_violation<a name="convergence_eq_violation"></a>

!!! variable "double convergence_eq_violation"

    Equality constraint violation Inf norm must be less than this value for convergence
    

### convergence_ineq_violation<a name="convergence_ineq_violation"></a>

!!! variable "double convergence_ineq_violation"

    Inequality constraint violation Inf norm must be less than this value for convergence
    

### convergence_kkt_norm<a name="convergence_kkt_norm"></a>

!!! variable "double convergence_kkt_norm"

    KKT Inf norm must be less than this value for convergence
    

### debug<a name="debug"></a>

!!! variable "bool debug"

    Write a JSONL debug log with iterates and solver state (one JSON object per line)
    

### debug_log_every<a name="debug_log_every"></a>

!!! variable "int debug_log_every"

    Log every N iterations (1 = every iteration)
    

### debug_output_path<a name="debug_output_path"></a>

!!! variable "std::string debug_output_path"

    Path to the debug log file (used when debug=true)
    

### gamma_constraint<a name="gamma_constraint"></a>

!!! variable "double gamma_constraint"

    (filter) Sufficient progress parameter for constraint violation decrease
    

### gamma_objective<a name="gamma_objective"></a>

!!! variable "double gamma_objective"

    (filter) Sufficient progress parameter for objective value decrease
    

### max_iters<a name="max_iters"></a>

!!! variable "int max_iters"

    Maximum number of iterations for the solver, iterations refers to outer + inner iterations
    

### max_iters_linesearch<a name="max_iters_linesearch"></a>

!!! variable "int max_iters_linesearch"

    Maximum number of iterations for the filter linesearch
    

### outer_step_kkt_norm<a name="outer_step_kkt_norm"></a>

!!! variable "double outer_step_kkt_norm"

    KKT Inf norm must be less than this value to take an outer step in the algorithm
    

### output_dir<a name="output_dir"></a>

!!! variable "std::filesystem::path output_dir"

    Output directory for solution and solve information
    

### penalty_initial<a name="penalty_initial"></a>

!!! variable "double penalty_initial"

    Initial AL penalty parameter
    

### penalty_max<a name="penalty_max"></a>

!!! variable "double penalty_max"

    Maximum AL penalty parameter
    

### penalty_scaling<a name="penalty_scaling"></a>

!!! variable "double penalty_scaling"

    AL penalty parameter scaling factor, multiplies current penalty parameter
    

### print_every<a name="print_every"></a>

!!! variable "int print_every"

    Print a row every N iterations (only used when verbosity >= 1)
    

### relaxation_initial<a name="relaxation_initial"></a>

!!! variable "double relaxation_initial"

    Initial relaxation parameter for complementarity and inequality constraints
    

### relaxation_min<a name="relaxation_min"></a>

!!! variable "double relaxation_min"

    Minimum relaxation parameter for complementarity and inequality constraints
    

### relaxation_scaling<a name="relaxation_scaling"></a>

!!! variable "double relaxation_scaling"

    Relaxation parameter scaling factor, multiplies current relaxation parameter
    

### ruiz_iterations<a name="ruiz_iterations"></a>

!!! variable "int ruiz_iterations"

    Number of ruiz iterations for scaling
    

### verbosity<a name="verbosity"></a>

!!! variable "int verbosity"

    Verbosity level: 0=silent, 1=per-iteration table + footer
    

