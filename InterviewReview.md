INTERVIEW REVIEW
================

This is a language-independent, high level, computer science and coding interview review.  This is intended to be used 
in conjunction with language specific reviews.   

The sections are:  
- Generic Interview Tips
- Math & Bit Manipulation Tips
- Definitions
- Big O
- Data Structures
- Algorithms
- Design Patterns
- Databases
- References & Links




GENERIC INTERVIEW TIPS
----------------------
- Never Give Up.
- Always state all assumptions, take a second to ask if assumptions are OK.
- Always create/draw examples, even if it looks easy, find all of the corner cases before you code anything.
- Think out loud, wonder out loud, explain thought process.
- Always give a naive/brute force solution first (so you have something), then attempt optimal solution.
- Separate code into different methods; it's easier to work with, and it's better to finish defining methods and SOME 
   code than not finishing ALL code in a massive method.
- For questions about languages, if you don't know, admit you don't remember, but offer to try and figure it out
   by using code examples and/or trying to remember past examples.
- Optimize when done (or stuck).
 



DEFINITIONS
-----------

#### General
- Time Complexity
    * The computational complexity that describes the amount of time it takes to run an algorithm.
- Space Complexity
    * Total space taken by an algorithm with respect to input size.
- O (big O)
    * The limiting behavior, or an upper bound, of a function when the argument tends to a particular value or infinity.
    * less than or equal to  
- Ω (big omega)
    * The same as Big O, but for lower bound.
- Θ (big theta)
    * Both Big O and Big Omega; a tight bound to describe the computation complexity of a function. 
    * NOTE: This is typically what CS/Industry people mean when they say "Big O".
- Pass By Value  
    * A local parameter is a COPY of the original argument passed in to the function.   
    * Changes made in the function to the variable does not affect original.
- Pass By Reference
    * The local parameter is the reference to the storage locations of the original argument passed in.
    * Changes to the variable in the function WILL affect the original.
    * NO copy is made, so overhead of copying (time, storage) is saved.
- Recursion
    * When a (recursive) function calls its self either directly or indirectly.
- Dynamic Programming 
    * An optimization over plain recursion.
    * A method for solving a complex problem by breaking it down into a collection of simpler sub-problems, solving 
 		each of those sub-problems just once, and storing their solutions using a memory-based DS (array, map,etc). 
	* Each of the sub-problem solutions is indexed in some way, typically based on the values of its input parameters,
 		so as to facilitate its lookup.
	* There are two different ways to store the values so that the values of a sub-problem can be reused.
		- Tabulation - Bottom up
 		- Memoization - Top Down
- Infix Notation
    * Operators are written between their operands ("normal" way).
    * Needs extra information to make the order of evaluation of the operators clear (i.e., () and order of operations).
    * Example: (A * (B + C) / D)
- Prefix Notation (Polish Notation)
    * Operators are written before their operands.
    * The order of evaluation of operators is always left-to-right, and brackets/() cannot be used to change this order. 
    * Operators act on the two nearest values on the right.
    * Example: / * A + B C D  (or with parenthesis: (/ (* A (+ B C) ) D) )
- Postfix Notation (Reverse Polish Notation)
    * Operators are written after their operands.
    * The order of evaluation of operators is always left-to-right, and brackets/() cannot be used to change this order. 
    * Example: A B C + * D /  (or with parenthesis:  ((A (B C +) *) D /) )
- Two's Complement
	* How computers store integers.
	* Positive number has a 0 as the leading or sign bit.
	* Negative number has a 1 as the leading or sign bit.
	* To convert a binary number to a binary negative number: (1) invert all bits, (2) and add 1
- Endianness
	* Refers to the order of bytes (or sometimes bits) within a binary representation of a number. 
	* In its most common usage, endianness indicates the ordering of bytes within a multi-byte number.
- Big-Endian
	* The "big end", most significant value in the sequence, is stored first (at the lowest storage address). 
- Little-Endian
	* The "little end", least significant value in the sequence, is stored first.
	* Most PCs (x86) are this way (note that ARM is bi-endian)
- Prime Number
	* A whole number greater than 1 whose only factors are 1 and itself. 
- Factor
	* A factor is a whole numbers that can be divided evenly into another number.
- Prime Factor
	* Any number in the set of prime numbers that is also a factor of (or, can be evenly divided into) a given integer. 
	* There is only one unique set of prime factors for any number.
- Hash Function
	* Any function that can be used to map data of arbitrary size to fixed-size values.
	* Values returned by a hash function are called hash values, hash codes, digests, or hashes.
- Type Erasure
	* In programming languages, type erasure refers to the load-time process by which explicit type annotations are 
 		removed from a program, before it is executed at run-time.
	* In JAVA it is used to implement generics. The Java compiler does:
 		- Replaces all type parameters in generic types with their bounds or Object if the type parameters are 
 		    unbounded. The produced bytecode, therefore, contains only ordinary classes, interfaces, and methods.
 		- Insert type casts if necessary to preserve type safety.
 		- Generate bridge methods to preserve polymorphism in extended generic types.


#### Data Structures
- Tree 
	* A data structure comprised of nodes.  
    * Each tree has a root node. 
	* The root node has zero or more child nodes.
	* Each child node has zero or more child nodes. Etc.
	* Tree DOES NOT contain cycles.
	* The nodes may or may not be in a particular order.
	* The nodes have any type of values.
	* The nodes may or may not have links back to their parents. 
- Binary Tree
	* A tree in which each node has up to two children.
- N-Ary Tree
	* A tree in which each node has up to N children.
- Binary Search Tree
	* A tree in which EVERY node follows the property: all left children <= node < all right children 
- Balanced Binary Tree
	* A binary tree balanced enough to ensure O(log n) times for insert and find. 
- Complete Binary Tree
	* A binary tree in which every level of the tree is fully filled, except the last level.
	* The last level is filled left to right.
- Full Binary Tree
	* A binary tree in which every node has either zero or two children (no node has only ONE child).
	* Doesn't need to be balanced. 
- Perfect Binary Tree
	* A binary tree that is BOTH full and complete.
	* ALL leaf nodes will be at the same level, and that level has the maximum number of nodes.
	* Will have exactly 2^k - 1 nodes, where k is the number of levels. 
- AVL Tree (Adelson-Velsky and Landis)
	* A self balancing binary search tree.
	* Maintains height of two child sub-trees.
	* If at any time children heights DIFFER by more than ONE, the tree is rebalanced via ROTATIONS.
	* Lookup, Insertion, Deletion all take O(log n) time (both average and worst case) where n is number of nodes.
- Red-Black Tree
	* A self balancing binary search tree.
	* Each node has a color (red or black) property, used to ensure the tree is approximately balanced.
	* Balancing is "good enough" to ensure an Insertion, Deletion and Lookup time of O(log n).
	* Are faster and require less memory than AVL trees.
- In-Order Traversal
	* Visit Left branch, then Current Node, then Right branch
	* When performed on a binary search tree, it visits the nodes in ascending order. 
- Pre-Order Traversal
	* Visit Current Node, then children nodes.
	* Root is always first.
- Post-Order Traversal
	* Visit Children nodes, then current node.
	* Root is always last. 
