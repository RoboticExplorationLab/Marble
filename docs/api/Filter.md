---
generator: doxide
---


# Filter

**class Filter**



## Functions

| Name | Description |
| ---- | ----------- |
| [Filter](#Filter) | Construct a new Filter object  |
| [sufficient_progress](#sufficient_progress) | Determine if a candidate point makes sufficient progress with respect to feasibility and merit decrease compared to an entry in the filter :material-location-enter: `candidate` :    Candidate filter entry :material-location-enter: `entry` :    Existing filter entry to compare against :material-keyboard-return: **Return** :    std::pair<bool, bool> Pair indicating whether sufficient progress is made in feasibility, merit decrease, respectively  |
| [candidate_acceptable](#candidate_acceptable) | Determine if a candidate point is acceptable compared to an existing entry in the filter. |
| [candidate_dominated](#candidate_dominated) | Determine if a candidate point is dominated by an existing entry in the filter. |
| [acceptable](#acceptable) | Determine if a candidate point is acceptable compared to any entry in the filter. |
| [update](#update) | Add a new entry to the filter and remove any entries that are dominated by the new entry :material-location-enter: `new_entry` :    New filter entry to add  |
| [clear](#clear) | Clear all entries from the filter  |

## Function Details

### Filter<a name="Filter"></a>
!!! function "Filter()"

    Construct a new Filter object
    

### acceptable<a name="acceptable"></a>
!!! function "bool acceptable(const Entry&amp; candidate)"

    Determine if a candidate point is acceptable compared to any entry in the filter. Defined as making either
        sufficient feasibility progress or sufficient merit decrease compared to any entry in the filter.
    
    
    :material-location-enter: `candidate`
    :    Candidate filter entry
        
    :material-keyboard-return: **Return**
    :    true Candidate is acceptable
        
    :material-keyboard-return: **Return**
    :    false Candidate is not acceptable
    

### candidate_acceptable<a name="candidate_acceptable"></a>
!!! function "bool candidate_acceptable(const Entry&amp; candidate, const Entry&amp; entry) const"

    Determine if a candidate point is acceptable compared to an existing entry in the filter. Defined as making either
        sufficient feasibility progress or sufficient merit decrease compared to any entry in the filter.
    
    
    :material-location-enter: `candidate`
    :    Candidate filter entry
        
    :material-location-enter: `entry`
    :    Existing filter entry to compare against
        
    :material-keyboard-return: **Return**
    :    true Candidate is acceptable
        
    :material-keyboard-return: **Return**
    :    false Candidate is not acceptable
    

### candidate_dominated<a name="candidate_dominated"></a>
!!! function "bool candidate_dominated(const Entry&amp; candidate, const Entry&amp; entry) const"

    Determine if a candidate point is dominated by an existing entry in the filter. Defined as not making sufficient
        progress in either feasibility or merit decrease compared to the existing entry.
    
    
    :material-location-enter: `candidate`
    :    Candidate filter entry
        
    :material-location-enter: `entry`
    :    Existing filter entry to compare against
        
    :material-keyboard-return: **Return**
    :    true Candidate is dominated
        
    :material-keyboard-return: **Return**
    :    false Candidate is not dominated
    

### clear<a name="clear"></a>
!!! function "void clear()"

    Clear all entries from the filter
    

### sufficient_progress<a name="sufficient_progress"></a>
!!! function "std::pair&lt;bool, bool&gt; sufficient_progress(const Entry&amp; candidate, const Entry&amp; entry) const"

    Determine if a candidate point makes sufficient progress with respect to feasibility and merit
    decrease compared to an entry in the filter
    
    
    :material-location-enter: `candidate`
    :    Candidate filter entry
        
    :material-location-enter: `entry`
    :    Existing filter entry to compare against
        
    :material-keyboard-return: **Return**
    :    std::pair<bool, bool> Pair indicating whether sufficient progress is made in feasibility, merit decrease, respectively
    

### update<a name="update"></a>
!!! function "void update(const Entry&amp; new_entry)"

    Add a new entry to the filter and remove any entries that are dominated by the new entry
    
    
    :material-location-enter: `new_entry`
    :    New filter entry to add
    

