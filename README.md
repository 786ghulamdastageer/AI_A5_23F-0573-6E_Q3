# AI_A5_23F-0573-6E_Q3
This is Sudoko game using CSP.

Sudoku CSP Solver
A Complete Constraint Satisfaction Problem Implementation
Overview
This project implements a Sudoku solver using Constraint Satisfaction Problem (CSP) techniques. The solver uses three main algorithms:

AC-3 (Arc Consistency Algorithm) - Preprocesses domains before search

Backtracking Search - Systematically explores possible assignments

Forward Checking - Prunes neighbor domains after each assignment

MRV Heuristic - Selects variable with minimum remaining values

The solver can handle Sudoku puzzles of varying difficulty levels (Easy, Medium, Hard, Very Hard).

Problem Formulation
Sudoku is formulated as a CSP with the following components:

Component	Description
Variables	81 cells (each empty cell needs a value)
Domains	{1, 2, 3, 4, 5, 6, 7, 8, 9} for each empty cell
Constraints	Each row, column, and 3×3 box must contain digits 1-9 exactly once
Solution	Complete assignment where all 81 cells have values satisfying all constraints
Algorithms Explained
1. AC-3 (Arc Consistency Algorithm)
Purpose: Reduce search space before backtracking begins

How it works:

Put all arcs (constraints between variables) in a queue

While queue is not empty:

Take an arc (Xi, Xj) from queue

Remove values from Xi's domain that have no support in Xj

If Xi's domain changed, add all arcs (Xk, Xi) back to queue

If any domain becomes empty, no solution exists

Time Complexity: O(n × d³) where n = variables, d = domain size

2. Backtracking Search
Purpose: Find a valid assignment for all variables

How it works:

If all variables assigned, return solution

Select unassigned variable (using MRV heuristic)

Try each value in variable's domain

If value is consistent with current assignments:

Assign value

Recursively search

If recursion succeeds, return solution

If fails, backtrack (undo assignment)

3. Forward Checking
Purpose: Prune invalid values early

How it works:

After assigning a value to a variable

Identify all peers (same row, column, box)

Remove the assigned value from each peer's domain

If any peer's domain becomes empty → assignment invalid

Store pruned values to restore on backtracking

4. MRV Heuristic (Minimum Remaining Values)
Purpose: Choose most constrained variable first

How it works:

Select variable with smallest domain size

This reduces branching factor

Detects failures earlier

Board File Format
Each board file contains 9 lines, each with 9 digits:

0 represents empty cell

1-9 represent fixed numbers
