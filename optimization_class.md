![class](out/problems/problems.png)

- A name for the most top class? (`OptimizationProblem`, `CombinatorialProblem`, or something)
- How handle an optimization model. `get_qp()` or `get_docplex()`?
- how to call a class which does not use graph (non "GraphProblem" class)
    - We can have SetProblem for non "GraphProblem" classes?
- Currently, each problem has their own function to return a solution e.g. `max_cut_value()`. We can have something like `get_solution()` to output the solution (The output format should depend on the problem e.g. True/False for a decision problem. Subsets for a set problem)?
- `get_graph_solution` in `GraphProblem` class is to visualize a graph based on a solution with networkx. For example, for maxcut, it paints each node in two colors.
- to_ising() //maybe we don't need this since we can convert a problem with converters

## Use cases
- We can call `OptimizationProblem.to_qp()` to get a `QuadraticProblem` from each problem class. For example, for max cut, it should be as follows.
```
max_cut = MaxCut() 
qp = max_cut.to_qp()

qaoa_mes = QAOA()
qaoa = MinimumEigenOptimizer(qaoa_mes)
qaoa_result = qaoa.solve(qp)
print(qaoa_result)
```