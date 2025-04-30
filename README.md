# test_constraints

## Questions about constraints:

- the first 3 constraints are working as expected and are just added to reduce the amount of solutions

### Question 1:
```!F Exists (?x) 'Aluminium'(?x)```

This constraint should eliminate all solutions that use 'Aluminium' as a type. However, Aluminium is still being used as a possible input.
When I use the predefined constraint ```nuse_t``` it works. Why is the SLTLx version of that constraint not working?

### Question 2:
```!F Exists (?x) Exists (?y) ((<'CalculateVacancyFormationEnergy'(?x,?y;)> true) & !R(?y,?x))```

The goal with this constraint is to make sure that the two inputs for 'CalculateVacancyFormationEnergy' originate from the same structure. This is the case in [solution 1](test_constraints/solution/Figures/candidate_workflow_1.png) but not in [solution 3](test_constraints/solution/Figures/candidate_workflow_3.png). However, it seems to me that some types are not being recognized / correctly evaluated by the formula.\
I was testing this with the following formula:\
```!F Exists (?x) ((<'CreateStructure'(;?x)> true) & (F Exists (?y) ((<'CalculateVacancyFormationEnergy'(;?y)> true) & (R(?x,?y)))))```\
In my opinion, this should lead to 0 solutions, because the output of 'CalculateVacancyFormationEnergy' will always be derived from an output of 'CreateStructure'. However, it seems to have no effect on the solutions. When I insert the tool 'CreateProject' instead of 'CreateStructure' the formula has the expected outcome of 0 solutions. Why is this the case?