- Binary heap
	* A heap data structure that takes the form of a binary tree.
- Min-Heap
	* A complete binary tree (that is totally filled other than the rightmost element on the last level) where 
 		each node is smaller than its children. 
	* The root is the minimum element in the tree. 
- Max-Heap
	* A complete binary tree (that is totally filled other than the rightmost element on the last level) where 
 		each node is equal to or greater than its children.
	* The root is the maximum element in the tree. 
- Tries (Prefix Tree)
	* A variant of an N-Ary tree.
	* Characters are stored at each node (so each path down the tree may represent a word).
	* Uses * Nodes or "null nodes" to indicate complete words.
	* Commonly used to store an entire language for quick prefix lookups (other data types like hashes can look up 
 		words but can't say if it's a prefix of a valid word. 
- Graph
	* A collection of nodes with connections (edge) between (some of) them.
	* Can have cycles
	* NOTE: when implementing algs for graphs you need to CHECK if the node has been visited (bc there may be loops).
- Directed Graph aka Digraph aka Directed Network
	* A graph where each connection (edge) is directed from one node to another.
- Undirected Graph
	* A graph where each connection (edge) has no direction. 
- Connected Graph
	* A graph where every node is connected (there is a path between every pair of vertices).
- Acyclic Graph
	* A graph without cycles
- Spanning Tree
	* A tree that connects ALL nodes/vertices in a WEIGHTED, CONNECTED, UNDIRECTED graph.
	* Minimum Spanning Tree is a Spanning Tree with minimum weights.
- Adjacency List
	* A common way to represent a graph.
	* Every Node (vertex) stores a list of adjacent nodes (vertices).
	* In an undirected graph, an edge like (a, b) would be stored twice; once in a's and once in b's adjacent nodes.
- Adjacency Matrices
	* A NxN (usually) boolean matrix (where N is the number of nodes) where a true value at matrix[i][j] indicates
 		an edge from node i to node j.  
	* An undirected graph will be symmetric. 
- Depth-First Search
	* Start at root (or another arbitrarily selected node), and explore each branch COMPLETELY before moving on to
 		the next branch.
	* DFS is Simpler to visit every node in the graph. 
	* Can implement with recursion. 
- Breadth-First Search
	* Start at root (or another arbitrarily selected node), and explore each neighbor before going on to any of their
 		children.
	* BFS is better for shortest path.
	* NOTE: If implementing, Don't Use Recursion, use a QUEUE!
	* BigO: O(q^k) where k is number of nodes and q is path length 
- Bidirectional Breadth First Search
	* A search to find the shortest path between a source and destination node.
	* Basically, it runs two Breadth-First Searches, one at each node, colliding and forming a path. 
	* BigO: O(q^k/2 + q^k/2) where k is the number of nodes and q is path length.
	* Much better than normal Breadth-First Search!
- Hash Table
	* A Data Structure that implements a collection of key, value pairs, where the keys are mapped to the values.
	* Uses a hash function, on the key, to compute the keys index of the hash table. 
- Collision (Hash Table)
	* When two or more elements are hashed(mapped) to the same value.
	* Solutions to collisions include: Chaining Linked Lists, Chaining Binary Search Trees, Open Addressing with 
 	  Linear Probing, Open Addressing with Quadratic Probing, and Double Hashing.
- Chaining (Collision Handling) 
	* The idea is to make each cell of hash table point to a linked list of records that have same hash function value.
	* Chaining is simple, but requires additional memory outside the table.
	* Can waste space (some parts of hash table may never be used.
	* Worse cache performance BC keys are stored using linked list. 
	* Used when the number and frequency of inserts/deletes are unknown. 
	* Never fills up (we can always add more elements to chain).
- Open Addressing (Collision Handling)
	* In open addressing, all elements are stored in the hash table itself. 
	* Each table entry contains either a record or NIL. 
	* When searching for an element, we one by one examine table slots until the desired element is found or it is 
 		clear that the element is not in the table.
	* Generally requires more computation than Chaining. 
	* Better cache performance, no hash table wastage. 
	* Is used when the frequency and number of keys is known. 
	* Requires extra care to avoid clustering and load factor. 
- Double Hashing (Collision Handling)
	* Used with OPEN ADDRESSING (not Chaining).
	* Applies a second has function as an offset IFF a collision occurs. 


#### Scalability
- System Scaling
	* A system can be scaled (increased) in one of two ways; Horizontal or Vertical Scaling. 
- Horizontal Scaling
	* Increasing the number of nodes in a system.  
	* For example, adding additional servers.
- Vertical Scaling
	* Increasing the resources of a specific node.
	* For example, adding memory/processors/disk space to a server. 
- Load Balancer
	* A system to distribute a load (e.g., front end of a website) evenly so that one server doesn't crash and take the
 	  whole system offline. 
	* Could be a system of cloned servers that have essentially the same code and access to the same data. 
- Sharding (Database Partitioning)
	* Splitting data across multiple machines while ensuring you have a way of knowing what data is where. 
	* Includes: Vertical, Key-Based, Hash-Based, and Directory-Based Partitioning
- Vertical Partitioning
	* Partitioning by Feature
	* For example, a social network might have a partition for tables relating to profiles, another for messages, etc.
	* One issue is if one table gets very large, it may need to be repartitioned (possibly using a different method).
- Key-Based or Hash-Based Partitioning
	* Uses a part of the data (i.e., an ID) to partition it.
	* A simple implementation: Allocate N servers and put the data on mod(key, n)
	* One issue is that the number of servers is effectively fixed (you'd have to reallocate ALL DATA to add servers).
- Directory-Based Partitioning
	* Maintain a lookup table for where the data can be found.
	* This has two issues (1) the lookup table can be a single point of failure (2) access to table affects performance 
- Bandwidth
	* The maximum amount of data that can be transmitted in a unit of time. 
- Throughput
	* The amount of data that is transferred (successfully) in a unit of time. 
- Latency
	* How long it takes for data to go from one end to the other. 
- MapReduce
	* Used to process large amounts of data via parallel processing.
	* Has two parts:
 		- Map takes in some data and emits a <key, value> pair.
 		- Reduce takes a key and a set of associated values and "reduces" them in some way, emitting a new key & value.
 	NOTE: It's useful to think of what REDUCE should do first, then design MAP around REDUCE.
 	1. The system splits up the data across different machines.
 	2. Each machine starts running the user provided MAP program.
 	3. The MAP program takes some data and emits a <key, value> pair.
 	4. The system provided SHUFFLE process reorganizes the data so that all <key, value> pairs associated with a given 
 	   key go to the same machine, to be processed by REDUCE. 
 	5. The user provided REDUCE program takes a key and a set of associated values and "Reduces" them in some way, 
 	   emitting a new key and value.  The results of this might be fed back into the REDUCE program for more reducing.
- External Sorting
	* A class of sorting algorithms that can handle massive amounts of data. 
	* Is required when the data being sorted doesn't fit into the main memory of a computing device (usually RAM).
	* External sorting typically uses a hybrid sort-merge strategy. 
 		- Sorting Phase: chunks of data small enough to fit in memory are read, sorted, & written to a temporary file. 
 		- Merge phase: The sorted sub-files are combined into a single larger file.


#### DATABASE
- Table
	* A collection of related data held in a database. (I.e. Users, Products, or Invoices)
- Field 
	* The basic unit of data in a table (I.e., FirstName LastName in Table Users ).
- Column 
	* Another name for field, 
- Row 
	* A single set (record) of data containing all the columns in a table. 
- Record 
	* A single set (row) of data containing all the columns in a table.
- Flat File Database 
	* Stores all data in one table, results in many duplicates (bad).
- Normalization 
	* The process of structuring a Relational Database in accordance with a series of normal forms in order to reduce 
 		data redundancy and improve data integrity. 
- Join 
	*  A SQL operation to establish a connection between two or more database tables based on matching columns.
- View 
	* Is a selection of rows and columns, possible from more than one table. 
- SQL Script 
	* Script containing SQL code, usually ends in .sql.
- Primary Key 
	* Unique Identifiers (use NOT NULL PRIMARY KEY, optionally AUTO_INCREMENT).
- Foreign Key 
	* Primary Keys in another table (use FOREIGN KEY(field) REFERENCES foreign_table(field))
- Index 
	* Faster search/query time, slower update time, users cannot see indexes.
- Inner Join 
	* SQL operation that selects all rows from both participating tables as long as there is a match between the columns.
- Outer Join 
	* Returns matched and unmatched rows from one or both tables.  
- Left Outer Join 
	* Returns all rows from left and matched rows from right. 
- Right Outer Join 
	* Not used that often; Returns all rows from the right and matched rows from the right. 
- Cross Join 
	* If NO WHERE clause, it produces a result set which is the number of rows in the first table 
 		multiplied by the number of rows in the second table if no WHERE clause is used along with CROSS JOIN.
	* If WHERE clause is used with CROSS JOIN, it functions like an INNER JOIN.
- Union 
	* Combines the results of two or more SQL SELECT queries into a single table of all matching rows. 
	* The two queries must result in the same number of columns and compatible data types in order to unite.
- Stored Procedures 
	* A NAMED set of SQL statements stored in a RDBMS.
- Stored Functions 
	* A stored procedure that returns a VALUE to the environment in which it was called. 
- Triggers 
	* Is a SQL procedure that fires/initiates an action when an event (INSERT, DELETE or UPDATE) occurs. 
	* They are stored in and managed by the DBMS. 
	* Each trigger is attached to a single, specified table in the database.
- Events 
	* Tasks that execute according to a specified schedule
- Aggregate Function 
	* A function that performs a calculation on a set of values, and returns a single value. 
	* Includes Count(), Sum(), Avg(), Min(), and Max().

#### CONCURRENT
- Process Control Block (PCB) 
	* A data structure maintained by the OS for every process.  
	* Contains processes state, privileges, ID, parent pointer, CPU registers, CPU scheduling info, memory management 
 		info, accounting (CPU) info, and IO status info.
- Process 
	* An instance of a program.
	* Has complete, private set of run-time resources. 
	* Processes cannot directly communicate, but rely on interprocess comm (sockets, pipes, files, signals).  
	* Processes consist of stack, heap, data, text, and PCB.
- Thread 
	* Smallest unit of processing that can be performed in an OS. 
	* Dependent on a process, consist of a program counter, registers, stack, and state and run in shared memory space. 
	* Can directly communicate with other threads.
- Context Switching 
	* The process of storing the state of a process so that it can be restored and execution resumed from the same 
 		point later. 
- Mutex (MUTal EXclusion)
	* MUTal EXclusion or a LOCK
	* Grants exclusive-member access to a resource. 
	* USED for RESOURCE SHARING
- Semaphore 
	* N-Member (where N is a number) access to a resource, or a n-member LOCK. 
	* USED for SIGNALING. 		
- Circular Wait 
	* Two or more threads form a circular chain where each is waiting on another resource in the chain.
- Race Condition 
	* State when multiple threads try to access and modify shared resources and an inconsistent 
 		outcome occurs (due to the particular order of execution)
- Thread Starvation 
	* State where a thread is unable to gain regular access to a shared resource and is unable to make progress.  
	* Happens when shared resources are made unavailable for long periods by "greedy" threads.
- Atomic Action 
	* An action that a thread CANNOT be suspended on.
- Deadlock 
	* A state in which each member of a group is WAITING for another member, including itself, to take action, such as 
 		sending a message or releasing a lock. 
	* All of the following are required for a deadlock to occur:
 			1. MUTUAL EXCLUSION: Only one process can access a resource at a given time.
 			2. HOLD AND WAIT: Processes holding a resource can request more resources, without releasing their current resources.
 			3. NO PREEMPTION: One process cannot forcibly remove another process' resource.
 			4. CIRCULAR WAIT: Two or more processes form a circular chain where each process is waiting on another resource in the chain.
 		 NOTE: Most deadlock prevention algorithms focus on preventing CIRCULAR WAITS (4).
- Livelock 
	* Similar to Deadlock, except that the states of the processes involved constantly change with regard to one 
 		another, none progressing.  
	* Livelock is a special case of resource starvation.


#### Miscellaneous
- Birthday Paradox
	* With 23 people, there is a 50% chance that two will share the same birthday.
	* With 70 people, there is a 99.9% chance that two will share the same birthday. 
- Unified Modeling Language (UML)
    * General purpose modeling language.
    * Defines a stand way to visualize the behavior and structure of a system.
- UML State Diagram
    * Represents the condition of a system at finite states or instances of times.
    * Consists of:
        - Initial State - Black Circle - The initial state of the system.
        - Transition - Solid Arrow - Change from one state to another. Labeled with the event which cause the change.
        - State - Rounded Rectangle - Represents the conditions of an object at an instance (state) of time.
        - Fork - 1 Arrow In, Solid Rectangular Bar, 2 Arrow Out - Fork of one state to two or more concurrent states. 
        - Join - 2 Arrow In, Solid Rectangular Bar, 1 Arrow Out - Two or more concurrent states converging into one. 
        - Self Transition - Solid Arrow Back To State - An event that doesn't cause a state change. 
        - Final State - Filled Circle in Circle - Final state in a machine. 





BIG O
----- 

#### Calculating Big O
1. Calculate Total Time
    - Calculate the Total Time by adding the time of each statement applied to the input size.   
    - Add runtimes if a statement is completed before next statement. 
    - Multiply runtimes if a statement is nested in a different statement.  
2. Remove Constants
3. Drop Non-Dominant Terms


#### Rate of Increase
The following is a comparison of common Big O times for large values of n:  

Big O Time  | Classification    | Example
|:---------:|:-----------------:|:--------:|
O(1)        | Constant          | Push to Stack
O(log n)    | Logarithmic       | Binary Search
O(n)        | Linear            | Linear Search
O(n log n)  | Super-Linear      | Merge Sort
O(n^2)      | Polynomial        | Bubble Sort
O(2^n)      | Exponential       | Tower of Hanoi
O(n!)       | Factorial         | Brute Force Traveling Salesman
O(n^n)      | Apocalyptic       | 


#### Data Structure Time Complexity

Data Structure      | Avg. Get  | Avg. Search   | Avg. Add  | Avg. Del  | Worst Get | Worst Search  | Worst Add | Worst Del |    
|:-----------------:|:---------:|:-------------:|:---------:|:---------:|:---------:|:-------------:|:---------:|:---------:|
Array               | O(1)      | O(n)          | O(n)      | O(n)      | O(1)      | O(n)          | O(n)      | O(n)
Stack               | O(n)      | O(n)          | O(1)      | O(1)      | O(n)      | O(n)          | O(1)      | O(1)
Queue               | O(n)      | O(n)          | O(1)      | O(1)      | O(n)      | O(n)          | O(1)      | O(1)
Singly Linked List  | O(n)      | O(n)          | O(1)      | O(1)      | O(n)      | O(n)          | O(1)      | O(1)
Doubly Linked List  | O(n)      | O(n)          | O(1)      | O(1)      | O(n)      | O(n)          | O(1)      | O(1)
Hash Table          | N/A       | O(1)          | O(1)      | O(1)      | N/A       | O(n)          | O(1)      | O(1)
Binary Search Tree  | O(log n)  | O(log n)      | O(log n)  | O(log n)  | O(n)      | O(n)          | O(n)      | O(n)
B-Tree              | O(log n)  | O(log n)      | O(log n)  | O(log n)  | O(log n)  | O(log n)      | O(log n)  | O(log n)  
Red-Black Tree      | O(log n)  | O(log n)      | O(log n)  | O(log n)  | O(log n)  | O(log n)      | O(log n)  | O(log n)
AVL Tree            | O(log n)  | O(log n)      | O(log n)  | O(log n)  | O(log n)  | O(log n)      | O(log n)  | O(log n)


#### Sorting & Searching Time/Space Complexity

Algorithm               | Best Time     | Avg. Time     | Worst Time    | Worst Space
|:---------------------:|:-------------:|:-------------:|:-------------:|:-----------:|
Binary Search           | O(1)          | O(log(n))     | O(n log(n))   | O(log(n))
Quick Sort              | O(n log(n))   | O(n log(n))   | O(n^2)        | O(log(n))    
Merge Sort              | O(n log(n))   | O(n log(n))   | O(n log(n))   | O(n)
Bubble Sort             | O(n)          | O(n^2)        | O(n^2)        | O(1)
Insertion Sort          | O(n)          | O(n^2)        | O(n^2)        | O(1)
Selection Sort          | O(n^2)        | O(n^2)        | O(n^2)        | O(1)
Depth First Search      | O(V + E)      | O(V + E)      | O(V + E)      | O(V)
Breadth First Search    | O(V + E)      | O(V + E)      | O(V + E)      | O(V)
Topological Sort        | O(V + E)      | O(V + E)      | O(V + E)      | O(V + E)
Dijkstra's Alg          | O(V + E)      | O(E log(V))   | O(V^2)        | O(V + E)
Bellman-Ford Alg        | O(V + E)      | O(V + E)      | O(V + E)      | O(V + E)
Floyd-Warshall Alg      | O(V^3)        | O(V^3)        | O(V^3)        | O(V^2)




DATA STRUCTURES
---------------

#### Stacks
- A linear data structure where the order is 'first in last out' (FILO).  
- Implementation:
    1. Node (Linked List) Class
        - value - Pointer to object of the items in the st
        - next - Pointer to next node in the stack.  
    2. Built-in Array
- Members:
    * top - The top node of the stack or null/none.
    * size - The number of nodes in the stack.
- Methods:
    * push(value) - Adds an item onto the stack.
    * peek() - (or top()) Returns the last item pushed onto the stack.
    * pop() - Removes and returns the top, or most recently pushed, item from the stack.
    * is_empty() - True if no more items can be popped and there is no top item.
    * is_full() - True if no more items can be pushed.
    * get_size() - Returns an integer number of elements on the stack.
- Applications:
    * Backtracking (or accessing the most recent data element in a series of elements, i.e., page history, 'undo')
    * Infix to Postfix/Prefix Conversion
    * Tower of Hanoi, Tree Traversal
    
    
#### Queues
- A linear data structure where the order is 'first in first out' (FIFO).  
- Implementation Variations:
    1. Node (Linked List) Class
        - value - Pointer to object of the items in the st
        - next - Pointer to next node in the stack.  
    2. Built-in Array
- Members:
    * first - The first node of the queue or null/none.
    * last - The last node (most recently) item in the queue. 
    * size - The number of nodes in the queue.
- Methods:
    * enqueue(value) - Adds an item onto the stack.
    * dequeue() - Removes and returns the first, or longest queued, item from the queue.
    * peek() - Returns the first, or longest queued, item from the queue.
    * is_empty() - True if no more items can be dequeued and there is no first item.
    * is_full() - True if no more items can be pushed.
    * get_size() - Returns the number of elements on the queue.
- Applications:
    * Breath First Search
    * Shared Resources
    * Asynchronous Transfers


#### LinkedLists
- A linear data structure, in which the elements are not stored at contiguous memory locations
- Each node had at least one pointer to the next node in the data structure. 
- Implementation Variations:
    * Singly Linked - Each node has just one pointer to the next node in the list; tail's next value is always null/none.
    * Doubly Linked - A singly linked list with an additional pointer (previous) that points to the previous node.
    * Circular Linked - A doubly linked list where the tails next points to the head of the list. 
- Node Class
    * data - The data that the node holds. 
    * next - The next node in the list.  Circular only: the last nodes next will point to the head node.
    * previous - Doubly and Circular only: The previous node in the list.
- Members
    * head - The first node.
- Methods
    * add(value) - Adds an item to the end of the list.
    * remove(value) - Removes an item from the list.
    * is_empty() - True if head is null/none.
    * get_size() - Returns the number of nodes in the list.
- Applications:
    * Used in stack, queue, and graphs implementations. 


#### HashTables
- A data structure that implements an associative array abstract data type, a structure that can map keys to values. 
- Uses a hash function, that when given a key, computes an index or hash code.
- A Collision is when the hash of two different keys map to the same index.
- Implementation Variations:
    1. Chaining
        * Solution to collision issue; each cell of an array points to a linked list.
        * Node Class
            - Key - The key to be used to access the value via the hash function.
            - Value - The value associated with the key.
            - Next - Points to the next node in the chain or null/none.
    2. Open Addressing 
        * Solution to collision issue; values are stored at the computed index of the array, or some offset from the 
          index if that index is occupied.
        * NOTE: Both the key and the value need to be stored in the array (as tuple or obj) because the hash function 
          can map multiple inputs to one output.
- Members:
    * array[] - The array containing nodes (non-linked node if open addressing, linked list node if chaining).
    * capacity - The size of the array.
    * size - The number of key, value pairs in the hash table.
    * load_factor - Used with resizing; the ratio of size/capacity at which the hash table will be resized. 
- Methods:
    * get_index(key) - The hash function that when given a key of any size will provide an index of fixed size. 
    * add(key, value) - Adds a key value pair to the hash table.
    * remove(key) - Removes the key, value pair from the hash table.
    * get(key) - Returns the value associated with the key.
    * update(key, value) - Updates the value associated with the key.
    * get_size() - Returns the number of key, value pairs in the hash table.
- Applications:
    * Associative Arrays
    * Search Trees
    * Non-Digit Indexing
    * Sets
    

#### Graphs
- A non-linear data structure consisting of nodes and edges which represent a connected pair of nodes.
- Or, a collection of nodes with connections between (some of) them.
- Can be directed or undirected.
- Can contain isolated sub-graphs.
- Can have cycles.
- Implementation Variations:
    1. Adjacency List
        * Most common way to represent graph.
        * Every vertex/node stores a list/array of adjacencies/neighbors.  
        * Node Class:
            - name - Name of the vertex/node in the graph.
            - adjacencies[] - Aka children/neighbors, List/array of adjacencies node is connected to (may contain weight).
            - state - (Optional) An enum representing state (visiting/visited/unvisited) 
            - visited - (Optional) A boolean to indicate if a vertex/node has been visited in a traversal/search. 
    2. Adjacency Matrices 
        * Graph contains an NxN matrix (where N is the number of vertexes), where a true/1 at matrix[i][j] represents an 
          edge from i to j.
- Members:
    * vertices[] - (if adjacency list) - A list/array/set of vertieces/nodes objects.
    * adjMatrix[] - (if adjacency matrices) - An NxN representation of the graph.  
- Methods:
    * add_node(name) - Add vertex/node with given name. 
    * add_edge(node1, node2) - Adds edge from node1 to node2, optionally may contain weight. 
    * get_node(name) - Returns the node object with a given name or null/none.
    * has_node(name) - The hash function that when given a key of any size will provide an index of fixed size. 
- Applications:
    * Used to represent physical structures (roads, pipelines, etc.)
    * Used to represent networks or abstract connections (internet, friends network, family tree, work hierarchy). 


#### Trees
- A non-linear data structure consisting of a root node with one or more children (nodes).
- Each child may have on ore more children (nodes).
- May NOT HAVE cycles. 
- NOTE: For interviews, it's simpler/cleaner to NOT wrap the nodes in a tree class--just use nodes!
- Implementation Variations:
    * Trie or Prefix Tree - An N-ary reTRIEval tree, where characters are stored at each node.
    * Binary Trees - A tree in which each node has a MAX of 2 children.
    * Binary Search Trees - A binary tree (typically without duplicates) with the ordering property: 
                            For each node n, all left descendants >= n < all right descendants.
    * AVL/Red-Black Tree - Self balancing binary search tree.
    * Complete Binary Tree - A bin tree in which every level is fully filled, except (optionally) the last level.
    * Max/Min Heap - A complete binary tree where every node is greater/smaller than its children.
        - Insert a new node in the last level, then "fix" or bubbled it to the correct place (to maintain order).
        - ExtractMax/Min a max/min node, then replace it with the last node (last level), then bubble it to correct place.
- Node Class:
    * name - Name, or value, of the node in the tree.
    * children[] - (if not binary tree) - The list/array of children nodes of current node. 
    * left - (if binary tree) - The left child node.
    * right - (if binary tree) - The right child node. 
    * null_node - Flag or node value to indicate a completed word. 
- Members:
    * root - The root node of the tree.
- Methods:
    * insert(node) - Inserts a node in the tree.
    * delete(node) - Deletes the node from the tree.
    * find(value) - Finds a node with a given value or null/none.
    * get_height(node) - Gets the height of the node in the tree.
- Applications:
    * To store hierarchical data (i.e., XML/HTML).
    * Pattern matching.




ALGORITHMS
----------

#### Russian Peasant Algorithm
 - How to multiply two numbers (a, b) without using the multiplication operator (*).  
    ```
    Add(a: int, b: int) -> int:    
        res := 0
        while b > 0:
            if b % 2 == 1:
                res := res + a
            a := a * 2
            b := b / 2
        return res 
    ```
 
#### Sieve of Eratosthenes 
 - Finds all prime numbers from 2 to a given limit n.  
    ```
    Eratosthenes(n: int) -> []:
        boolean A[2...n] := true
        for i := 2, i < sqrt(n), i++:
            if A[i] == true:
                for j := 2 * i, j < n, j + i:
                    A[j] := false
        return all i in A[i], if A[i] == true
    ```

#### Euclidean or Euclid's Algorithm (GDD)
- Computes the greatest common divisor (GCD) of two numbers; or the largest number that divides both without remainder.
    ```
    Euclid(a: int, b: int) -> int:    
        while b != 0:
            temp := b
            b := a % b
            a := temp
        return a
    ```
    
#### Pollard's Rho (Prime Factorization Alg)
- Algorithm for integer factorization; or the decomposition of a composite number to a product of smaller numbers.
    ```
    g(x: int, n: int) -> int:
        return (x^2 + 1) % n 
  
    Pollard(n: int) -> int:  
        x := 2
        y := 2
        factor := 1
        while factor == 1:
            x := g(x, n)
            y := g(g(y, n), n)
            factor := gcd(abs(x - y), n)
        return factor if d != n else none
    ```        

#### Towers of Hanoi:  
- Puzzle with three rods and n disks, each atop a larger disk, on one rod.
- The objective is to move the stack of disks to another rod, with the following constraints:
    1. Only one disk can be moved at a time.
    2. Each move consists of taking the top disk from one stacks and placing it on top of another stack or empty rod.
    3. Larger disks can not be placed on top of smaller disks.
    ```
    Hanoi(n: int, A: stack, C: stack, B: stack):
        Hanoi(n-1, A, B, C)
        C.push(A.pop())
        Hanoi(n-1, B, C, A)
    ```    

#### Floyd Cycle Detection
- Detects a cycle in a sequence of (node) values.
- Uses two pointers, initially, one moves at twice the 'speed' than the second.
- Can return the first repetition (rep) and the length (len) of the shortest cycle (starting at rer).
    ```
    f(x: node) -> node:
        return x.next
  
    Floyd(start: node) -> node, int:
        p1 := start
        p2 := start
        while p1 != p2:
            if p1 is null:
                return null, -1
            p1 := f(f(p1))
            p2 := f(p2)
        
        rep := 0
        p2 := start
        while p1 != p2:
            p1 := f(p1)
            p2 := f(p2)
            rep := rep + 1

        len := 0
        p1 := f(p2)
        while p1 != p2:
            p1 := f(p1)
            len := len + 1
            
        return rep, len
    ```
		
#### Quick Select/Selection Rank Algorithm (to find the kth smallest/largest number in a list or array;)
- Select the kth smallest element in an unordered list.
- Similar to Quick Sort (uses same partition alg); however, after finding the pivot, it only recurs on the part with k.
- Runtimes: Average is O(n), Worst is O(n^2), and Best is O(n)
- Space Complexity: O(log(n))
    ```
    QuickSelect(list: list, k: int):
        return QuickSelect(list, 0, len(list) - 1, k)
    
    
    QuickSelect(list: list, l: int, r: int, k: int):
        if 0 < k <= r - l + 1:
            index := Partition(arr, l, r)
            if index - l == k - 1:
                return list[index]
    
            if index - l > k - 1:
                return QuickSelect(list, l, index - 1, k)
            return QuickSelect(list, index + 1, r, k - index + l - 1)
        return null
    
    
    Partition(list: list, l: int, r: int):
        pivot := list[r]
        i := l
    
        for j in range(l, r):
            if list[j] <= pivot:
                list[i], list[j] := list[j], list[i]
                i := i + 1
    
        list[i], list[r] := list[r], list[i]
        return i
    ```

#### Rabin-Karp Algorithm (Substring Search)
- Rabin-Karp alg is a hash optimized substring pattern (p) search of a string (s). 
- Average runtime is O(s + b), and a worst case runtime is O(sp)		
- Brute Force Substring Search takes O(p(s-p)) time where s is len(substring) and b is len(string).
- Uses a ROLLING HASH; a hash function that uses the previous hash value to compute next hash value in linear time.
- NOTE: The following uses a bad rolling hash function, in practice use Rabin fingerprint or a good hash function.
	```
    Rabin-Karp(s[1...n]: string, p[1...m]: string) -> int:
        hp := hash(p[1...m])
        
        for i = 1, i < n - m + 1, i++:
            hs := hash(s[i..i+m-1])
            if hp == hs:
                if s[i...i+m-1] == p[1..m]:
                    return i
        return null
    ```
		
#### Bubble Sort
- Sorting algorithm that iteratively compares adjacent items in a list. 
- Runtimes: Average is O(n^2), Worst is O(n^2), and Best is O(n)
- Space Complexity: O(1)
- Sorts in place, and is stable (does not change the relative order of elements with equal keys.
    ```
    BubbleSort(l: list):
        n := len(l)
        swapped := true
        while swapped == true:
            swapped := false
            for i from 1...n:
                if l[i - 1] > l[i]
                    l[i - 1], l[i] := l[i], l[i - 1]
                    swapped := true
            n := n - 1
    ```

#### Insertion Sort
- Simplistic sorting algorithm.  
- Runtimes: Average is O(n^2), Worst is O(n^2), and Best is O(n)
- Space Complexity: O(1)
- Sorts in place and is stable (does not change the relative order of elements with equal keys)
- Is online sort (can sort a list as it receives it)
    ```
    InsertionSort(l: list):
        s := size(l)
        for i from 1 to s:
            key := l[i]
            j = i - 1
            while j >= 0 and key < l[j]:
                l[j + 1] := l[j]
                j := j - 1
            l[j + 1] := key
    ```

#### Selection Sort
- Simplistic sorting algorithm.  
- Runtimes: Average is O(n^2), Worst is O(n^2), and Best is O(n^2)
- Space Complexity: O(1)
- Sorts in place, is not stable (changes the relative order of elements with equal keys)
    ```
    SelectionSort(l: list):
        n := len(l)
        for i from 1...n:
            min_i = i
            for j from i+1...n:
                if l[min_i] > l[j]:
                    min_i := j
            l[i], l[min_i] := l[min_i], l[i]
    ```

#### Quick Sort
- Simplistic sorting algorithm.  
- Runtimes: Average is O(n log(n)), Worst is O(n^2), and Best is O(n log(n))
- Space Complexity: O(log(n))
- Sorts in place, is not stable (changes the relative order of elements with equal keys)
    ```
    QuickSort(l: list):
        QuickSort(l: list, 0, len(l) - 1)
    
    QuickSort(l: list, lo: int, hi: int):
        if lo < hi:
            p := Partition(l, lo, hi)
            Quicksort(l, lo, p - 1)
            Quicksort(l, p + 1, hi)

    Partition(l: list, lo: int, hi: int) -> int:
        pivot := l[hi]
        i := lo
        for j from lo...hi
            if l[j] < pivot
                l[i], l[j] := l[j], l[i]
                i := i + 1
        l[i], l[hi] = l[hi], l[i]
        return i
    ```

#### Merge Sort
- Decent sorting algorithm.  
- Runtimes: Average is O(n log(n)), Worst is O(n log(n)), and Best is O(n log(n)).
- Space Complexity: O(n).
- Does NOT sort in place but is stable (does not change the relative order of elements with equal keys).
    ```
    alg MergeSort(l: list):
        mid := len(l) / 2
        left := l[0...mid]
        right := l[mid...len(l)]

        MergeSort(left)
        MergeSort(right)

        i, j, k := 0

        while i < len(left) and j < len(right):
            if left[i] < right[j]:
                l[k] := left[i]
                i := i + 1
            else:
                l[k] := right[j]
                j := j + 1
            k++

        while i < len(left):
            l[k] := left[i]:
            i := i + 1
            k := k + 1

        while j < len(right):
            l[k] := right[j]
            j := j + 1
            k := k + 1
    ```

#### Topological Sort
- Orders a list of nodes such that if edge(a, b) is in the graph, a will be ordered before b in the list.
- Graph MUST be directed.
- Graph CAN NOT have cycles.
- Used for scheduling jobs or tasks with dependencies (jobs are nodes, dependencies are edges).
- Used for data serialization. 
- NOTE: Requires the count of each nodes INBOUND edges; most nodes typically store outbound.
    ```
    topological_sort(n: int, edges[n][n]: list[list]):
        L := list()
        Q := queue()
        visited := list[n]
        inbound := list[n]
        
        for i from 1...n
            inbound[i] := 0
            visited[i] := false

        for i from 1...n:
            for j from 1...n:
                if edges[i][j] == true:
                    inbound[j] := inbound[j] + 1

        for i from 1...n:
            if inbound[i] == 0:
                Q.enqueue(i)
                visited[i] := true

        while Q is not empty:
            i := Q.dequeue()
            L.append(i)
            for j from 1...n:
                if edges[i][j] == true and visited[j] == false:
                    inbound[j] := inbound[j] - 1
                    if inbound[j] == 0:
                        Q.enqueue(j)
                        visited[j] := true
        return L
    ```
  
#### Binary Search
- Searches for an element (x) in a SORTED array.
- Runtimes: Average is O(log(n)), Worst is O(log(n)), and Best is O(1)
- Space Complexity: O(1)
    ```
    BinarySearch(l: list, x: int):
        low := 0
        high := len(arr) - 1
        while low <= high:
            mid := (low + high) / 2
            if l[mid] < x:
                low := mid + 1
            else if l[mid] > x:
                high := mid - 1
            else:
                return mid
        return null
    ```

#### In-Order Tree Traversal
- Visit left branch, current node, then right branch.
- When used on BST, visits the nodes in ascending order.
- Used to FLATTEN a tree.
    ```    
    Visit(n: node) -> arbitrary function on n
  
    InOrder(n: node):
        if n != null:
            InOrder(n.left)
            Visit(n)
            InOrder(n.right)
    ```

#### Pre-Order Tree Traversal
- Visits current node before children (root is visited first).
- Used to create a COPY of a tree.
- Used to get a PREFIX expression of an expression tree.
    ```    
    Visit(n: node) -> arbitrary function on n

    PreOrder(n: node):
        if n != null:
            Visit(n)
            PreOrder(n.left)
            PreOrder(n.right)
    ```

#### Post-Order Tree Traversal
- Visits current node AFTER children (root is visited last).
- Used to DELETE a tree.
- Used to get POSTFIX expression of an expression tree.
    ```    
    Visit(n: node) -> arbitrary function on n

    PostOrder(n: node):
        if n != null:
            PostOrder(n.left)
            PostOrder(n.right)
            Visit(n)
    ```

#### Breath First Tree Traversal
- Starting at root, visits each level of the tree.
- NOTE: Because trees are graphs without cycles, there is no need to mark a node as visited.
    ```
    Visit(n: node) -> arbitrary function on n

    BreathFirst(n: node):
        h := height(n)
        for i from 1...h:
            BreathFirst(n, i)
            
    BreathFirst(n: node, i: int):
        if n == null:
            return
        if i == 1:
            Visit(n)
        else:
            BreathFirst(n.left, i - 1)
            BreathFirst(n.left, i - 1)
    ```

#### Depth First Search
- Searches (or traverses) trees and graphs.
- Used for solving puzzles with only one solution (such as mazes).
- Used for Topological Sorting/Scheduling. 
- NOTE: Because graphs can have cycles, there must be a check if the node has been previously visited. 
    ```
    Visit(n: node) -> arbitrary function on n
    
    DFS(n: node):
        if n == null:
            return
        Visit(n)
        n.visited := true
        
        for node a in n.adjacent:
            if a.visited == false:
                DFS(a)
    ```

#### Breadth First Search
- Searches (or traverses) trees and graphs.
- Used for finding shortest paths.
- NOTE: Because graphs can have cycles, there must be a check if the node has been previously visited. 
- NOTE: Implemented via QUEUE, NOT RECURSION. 
    ```
    Visit(n: node) -> arbitrary function on n

    BFS(n: node):
        Q := queue()
        n.visited := true
        Q.enqueue(n)
        while not Q.empty:
            n := Q.dequeue()
            Visit(n)
            for node a in n.adjacent:
                if a.visited == false:
                    a.visited := true
                    Q.enqueue(a)
    ```        

#### Dijkstra's Algorithm
- Finds the shortest/minimum weight path from a start node s, to EVERY node in a weighted directed graph.
- Graph must be directed.
- Graph must be weighted with POSITIVE values only.
- Graph CAN have cycles.
    ```
    Dijkstra(g: graph, source: vertex) -> list, list:
        S := set()
        dist := list[len(g)]
        prev := list[len(g)]      
        for each node n in graph:             
            dist[n] := infinity                  
            prev[n] := null                 
            Q.add(n)                      
        dist[source] := 0                        
        
        while S is not empty:
            u := node in S with min u.weight                                  
            S.remove(u) 
            for each neighbor v of u:
                alt := dist[u] + length(u, v)
                if alt < dist[v]:               
                    dist[v] := alt 
                    prev[v] := u 
        
        return dist[], prev[]
    ```

#### Bellman-Ford Algorithm
- Computes shortest/minimum weight path from a start node s, to EVERY other node in a weighted directed graph.
- Graph must be directed, weighted (positive and negative values are OK), and CAN have cycles.
- Slower than Dijkstra's, but more versatile.
    ```
    BellmanFord(vertices: list, edges: list, source: vertex) -> list, list:
        dist := list[]
        pred := list[]
        for each vertex v in vertices:
            dist[v] := inf
            pred[v] := null
        dist[source] := 0
    
        for i from 1...size(vertices)−1:
            for each edge (u, v) with weight w in edges:
                if dist[u] + w < dist[v]:
                    dist[v] := dist[u] + w
                    pred[v] := u
    
        for each edge (u, v) with weight w in edges:
            if dist[u] + w < dist[v]:
                return null
        
        return dist[], pred[]
    ```

#### Floyd-Warshall algorithm
- Finds shortest paths in WEIGHTED graph, with positive & negative edge weights with ONLY POSITIVE cycles.
- Best for dense graphs (most or all nodes are connected), (if sparse use Dijkstra's).
    ```
    Floyd-Warshall(nodes: list) -> list, list: 
        s := size(graph)
        dist[s][s] := infinity
        next[s][s] := null
        
        for each edge(n, m) in each node in graph:
            dist[n][m] := edge(n,m).weight
            next[n][m] := m
        
        for each node n in graph:
            dist[n][n] := 0
            next[n][n] := n
  
        for k from 1...s:
            for i from 1...s:
                for j from 1...s:
                    if dist[i][j] > dist[i][j] + dist[k][j]:
                        dist[i][j] = dist[i][j] + dist[k][l]
                        next[i][j] = next[i][k]
  
        return dist[], next[]
    ```




DESIGN PATTERNS
---------------
#### Singleton
Ensures that at most only one instance of an object exists throughout application.
- Consider a Singleton when all three requirements present:
    * Control concurrent access to a shared resource.
    * Access to the resource will be requested from multiple, disparate parts of the system.
    * There can only be one object. 
- Examples:
    * Logging
    * Service locators


#### Factory
The factory design pattern defines an interface for creating an obj, but let subclasses decide which class to instantiate.  
This pattern delegates the responsibility of initializing a class from the client to a particular factory class by 
creating a type of virtual constructor.  
The created objects are accessed using a common interface.
- Consider using a Factory when:
    * A class cannot anticipate the type of objects it needs to create beforehand.
    * A class requires its subclasses to specify the objects it creates.
    * You want to localize the logic to instantiate a complex object.
- Examples:
    * java.util.Calendar, ResourceBundle and NumberFormat getInstance() methods uses Factory pattern
    * valueOf() method in wrapper classes like Boolean, Integer etc


#### Builder
The Builder design pattern separates the construction of a complex object from its representation. 
By doing so the same construction process can create different representations.
- Consider using the Builder Pattern when:
    * When the process of creating an object is extremely complex, with many mandatory and optional parameters. 
    * When an increase in the number of constructor parameters leads to a large list of constructors.
    * When client expects different representations for the object that's constructed.




PROGRAMMING LANGUAGES
---------------------

#### Every Day Syntax
For each language you plan to use in an interview, make sure you don't forget the syntax to these common operations:
- Formatting
- Decimal <=> Binary Conversion
- Lambda
- Map, Filter, Reduce
- User IO
- File IO (Open, Read, Write, Create, Delete)
- REGEX 
- Math Functions (Log, Square Root, Floor, Ceiling)
- String Manipulation (list <--> string, replace, replace all, find, substring, upper/lower, isdigit, isalpha, etc.)
- Random Numbers
- Threads/Threading 


#### Basic Functions
Know how to implement the following functions in each of your languages:
- IsPrime
- Fibonacci
- Factorial


#### Data Structures
Know how to use your languages built in data structures; know how to make them, know how to use them, know their 
advantages and their disadvantages.  

Furthermore, know how to implement each of the following data structures in your language(s):
- Stacks
- Queues
- LinkedLists
- HashTables
- Graphs
- Trees
- Trie (Prefix Trees)
- BST

#### Algorithms
Are you familiar enough with your languages that you would be able to implement all of the algorithms from the 
ALGORITHMS section above?





DATABASES
---------

#### NoSQL
- Non-Relational or Distributed Databases
- Syntax Varies (sometimes called UnQL or Unstructured Query Language) 
- Dynamic schema/model for unstructured data (key:value pairs, documents, text, etc.)
- No Join
- Document with lines of data
- Horizontally Scalable
- Brewers CAP Theorem Mentality (Consistency, Availability, and Partition tolerance)
- NOT GOOD for Complex Query
- GOOD for Hierarchical Data Storage and Large Data Sets	
- NOT AS GOOD at High Load/Traffic
- Examples: MongoDB, Redis, Cassandra


#### SQL
- Relational Databases (RDBMS)
- uses SQL language
- Standard schemas/model (tables: of n rows by m columns)
- Vertically Scalable
- ACID Mentality (Atomicity, Consistency, Isolation, and Durability)
- GOOD for Complex Query
- NOT GOOD for Hierarchical Data Storage
- GOOD for High Load/Traffic
- Examples: MySQL, SQLite, Postgres, MS-SQL


#### SQL Command Categories
- Data Query Language (DQL)
    * SELECT - Retrieve data from table(s).
- Data Manipulation Language (DML)
    * INSERT - Insert data into db table.
    * UPDATE - Update data in db table.
    * DELETE - Delete data from table.
- Data Definition Language (DDL)
    * CREATE - Create db object (table, view, etc.)
    * ALTER - Modify db object (table, view, etc.)
    * DROP - Delete db object (table, view, etc.)
-Data Control Language (DCL)
    * GRAND - Assign privilege.
    * REVOKE - Remove privilege. 
    
    
#### Basic SQL Command Syntax
- Create table:
    ```
    CREATE TABLE <Table Name>
    ( Column1 DataType, 
            ...
      ColumnN DataType  )
    ```
- Select data from a table:
    ```
    SELECT <Column List>
    FROM <Table Names>
    WHERE <Search Condition>
    ```
- Insert data in a table:
    ```
    INSERT INTO <Table Names>
    (<Column Name List>) VALUES (<Values>)
    ```
- Update data from a table:
    ```
    UPDATE <Table Name>
    SET <Column1>=<Value1>, <Column2>=<Value2>, ...
    WHERE <Search Condition>
    ```
-  Delete data from a table:
    ```
    DELETE FROM <Table Name>
    WHERE <Search Condition>
    ```
- Group and Order data from tables:
    ```
    SELECT <Column List>, <Aggrgate Function>(<Column Names>) AS <Aliased Name>
    FROM <Table Name>
    WHERE <Search Condition>
    GROUP BY <Column List>
    HAVING <Condition> 
    ORDER BY <Column List> DESC
    ```
- Joining data from multiple tables:
    ```
    SELECT <Table1>.<Table1Column>, <Table2>.<Table2Column>, <Table3>.<Table3Column>
    FROM <Table1> 
    INNER JOIN <Table2>
    ON <Table1>.<Table1Column>=<Table2>.<Table2Column>
    INNER JOIN <Table3>
    ON <Table3>.<Table3Column>=<Table2>.<Table2Column>
    ```
- Union, or combine, the results of two selects (both table fields must be same order, #, and type, different names OK):
    ```
    SELECT <Column List> FROM FROM <Table Name1>
    UNION  
    SELECT <Column List> FROM FROM <Table Name2>    
    ```
- Replace 'null' with 0:  
    ```
    SELECT COALESCE(<Column Name>, 0) <Table Name>
    ```

#### HOW TO DESIGN A DATABASE
1. Think of the Real World Example to derive the schema from.
2. Create A Entity Relationship Diagram (ERD)
    - Entity - __Rectangle__ - An object or concept, can self-link via Action.
	- Weak_Entity - __Double Rectangle__ - Entity that cannot be identified by its own attributes; must use foreign key 
	  in addition to one of its attributes to form a primary key. 
	- Relationship - __Diamond__ - Shows how two entities interact (VERB).
	- Attribute	- __Oval__ - A unique characteristic of an Entity.
	- Primary Key - __Underlined Oval__ - A min set of attributes that uniquely specify a row in a table. 
	- Derived Attribute - __Dashed Oval__ - An attribute that can be calculated (derived) from other attributes.
	- Multi-Valued Attribute - __Double Oval__ - Multi-Valued Attribute (i.e. multiple types of phone numbers).
	- Cardinality - __Lines connecting Entities__ - 1:1 one to one, 1:N one to zero or more, M:N 0 or more to 0 or more.
3. Create The Schema
	1. Map Regular Entities To Tables - CREATE new TABLE for ENTITY with fields being its ATTRIBUTES.
	2. Map Weak Entities To Tables - CREATE new TABLE for ENTITY with fields being its ATTRIBUTES. PRIMARY KEY should be 
	                                 partial key of the WEAK ENTITY plus owners PRIMARY KEY.
    3. Map Binary 1:1 Relationships - Add PRIMARY KEY from one ENTITY as FOREIGN KEY in other ENTITY.
	4. Map Binary 1:N Relationships - Add 1's side PRIMARY KEY as a FOREIGN KEY on the N side. 
	5. Map Binary M:N Relationships - CREATE new TABLE where its PRIMARY KEY is a combination of both ENTITIES PRIMARY 
	                                  KEYS, add any ATTRIBUTES as fields. 
4. Reduce Redundant Data (Normalizing Databases) 




MATH & BIT MANIPULATION TIPS
----------------------------
TODO TODO TODO --- Reread CCI chapter 6 (pg 117) and add probability and other missed stuff here. 
- abs(a) = (a^2)^0.5
- ceil(a/b) = (a+b-1) // b
- f(x) = 0 if x == 0 else 1  === ceil(x^2 / (x^2 + 1))
- x^m * x^n === x^m+n
- x^m / x^n === x^m-n
- x^-n === 1 / x^n
- log_b k = c === b^(c) = k
- log_b x = log_a x / log_a b (change of base formula)
- log(xy) = log x + log y
- log(x/y) = log x - log y
- y = mx + b where m is slope and b is y-intercept
- slope (m) = y2 - y1 / x2 - x1 where (x1, y1) and (x2, y2) are points representing two lines. 
- sum 0-n = n(n + 1) / 2
- num of permutations of n unique items = n!  (permutations are ordered)
- num of permutations of len(k) of n unique items = n!/(n - k)!  (permutations are ordered)
- num of combinations of k items from n unique items === n!/k!(n - k)! === (n choose k) (combinations are NOT ordered)
- Quadratic Formula === ax^(2) + bx + x --> x = [-b +- sqrt(b^2 - 4ac)] / 2a
- union(A, B) === A + B - intersection(A, B)
- a set of size n has 2^n subsets. 




REFERENCES & LINKS
------------------

#### Big O
[Algorithm Big Os](https://thejjjunk.ucoz.com/algorithms)  
[Big-O Complexity Chart](http://www.souravsengupta.com/cds2016/lectures/Complexity_Cheatsheet.pdf)


#### DAILY STUDY
[LeetCode Problems](https://leetcode.com/problemset/all/)  
[coderbyte Challenges](https://www.coderbyte.com/challenges)  
[GeeksForGeeks Data Structure/Algorithms/Company-Specific Practice](https://practice.geeksforgeeks.org/)  
[codility Lessons](https://app.codility.com/programmers/lessons/1-iterations/)  


#### INTERVIEW QUESTIONS (WEBPAGE)
[Java Multithreading Questions](https://javarevisited.blogspot.com/2014/07/top-50-java-multithreading-interview-questions-answers.html)
[Java Lock/Synchronization Questions](https://javarevisited.blogspot.com/2017/02/10-java-wait-notify-locking-and-synchronization-Interview-Questions-Answers.html)





















