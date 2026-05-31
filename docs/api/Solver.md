---
generator: doxide
---


# Solver

**class Solver**



## Types

| Name | Description |
| ---- | ----------- |
| [Options](Solver/Options.md) | Solver options  |

## Functions

| Name | Description |
| ---- | ----------- |
| [retract](#retract) | Retraction map (elementwise)  |
| [retract_deriv](#retract_deriv) | Retraction map derivative (elementwise)  |
| [retract_second_deriv](#retract_second_deriv) | Retraction map second derivative (elementwise)  |
| [ruiz_equilibration](#ruiz_equilibration) | Ruiz equilibration for current problem data using copies of H and J_*. |
| [set_problem](#set_problem) | Sets the problem for the solver given sparse matrices, computes sparsity indexing  |
| [set_problem](#set_problem) | Sets the problem for the solver given dense matrices, computes sparsity indexing  |
| [set_problem](#set_problem) | Populates the KKT system, computes sparsity indexing  |
| [get_problem](#get_problem) | Returns the problem currently set for the solver  |
| [initialize_kkt_sparsity](#initialize_kkt_sparsity) | Construct and initialize KKT sparsity  |
| [update_KKT_residual](#update_KKT_residual) | Compute KKT residual given the current guess stored in the workspace  |
| [update_KKT_system](#update_KKT_system) | Update KKT system given the current guess stored in the workspace  |
| [update_KKT_ineq](#update_KKT_ineq) | Update the KKT terms associated with s_ineq (no dependence on m_ineq)  |
| [update_KKT_comp](#update_KKT_comp) | Update the KKT terms associated with s_comp and m_comp  |
| [update_KKT_penalty](#update_KKT_penalty) | Update the KKT penalty diagonal  |
| [update_KKT_primal_regularizer](#update_KKT_primal_regularizer) | Update the KKT regularizer  |
| [analytical_factorization](#analytical_factorization) | Perform an analytical factorization of the KKT system using QDLDL  |
| [numerical_factorization](#numerical_factorization) | Perform an numerical factorization of the KKT system using QDLDL  |
| [check_inertia](#check_inertia) | The KKT system should define a saddle point, with n_primal positive and n_dual negative eigenvalues We can check this (called the inertia) after numerical_factorization() by checking the number of positive and negative elements of D because LDLt factorizations preserve inertia  |
| [backsolve](#backsolve) | Solve the KKT system using the factorized matrix, populating the solution in workspace->newton_step. |
| [compute_amd_ordering](#compute_amd_ordering) | Compute AMD ordering  |
| [get_workspace](#get_workspace) | Returns the workspace used by the solver  |
| [get_filter](#get_filter) | Get the filter object :material-keyboard-return: **Return** :    Filter& Filter object used for linesearch in the solver  |
| [filter_linesearch](#filter_linesearch) | Perform backtracking filter linesearch given a step direction :material-location-enter: `sqrt_relax_param` :    Square root of the complementarity and inequality relaxation parameter :material-location-enter: `inv_penalty_param` :    Inverse of the AL penalty parameter :material-location-enter: `max_iters` :    Maximum number of iterations for the linesearch !!! warning This function modifies the workspace solution to store the candidate solution, and updates the constraint residuals based on the candidate solution, which are used to evaluate the filter conditions. If the linesearch fails, the workspace solution is restored to its original value before returning. :material-keyboard-return: **Return** :    true Linesearch succeeded, new iterate is stored in workspace x_candidate :material-keyboard-return: **Return** :    false Linesearch failed  |
| [solve](#solve) | Solve the current problem instance. |
| [convergence](#convergence) | Determine if the solver has converged based on KKT residual norm, constraint satisfaction  |

## Function Details

### analytical_factorization<a name="analytical_factorization"></a>
!!! function "bool analytical_factorization()"

    Perform an analytical factorization of the KKT system using QDLDL
    

### backsolve<a name="backsolve"></a>
!!! function "void backsolve()"

    Solve the KKT system using the factorized matrix, populating the solution
    in workspace->newton_step.
    

### check_inertia<a name="check_inertia"></a>
!!! function "bool check_inertia()"

    The KKT system should define a saddle point, with n_primal positive and n_dual negative eigenvalues
    We can check this (called the inertia) after numerical_factorization() by checking the number of
    positive and negative elements of D because LDLt factorizations preserve inertia
    

### compute_amd_ordering<a name="compute_amd_ordering"></a>
!!! function "void compute_amd_ordering()"

    Compute AMD ordering
    

### convergence<a name="convergence"></a>
!!! function "bool convergence(const Options &amp;options)"

    Determine if the solver has converged based on KKT residual norm, constraint satisfaction
    

### filter_linesearch<a name="filter_linesearch"></a>
!!! function "bool filter_linesearch(const double sqrt_relax_param, const double inv_penalty_param, int max_iters)"

    Perform backtracking filter linesearch given a step direction
    
    
    :material-location-enter: `sqrt_relax_param`
    :    Square root of the complementarity and inequality relaxation parameter
        
    :material-location-enter: `inv_penalty_param`
    :    Inverse of the AL penalty parameter
        
    :material-location-enter: `max_iters`
    :    Maximum number of iterations for the linesearch
        
    !!! warning
     This function modifies the workspace solution to store the candidate solution, and updates the constraint residuals based on the candidate solution, which are used to evaluate the filter conditions. If the linesearch fails, the workspace solution is restored to its original value before returning.
            
    :material-keyboard-return: **Return**
    :    true Linesearch succeeded, new iterate is stored in workspace x_candidate
            
    :material-keyboard-return: **Return**
    :    false Linesearch failed
    

### get_filter<a name="get_filter"></a>
!!! function "Filter&amp; get_filter()"

    Get the filter object
    
    
    :material-keyboard-return: **Return**
    :    Filter& Filter object used for linesearch in the solver
    

### get_problem<a name="get_problem"></a>
!!! function "Problem&amp; get_problem()"

    Returns the problem currently set for the solver
    

### get_workspace<a name="get_workspace"></a>
!!! function "Workspace&amp; get_workspace()"

    Returns the workspace used by the solver
    

### initialize_kkt_sparsity<a name="initialize_kkt_sparsity"></a>
!!! function "void initialize_kkt_sparsity()"

    Construct and initialize KKT sparsity
    

### numerical_factorization<a name="numerical_factorization"></a>
!!! function "bool numerical_factorization()"

    Perform an numerical factorization of the KKT system using QDLDL
    

### retract<a name="retract"></a>
!!! function "Vec retract(const Vec&amp; s, double sqrt_relax_param) const"

    Retraction map (elementwise)
    

### retract_deriv<a name="retract_deriv"></a>
!!! function "Vec retract_deriv(const Vec&amp; s, double sqrt_relax_param) const"

    Retraction map derivative (elementwise)
    

### retract_second_deriv<a name="retract_second_deriv"></a>
!!! function "Vec retract_second_deriv(const Vec&amp; s, double sqrt_relax_param) const"

    Retraction map second derivative (elementwise)
    

### ruiz_equilibration<a name="ruiz_equilibration"></a>
!!! function "void ruiz_equilibration(int niter = 10)"

    Ruiz equilibration for current problem data using copies of H and J_*.
    Writes concatenated scaling vector [d; e_eq; e_ineq; e_comp] into workspace->scaling.
    

### set_problem<a name="set_problem"></a>
!!! function "void set_problem(SMat cost_hessian, Vec cost_gradient, double cost_const, SMat J_eq, Vec c_eq, SMat J_ineq, Vec c_ineq, SMat L, Vec l, SMat R, Vec r, Solver::Options&amp; options)"

    Sets the problem for the solver given sparse matrices, computes sparsity indexing
    

!!! function "void set_problem(Mat cost_hessian, Vec cost_gradient, double cost_const, Mat J_eq, Vec c_eq, Mat J_ineq, Vec c_ineq, Mat L, Vec l, Mat R, Vec r, Solver::Options&amp; options)"

    Sets the problem for the solver given dense matrices, computes sparsity indexing
    

!!! function "void set_problem(const Solver::Options&amp; options)"

    Populates the KKT system, computes sparsity indexing
    

### solve<a name="solve"></a>
!!! function "SolveResult solve()"

    Solve the current problem instance.
    

### update_KKT_comp<a name="update_KKT_comp"></a>
!!! function "void update_KKT_comp(const Vec&amp; s_comp, const Vec&amp; m_comp, double sqrt_relax_param)"

    Update the KKT terms associated with s_comp and m_comp
    

### update_KKT_ineq<a name="update_KKT_ineq"></a>
!!! function "void update_KKT_ineq(const Vec&amp; s_ineq, double sqrt_relax_param)"

    Update the KKT terms associated with s_ineq (no dependence on m_ineq)
    

### update_KKT_penalty<a name="update_KKT_penalty"></a>
!!! function "void update_KKT_penalty(const double inv_penalty_param)"

    Update the KKT penalty diagonal
    

### update_KKT_primal_regularizer<a name="update_KKT_primal_regularizer"></a>
!!! function "void update_KKT_primal_regularizer(const double reg)"

    Update the KKT regularizer
    

### update_KKT_residual<a name="update_KKT_residual"></a>
!!! function "void update_KKT_residual(double sqrt_relax_param, double inv_penalty_param)"

    Compute KKT residual given the current guess stored in the workspace
    

### update_KKT_system<a name="update_KKT_system"></a>
!!! function "void update_KKT_system(double sqrt_relax_param, double inv_penalty_param)"

    Update KKT system given the current guess stored in the workspace
    

