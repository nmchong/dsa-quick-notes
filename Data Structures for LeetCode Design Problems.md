
### Hash Maps (Dictionaries)
A data structure that stores key-value pairs, allowing for extremely fast retrieval of a value given its key.

Key Properties: 
1) Key-Value Pairs: Stores data as keys, which are used to look up associated values
2) Fast Lookups: Uses a hash function to compute an index into an array of buckets, or slots, from which the desired value can be found. Provides an average O(1) performace
3) Unordered: The keys are generally not stored in any specific order

When to Use: 
1) Use for caching, indexing or any scenario requiring quick lookups (i.e. checking for duplicates, counting frequencies)
2) Use them anytime you need to get something by its key instantly

Time Complexity: 
1) Access = O(1) on average
2) Insertion = O(1) on average
3) Deletion = O(1) on average
---
### Linked Lists
A linear data structure where elements are linked using pointers rather than being stored in contiguous memory locations

Key Properties: 
1) Node-Based Structure: Each element, or node, contains data and a pointer to the next node in the sequence. A doubly linked list node also points to the previous node.
2) Dynamic Size: The list can grow and shrink during execution
3) Sequential Access: You must traverse the list from beginning (the head) to access elements

When to use: 
- Ideal when you need frequent insertions and deletions in the middle of a sequence
- They are the foundation for more complex data structures like LRU Cache, where the ability to reorder nodes in O(1) time is critical

Time Complexity: 
Access (by index) = O(n)
Search (by value) = O(n)
Insertion / Deletion (at beginning) = O(1)
Insertion / Deletion (in middle with pointer) = O(1)
Insertion / Deletion (at end) = O(n) (or O(1) if a tail pointer is maintained)

---
### Trees
Used to represent hierarchical data, but different types are optimized for specific problems. 

Key Types: 
1) Trie (Prefix Trees): The go-to structure for any design problem involving strings, prefixes and auto-completion.
2) Balanced Binary Search Trees (BSTs): Use these when you need to keep data sorted while performing fats insertions, deletion and lookups (e.g., AVL or Red-Black Trees). 
	1) Usually don't need to implement the balancing from scratch, but must know when a structure with these guarantees is needed.

Time Complexity: 
1) Balanced BSTs: 
	- Access (search) = O(log n)
	- Insertion  = O(log n)
	- Deletion = O (log n)
2) Tries (Where k is the length of the key): 
	- Access (search) = O(k)
	- Insertion = O(k)
---
### Heaps (Priority Queues)
A tree-based data structure that satisfies the heap property, always keeping the minimum (min heap) or maximum (max heap) element at the top. 

Key Properties: 
1) Heap Property: in a min-heap, a parent node is always smaller than its children. Using heapq (python), heaps will always be min-heap, so if you want a max-heap, set the values to negatives.
2) heapq.heappush(heap, val) is used for adding an element
3) heapq.heappop(heap) is used to remove the smallest or largest element

When to use: 
1) Essential when you need repeated, efficient access to min or max element in changing collection
2) Critical for algorithms like Dijkstra's shortest path or finding the k-th largest element in a stream.
3) Use Python's heapq module for an efficient min_heap implementation

Time Complexity: 
1) heapq.heappush(heap, val) (add an element) = O(log n )
2) heapq.heappop(heap) (remove the min element) = O(log n)
3) heap[0] (look at the min element) = O(1)
---
### Queue
A collection that follows a First-In, First-Out (FIFO) principle. I.e. the first item added is the first item to be removed.

Key Characteristics:
1) FIFO order: elements are processed in the order they were added
2) Key Operation: list.append() (add to the back) and list.popleft() (remove from the front)

When to use: 
- Queues are essential for algorithms when you neeed to process items level by level or in a specific order. 
- Use collections.deque for efficient implementation

Time Complexity (using a deque):
- append (add to back) = O(1)
- popleft (remove from front) = O(1)
- q.[0] (look at front) = O(1)
---
### Sets
Unordered collection of unique elements. 

Key Characteristics: 
1) Mutable: You can add or remove elements
2) Unordered: Elements are not stored in any specific sequence.
3) No Duplicates: Each element must be unique

When to use it : 
- Use a set when you need to quickly check for the presence or absence of an item or when you need to remove duplicates from a collection. Go-to for tracking visited nodes in a graph search or finding unique items.

Time Complexity: 
- Search (contains)  = O(1)
- Insertion | O(1)
- Deletion | O(1)

---
### Lists
An ordered, mutable collection of elements

Key Characteristics:
1) Mutable: You can change, add or remove elements
2) Ordered: Elements maintain their position (index)
3) Duplicates Allowed: Can contain the same elements multiple index

When to use: 
- The most common data structure. Use it when you need a flexible collection of items that you can modify and access by their index

Time Complexity: 
- Access (by index) = O(1)
- Search (by value) = O(n)
- Insertion / Deletion (end) | O(1)
- Insertion / Deletion (middle) | O(n)
---
### Tuples
An ordered, immutable collection of elements

Key Characteristics:
1) Immutable: Once created, it cannot be changed
2) Ordered: Elements maintain their position (index)
3) Duplicates allowed: Can contain the same element multiple items

When to use: 
- Use a tuple when you have a small, fixed collection of related item that should not be modified, like coordinates (x, y) or a function that need to return multiple fixed values. 
- Because they are immutable, they used as keys in a dictionary (whereas lists cannot)

Time Complexity: 
- Access (by index) = O(1)
- Search (by value) = O(n)
