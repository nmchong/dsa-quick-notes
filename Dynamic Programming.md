A fancy term for recursion with memory. It is used where a naive recursive solution would be too slow because it re-computers the same subproblems over and over again. DP Stores the results of the subproblems so you only have to compute them once

### Key Properties of DP problems: 
1) Overlapping Subproblems: 
	1) When a problem can be broken down into smaller subproblems that are used multiple times.
2) Optimal Substructure: 
	1) The optimal solution to the overall problem can be constructed from the optimal solutions of its subproblem. 
	2) Example: the shortest path from point A to point C is the shortest path from A to B plus B to C

### Two Techniques: Memoization Vs. Tabulation: 
1) Memoization (Top-Down):
	1) You write a standard recursive function, but at the beginning of the function, you check if you've already solved this exact subproblem. If you have, you return the stored answer. If not you compute the answer, store it in a cache (like a hash map or an array), and then return it 
		1) Pros: Often easier to write and understand because it follows the natural logic of the problem
		2) Cons: Can lead to stack overflow on very deep recursion
2) Tabulation (Bottom-Up):
	1) Iterative and avoids recursion. You create a table (1D or 2D, often named dp) and fill it out from the bottom up, starting with the smallest, known base cases. Each entry dp[i] in the table is build on the previous entries (e.g., dp[i-1], dp[i-2])
		1) Pros: Faster (no recursion overhead) and avoids stack overflow. It can also open up opportunities for space optimization.
		2) Cons: Can be harder to reason about, as you need to figure out the correct order to fill out the table

### Framework for Solving any DP Problems: 
1) Recognize it is a DP Problem: 
	1) Look for keywords and problem types: 
		1) Find the min/max cost/profit/value...
		2) Find the number of ways to...
		3) Find the longest/shortest...
		4) Is it possible to reach a certain state?
		5) Problems involving decisions at each step that will affect future choices
2) Define the state: 
	1) "State" is a set of parameters that uniquely identify a subproblem. 
	2) What should you store in your dp table.
		1) 1D DP: The state is usually dp[i], For example, dp[i] could be maximum profit you can make up to day i
		2) 2D DP: The state is often dp i j where dp i j. could be the length of the longest common subsequence using the first i characters of string 1 and the first j characters of string 2
3) Write the Recurrence Relation (The transition): 
	1) This is the formula that relates the solution of a bigger problem to its subproblems. 
	2) Ask yourself: How do i solve for dp[i] using the states I have already computed (like dp [i- 1], dp [i - 2], etc.)
4) Identify the Base Cases: 
	1) Typically the smallest subproblems that you can solve directly, without recursion. The starting points for your dp table
