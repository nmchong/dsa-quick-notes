#### Traversals: 
1) Pre-Order (Root, Left, Right): 
	1) Useful for problems where you need to process a node before its children
	2) Things like creating a copy of a tree or serialization
2) In-order (Left, Root, Right): 
	1) Primary property is that it visits nodes in a Binary Search Tree ([Trees]) in sorted order. 
	2) Critical fact for BST validation and search problems. 
3) Post-order (Left, Right, Root): 
	1) Perfect for "bottom-up" calculations. 
	2) Use when you need to compute information from both the left and ridge children before you can process the parent node. Foundation of many hard LeetCode problems. 
		1) Example: find the diameter of a tree or checking if a tree is balanced requires knowing the results from the children first.
4) Advanced Recursion and Divide and Conquer: 
	1) Be comfortable defining a recursive helper that returns multiple pieces of information.
	2) Example: The "Binary Tree Maximum Path Sum" problem, your recursive function can't just return the max path sum from a sub tree, it needs to return the max path sum that can be extend upwards to the parent while updating a global maximum with paths that cannot extend upwards.

#### Specialized Tree Data Structures and Algorithms:
1) Tries (Prefix Trees): 
	1) When a problem involves a dictionary of words, prefixes or a string match, Tries are often the optimal data structure.
	2) Know how to build a trie: 
2) Segment Trees: 
	1) If you see a problem that involves performing range queries (e.g. finding the sum/min/max of a subarray) and updating values, a Segment tree is a powerful tool. While the
3) Lowest Common Ancestor: 
	1) BST: 
		1) Use DFS and use properties of BST to find lowest common ancestor
		2) Set node p to lowest and node q to highest value nodes.
		3) If root.val < p.val, i.e. the p value is greater than the root, or the lower of the two is greater than the root, check the right side
		4) Else if root.val > q.val, i.e. the q value is less than the root, or the higher of the two is less than the root, check the left side.
		5) Return the node if it the value is between the two.
	2) Regular Binary Tree: 
		1) Use DFS to search recursively on each branch of the nodes.
		2) if root == p or q, then you would return the root
		3) You would do recurse for the left and right side, returning the root if both p and q are found
		4) Otherwise return left or right result as both of p and q would be on that side.
```
class Solution:

	def lowestCommonAncestor(self, root: 'TreeNode', p: 'TreeNode', q: 'TreeNode') -> 'TreeNode':

		if not root: 
			return None
			
		if root == p or root == q: 
			return root
			
		left_result = lowestCommonAncestor(root.left, p,  q)
		right_result = lowestCommonAncestor(root.right, p, q)
		
		if left_result and right_result: 
			return root
		
		return left_result or right_result
```
1) Tree Serialization and Deserialization: 
	1) Converts a tree into a string or array representation and then rebuilding the tree from the representation. 
	2) Use pre-order to encode the tree, the using pre-order to decode the tree by calling the root, building it as a node, then recursively calling on the children



