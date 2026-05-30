---
generator: doxide
---


# Workspace

**class Workspace**

Contains all elements computed during each solver iteration, including current solution estimates, KKT residual terms and hessians, and Newton step

The workspace is initialized in Solver::set_problem() after the problem dimensions are known, and is updated during each iteration of the solver, minimizing allocations,
though more work needs to be done to fully leverage this.


## Variables

| Name | Description |
| ---- | ----------- |
| [z](#z) | Stacked solution vector [z; s_ineq; s_comp; m_eq; m_ineq; m_comp]  |
| [s_ineq](#s_ineq) | Primal variables  |
| [s_comp](#s_comp) | Inequality slacks (in the retraction domain)  |
| [m_eq](#m_eq) | Complementarity slacks (in the retraction domain)  |
| [m_ineq](#m_ineq) | Equality multipliers  |
| [m_comp](#m_comp) | Inequality multipliers  |
| [m_eq_est](#m_eq_est) | Complementarity multipliers  |
| [m_ineq_est](#m_ineq_est) | Equality multiplier estimates for AL  |
| [m_comp_est](#m_comp_est) | Inequality multiplier estimates for AL  |
| [kkt_residual](#kkt_residual) | Complementarity multiplier estimates for AL  |
| [s_ineq_stationarity](#s_ineq_stationarity) | KKT residual, driven to 0 in each subproblem solve  |
| [s_comp_stationarity](#s_comp_stationarity) | Inequality stationarity terms  |
| [residual_eq](#residual_eq) | Complementarity stationarity terms  |
| [residual_ineq](#residual_ineq) | Equality constraint residuals  |
| [residual_comp](#residual_comp) | Inequality constraint residuals  |
| [relax_param](#relax_param) | Complementarity constraint residuals  |
| [penalty_param](#penalty_param) | Relaxation parameter for the retraction map  |
| [kkt_system](#kkt_system) | Penalty parameter for the augmented Lagrangian KKT system matrix, stored in sparse format with the structure intended to be fixed after it is initialize by Solver::set_problem.  |
| [amd_perm_vec](#amd_perm_vec) | AMD permutation for KKT system, reduces in-fill  |
| [amd_iperm_vec](#amd_iperm_vec) | AMD permutation for KKT system, reduces in-fill  |
| [scaling](#scaling) | Inverse AMD permutation for KKT system  |
| [newton_step](#newton_step) | Diagonal scaling for KKT system, improves conditioning (ruiz equilibration)  |
| [etree](#etree) | Newton step for the KKT system (possibly computed with regularization)  |

## Functions

| Name | Description |
| ---- | ----------- |
| [appendBlockTriplets](#appendBlockTriplets) | Inserts a sparse block matrix into a sparse matrix represented as a triplet list given the top right corner of the block and the block matrix] while preserving the sparsity pattern of the original block matrix. |
| [findValuePtrIndex](#findValuePtrIndex) | Given a row and column index into kkt_system, find the data index in the underlying kkt_system.valuePtr() array, returning -1 if it doesn't exist. !!! warning This function assumes that the KKT system is in the compressed format :material-location-enter: `row` :    row index :material-location-enter: `col` :    col_index  |

## Variable Details

### amd_iperm_vec<a name="amd_iperm_vec"></a>

!!! variable "Eigen::Matrix&lt;QDLDL_int, Eigen::Dynamic, 1&gt; amd_iperm_vec"

    AMD permutation for KKT system, reduces in-fill
    

### amd_perm_vec<a name="amd_perm_vec"></a>

!!! variable "Eigen::Matrix&lt;QDLDL_int, Eigen::Dynamic, 1&gt; amd_perm_vec"

    AMD permutation for KKT system, reduces in-fill
    

### etree<a name="etree"></a>

!!! variable "Eigen::Matrix&lt;QDLDL_int, Eigen::Dynamic, 1&gt; etree"

    Newton step for the KKT system (possibly computed with regularization)
    

### kkt_residual<a name="kkt_residual"></a>

!!! variable "Vec kkt_residual"

    Complementarity multiplier estimates for AL
    

### kkt_system<a name="kkt_system"></a>

!!! variable "SMat kkt_system"

    Penalty parameter for the augmented Lagrangian
    KKT system matrix, stored in sparse format with the structure intended to be fixed
    after it is initialize by Solver::set_problem.
    

### m_comp<a name="m_comp"></a>

!!! variable "Eigen::Map&lt;Vec&gt; m_comp"

    Inequality multipliers
    

### m_comp_est<a name="m_comp_est"></a>

!!! variable "Vec m_comp_est"

    Inequality multiplier estimates for AL
    

### m_eq<a name="m_eq"></a>

!!! variable "Eigen::Map&lt;Vec&gt; m_eq"

    Complementarity slacks (in the retraction domain)
    

### m_eq_est<a name="m_eq_est"></a>

!!! variable "Vec m_eq_est"

    Complementarity multipliers
    

### m_ineq<a name="m_ineq"></a>

!!! variable "Eigen::Map&lt;Vec&gt; m_ineq"

    Equality multipliers
    

### m_ineq_est<a name="m_ineq_est"></a>

!!! variable "Vec m_ineq_est"

    Equality multiplier estimates for AL
    

### newton_step<a name="newton_step"></a>

!!! variable "Vec newton_step"

    Diagonal scaling for KKT system, improves conditioning (ruiz equilibration)
    

### penalty_param<a name="penalty_param"></a>

!!! variable "double penalty_param"

    Relaxation parameter for the retraction map
    

### relax_param<a name="relax_param"></a>

!!! variable "double relax_param"

    Complementarity constraint residuals
    

### residual_comp<a name="residual_comp"></a>

!!! variable "Vec residual_comp"

    Inequality constraint residuals
    

### residual_eq<a name="residual_eq"></a>

!!! variable "Vec residual_eq"

    Complementarity stationarity terms
    

### residual_ineq<a name="residual_ineq"></a>

!!! variable "Vec residual_ineq"

    Equality constraint residuals
    

### s_comp<a name="s_comp"></a>

!!! variable "Eigen::Map&lt;Vec&gt; s_comp"

    Inequality slacks (in the retraction domain)
    

### s_comp_stationarity<a name="s_comp_stationarity"></a>

!!! variable "Vec s_comp_stationarity"

    Inequality stationarity terms
    

### s_ineq<a name="s_ineq"></a>

!!! variable "Eigen::Map&lt;Vec&gt; s_ineq"

    Primal variables
    

### s_ineq_stationarity<a name="s_ineq_stationarity"></a>

!!! variable "Vec s_ineq_stationarity"

    KKT residual, driven to 0 in each subproblem solve
    

### scaling<a name="scaling"></a>

!!! variable "Vec scaling"

    Inverse AMD permutation for KKT system
    

### z<a name="z"></a>

!!! variable "Eigen::Map&lt;Vec&gt; z"

    Stacked solution vector [z; s_ineq; s_comp; m_eq; m_ineq; m_comp]
    

## Function Details

### appendBlockTriplets<a name="appendBlockTriplets"></a>
!!! function "void appendBlockTriplets(std::vector&lt;Eigen::Triplet&lt;double&gt;&gt;&amp; triplets, const SMat&amp; block, int row_start, int col_start)"

    Inserts a sparse block matrix into a sparse matrix represented as a
    triplet list given the top right corner of the block and the block matrix]
    while preserving the sparsity pattern of the original block matrix.
    
    
    !!! warning
    
        This function does not check whether the elements being inserted
        already exist in the triplet list.
    
    
    :material-location-enter: `triplets`
    :    the triplet list representing the sparse matrix to be modified
        
    :material-location-enter: `block`
    :    the block matrix to be inserted
        
    :material-location-enter: `row_start`
    :    the starting row index of the block in the sparse matrix
        
    :material-location-enter: `col_start`
    :    the starting column index of the block in the sparse matrix
    

### findValuePtrIndex<a name="findValuePtrIndex"></a>
!!! function "int findValuePtrIndex(int row, int col)"

    Given a row and column index into kkt_system, find the data index in the underlying
        kkt_system.valuePtr() array, returning -1 if it doesn't exist.
    
    
    !!! warning
    
        This function assumes that the KKT system is in the compressed format
    
    
    :material-location-enter: `row`
    :    row index
        
    :material-location-enter: `col`
    :    col_index
    

