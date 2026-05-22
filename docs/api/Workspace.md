---
generator: doxide
---


# Workspace

**class Workspace**



## Variables

| Name | Description |
| ---- | ----------- |
| [kkt_system](#kkt_system) | KKT system matrix, stored in sparse format with the structure intended to be fixed after it is initialize by Solver::set_problem.  |

## Functions

| Name | Description |
| ---- | ----------- |
| [appendBlockTriplets](#appendBlockTriplets) | Inserts a sparse block matrix into a sparse matrix represented as a triplet list given the top right corner of the block and the block matrix] while preserving the sparsity pattern of the original block matrix. |
| [findValuePtrIndex](#findValuePtrIndex) | Given a row and column index into kkt_system, find the data index in the underlying kkt_system.valuePtr() array, returning -1 if it doesn't exist. !!! warning this function assumes that the KKT system is in the compressed format :material-location-enter: `row` :    row index :material-location-enter: `col` :    col_index  |

## Variable Details

### kkt_system<a name="kkt_system"></a>

!!! variable "SMat kkt_system"

    KKT system matrix, stored in sparse format with the structure intended to be fixed
    after it is initialize by Solver::set_problem.
    

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
     this function assumes that the KKT system is in the compressed format
    
    
    :material-location-enter: `row`
    :    row index
        
    :material-location-enter: `col`
    :    col_index
    

