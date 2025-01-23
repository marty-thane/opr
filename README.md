# Optimální rozhodování

## Online solvery

- [AtoZmath.com](https://cbom.atozmath.com/Menu/CBomMenu.aspx)

## Videa

### PERT/CPM

- Critical path: [ODKAZ](https://youtu.be/-TDh-5n90vk)
- Crashing: [ODKAZ](https://youtu.be/zYnyGU9WSCk)

## Kódy

Níže naleznete MWE (*minimal working example*) optimalizace v Pythonu a MATLABu.

### PuLP

```
from pulp import *

prob = LpProblem(sense=LpMaximize)

x1 = LpVariable("x1", lowBound = 0)
x2 = LpVariable("x2", lowBound = 0)

prob += 2*x1 + 5*x2

prob += 3*x1 + 2*x2 >= 6
prob += 2*x1 + x2 <= 2
print(prob)

stat = prob.solve()
print(f"STATUS\n{LpStatus[stat]}\n")

print("SOLUTION")
for var in prob.variables():
    print(f"{var.name} = {var.varValue}")
print(f"z = {prob.objective.value()}")
```

### MATLAB

```
prob = optimproblem("ObjectiveSense", "maximize");

x1 = optimvar("x1", "LowerBound", 0);
x2 = optimvar("x2", "LowerBound", 0);

prob.Objective = 2*x1 + 5*x2;

prob.Constraints.c1 = 3*x1 + 2*x2 <= 6;
prob.Constraints.c2 = 2*x1 + x2 <= 2;

show(prob)

[sol,fval] = solve(prob);

disp(sol)
disp(fval)
```

