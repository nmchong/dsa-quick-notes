Searches refers to algorithms designed to find a specific piece of data
# Breadth First Search
Explores a graph or tree level by level. It uses a queue to keep track of the next nodes to visit.
#### Key Idea: 
- Explore a tree layer by layer expanding outward from the source
#### Data Structure: 
- Uses a Queue (FIFO)
#### Best For: 
- Trees: 
	- any problem that organizes or analyzes nodes by their depth
	- Key Terms: Level by Level, Nodes at depth k, minimum depth, right / left side view, zigzag level order
- Graphs: 
	- General algorithm for BFS on a graph: 
		- 1) Initialization:
			- Create a queue and add a starting node to it. 
			- Create a visited set and add the starting node to it, prevents from going in infinite loops 
		- 2) Loop: 
			- Continue until the queue is empty
			- Remove the front most node from the queue, call it current_node
			- Do whatever you need for the node, add neighbors, but check if you visited the neighbors yet
---
# Depth First Search
Explores a graph or tree as far down a branch as possible before backtracking. 
It can be implemented using recursion or an explicit stack call.
#### Key Idea: 
- Goes deep first, explores a path to its conclusion before trying another
#### Data Structure: 
- Mainly recursion or a Stack (LIFO)
#### Best For: 
- Connectivity: Determining if a path exists between two nodes
- Cycle Detection: Determines if there is a cycle in the graph
- Topological Sort: Ordering nodes in a directed acyclic graph (DAG)
- Pathfinding (any path): simply finding a path, not necessarily the shortest
- Exhaustive Search: Exploring all possible solutions, often the basis for backtracking
---
# Dijkstra's Algorithm: 
Used for finding the shortest path in a weighted graph where all edge weights are non-negative. A modified BFS that prioritizes exploring the node with the smallest known distance from the source.
#### Key Idea: 
- A greedy approach, each step visit the unvisited node with the smallest know distance from the start
#### Data Structure: 
- Priority Queue (Min-Heap) to efficiently retrieve the node with the minimum distance
#### Best For: 
- Finding the shortest path in networks like road systems, computer networks or any problem modeled as a graph with positive costs.
---
# Binary Search
An algorithm used to find a target value within a sorted collection of elements
Key advantage is its speed, having a O(log n) run time. 
#### Key Idea: 
- Search space is sorted or have a monotonic property (e.g. if a value x is a valid answer, all values greater than x are also valid)
- Complexity: O(log n) time , O(1) space
#### Best For:
- Finding an element in a sorted array
- Search on the answer: When you can guess on an answer and verify if it is "too high" or "too low", binary search for the optimal answer. 
#### Algorithm: 
1) Initialization: 
	- Set two pointers, left and right, left = 0 right = len(list)
	- Set mid = (left + right) // 2
2) Compare: 
	- Check if array[mid] == target: 
	- if target is smaller than array[mid] , the target must be in the left half so you set right = mid - 1
	- If target is larger than array[mid], the target must be in the right half, so you set left = mid + 1
3) Repeat: 
	-  Repeat step 2 until you find the target
---
# Modified Binary Search: 
Adaptation of the regular binary search so it can be used to find more than the first or last occurrence of a number in a list.

The core idea of halving the search space is still the same, just updates the logic for updating left and right pointers to fit the unique problem.
#### Common problems for Modified Binary Search: 
1) Finding first or last occurrence of an element in an array with duplicates 
	1) When trying to find the first occurrence, if array[mid] == target, don't stop the binary search. 
	2) Keep track of the index of mid as a potential first occurrence and then set right = mid - 1 and check again in the new list
	3) If you want to find the last occurrence, do the opposite, by setting the left = mid + 1 and keeping track of the index
2) Searching in a rotated sorted array: 
	1) A problem where the array has been sorted and then rotated to a pivot point.
	2) Logic: 
		1) After finding the mid element, compare it to the left boundary, i.e. array[left]
		2) if array[left] <= array[mid], the left half is guaranteed to be sorted
			1) Otherwise right half must be sorted
		3) Once you know which half it is in, you check if your target lies within that sorted range. If it is there, you search there, otherwise you search in the other unsorted half.
3) Finding a peak element: 
	1) A peak element is an element larger than its neighbors, left and right
	2) The array will not be sorted, but there are peaks and valleys which give a usable property
	3) Logic: 
		1) You can determine which way to go by looking at the slope
		2) Compare nums[mid] with its right neighbor nums[mid + 1]
		3) if nums[mid] < nums[mid + 1],  you are on an "upward slope", so a peak must exist to the right. (search left = mid + 1)
		4) Otherwise, you are on a downward slope, so the peak must exist to the left. search (right = mid)
4) Search on the Answer Problems:
	1) Large category of problems where you don't search on input array, but rather the range of possible answers.
	2) Square Root of X (integer): 
		1) Problem: find the integer square root of a number x without using built in functions
		2) Why modify?: You are searching for a number, not looking through an existing array
		3) The Modification: The search space is the range of integers from 0 to x. You binary search for a number mid, such that mid * mid <= x. if   mid * mid is too large, you search the lower half. Else you search the upper half 
	3) Split Array Largest Sum: 
		1) Given an array of numbers and an integer m, split the array into m continuous subarrays. Your goal is to minimize the largest sum amongst these subarrays
		2) Modification: You binary search on the answer, the possible values for the "minimized largest sum"
			1) The search space is from the largest single number in the array to the total sum of the array
			2) For a guess sum mid, you have a helper function to check: "is it possible to split the array into m subarrays such that no subarray's sum exceeds mid?
			3) If it is possible, try for a better (smaller) sum (right = mid - 1)
			4) If not, you need to allow for a larger sum (left = mid + 1)
---
# Back Tracking
A problem solving technique that systemically tires all possible paths to find a solution. You follow one path, if you hit a dead end, you "backtrack" to the last intersection and try a different path.

Basically a refined DFS approach to brute force. Instead of going through every combination, it builds a solution and abandons a path as soon as it determines it cannot lead to a valid solution.

### Core Idea: Choose, Explore, Un-Choose
1) Choose: Make a choice. Add an element to your current solution. 
2) Explore: Recurse, call the function again with the updated state to explore further possibilities down this path. 
3) Un-Choose: This is the "backtrack" step, undo the choice you made in Step 1. Crucial because it allows you to explore other paths from the same decision point

### When to use Backtracking: 
1) "Find all possible combinations"..
2) "Generate all possible permutations'..
3) "Return all subsets..."
4) Solve this puzzle 
5) Problems that be modeled as finding a path on a grid or in a decision tree

### General Template For LeetCode backtracking

```
def solve(input_data):
    results = []  # Store all valid solutions
    current_path = [] # Store the current combination/permutation being built

    def backtrack(start_index, other_params...):
        # 1. Base Case: Have we found a valid solution?
        if is_a_solution(current_path):
            results.append(list(current_path)) # Add a copy!
            return

        # (Optional) Other stopping condition
        if should_stop_exploring(current_path):
            return

        # 2. Iterate through all possible "next choices"
        for choice in available_choices(start_index, ...):

            # (Optional) Pruning: Skip invalid choices early
            if not is_valid(choice):
                continue

            # 3. Choose
            current_path.append(choice)

            # 4. Explore
            backtrack(new_start_index, ...) # Recurse with the new state

            # 5. Unchoose (The actual "backtrack")
            current_path.pop()

    # Initial call to start the process
    backtrack(0, ...)
    return results
```