# Data Structures

## Terminology

### Data Structure

A description of a means of collecting multiple data items in a singular thing. It will define a series of valid operations that can be used to manage the data within the structure, and usually there a trade off between the complexity of the operations that can be executed, the performance of those operations.

### Static vs Dynamic

Arrays (including multi-dimensional) are **static**, they are declared to be of a specific size, and the programming environment does not permit changes to that size. This can be highly performant, but less flexible.

Other structures like Linked Lists allow for data to be added and removed during runtime, but usually at the cost of memory fragmentation and performance.

### Data Type

Any variables, or data items in a program, will be of a specific data type. Some structures allow their data to be of mixed types (heterogenous), others require all data items to be of the same type (homogenous). You need to be familiar with the following data types:

* Integer - whole number
* Float - Number with fractional part
* Boolean - True/False value
* Character - A single text character
* String - piece of text
* Date - Often given it's own data type, or encapsulated as a record

## Warning on Programming Languages

For your A Level, you have to have an understanding of the following data types. OCR (and AQA) have specific ideas about what each of these data structures mean and the operations that a programmer can carry out on them.

Programming language have varying support and behaviour for these data types, often using different terminology, and not necessarily operating under the same constraints. I have attempted to provide demonstration code in various programming languages, specifically looking for the best fit, but don't be alarmed if you see variations in what OCR says an 'array' can do and what it can actually do in Python/JavaScript.

Data type support also varies across languages, C has several different types of number (according to the size) and floating point numbers are handled distinctly, whereas JavaScript just lumps all numbers together as _number_.

Languages such as Python and JavaScript sit a little higher over the memory than languages like C, so often their data structures are more dynamic.

{% embed url="https://computersciencewiki.org/index.php/Abstract_data_structures" %}
This topic is also covered on the Computer Science Wiki
{% endembed %}

## Array

A **fixed** size set of data items, stored contiguously in memory.

Arrays are 'fixed' data structures, once created they do not generally change size. All items in the array will be of the same data type, therefore each taking the same amount of memory.

* Advantage: Random elements can be accessed quickly
* Disadvantage: The list cannot be extended, beyond the fixed number of items known at its creation.

Python and JavaScript both allow their arrays to be used dynamically, so they are really lists. To show you what a fixed array looks like, here is an example in C.

{% embed url="https://repl.it/@MarlingSharp/array-c#main.c" %}

## Multi-Dimensional Array

Arrays can be nested (arrays of arrays) to create multi-dimensional arrays. This can be used to represent 2D or 3D structures.

Here is a simple program that defines a couple of multi-dimensional arrays, just to show the syntax of declaring them and addressing their data.

_Note that TypeScript allows arrays to be dynamic, the same example in C would require the size of the arrays to be fixed at declaration._

{% embed url="https://repl.it/@MarlingSharp/multi-dim-array-ts#index.ts" %}

## Record

A record can be used to associate a set of values as a single entity. For example a game object might have the following properties:

* Name - String
* Lifespan - integer
* Position - Vector
* Velocity - Vector
* Acceleration - Vector

Or a student might have the following properties

* Name - string
* Age - integer
* Subjects - array of strings

Typescript allows us to specify the properties required by a type of record using _interfaces_ and _objects_. Different programming languages will use different terminology here, but for your A Level, you need to recognise the word Record and understand that it means a set of values _of different data types_ collected as a single thing.

Here is an example that creates a Student interface in TypeScript, then creates a single object, then an array of those objects. Python does not really have a concept of Record.

{% embed url="https://repl.it/@MarlingSharp/record-ts" %}

## Tuple

Tuples are a way of putting multiple data items (of different types) together in a **fixed** structure. TypeScript/JavaScript does not really have a concept of Tuples, but Python uses them fairly extensively.

Here is an example of using Tuples to return multiple values from a function. It also creates a series of Tuples and demonstrates how Python allows de-structuring of Tuples in loops.

{% embed url="https://repl.it/@MarlingSharp/tuple-py#main.py" %}

## Queue

This is a list of items with a First In First Out logic. There are two key operations

* Enqueue - Place an item on the queue
* Dequeue - Remove an item from the queue, using FIFO

Here is a TypeScript implementation

{% embed url="https://repl.it/@MarlingSharp/queue-ts#index.ts" %}

## Stack

A stack places items into a dynamic structure with a Last In First Out. There are two key operations:

* Push - Place an item on the stack
* Pop - Remove an item from the stack, using LIFO

Here is an implementation in TypeScript

{% embed url="https://repl.it/@MarlingSharp/stack-ts#index.ts" %}

## Linked List

Each item contains a pointer to the next item in the list. This allows us to create new items and simply point to the new locations in memory.

* Advantage: The list items can be stored anywhere in memory, the structure is highly dynamic.
* Disadvantage: Random access slow, the only way to find items is to a navigate the pointers.

An implementation in TypeScript can be found here, together with a simple program that shows it in operation.

{% embed url="https://repl.it/@MarlingSharp/linked-list-ts#index.ts" %}

## Hash Table

A hash table attempts to solve both problems, by allocating a fixed array of Linked Lists. When adding items to a hash table, a hash value is calculated for the item, that hash is used to generate an index into the array. The item is then appended to the linked list at that index.

* Advantage - Random access is quicker, the hash effectively narrows down the values to search through to a small proportion of the overall data structure
* Advantage - The structure is dynamic, so items can be easily added and removed
* Disadvantage - A poorly written hash function, or low capacity, can lead to clustering, where lots of items resolve to the same key value and end up with roughly the same problem as a plain linked list.

There is a demonstration of this data structure here:

{% embed url="https://repl.it/@MarlingSharp/hash-table-ts#index.ts" %}

## Binary Tree

This is a tree structure, but each node can only have 2 children, and the Left and Right children have specific relationships with their parent node. Most often the left branch is 'less than' and the right branch contains nodes that are 'more than' (one side is arbitrarily picked to host 'equal to' nodes).

When values are added to a binary tree, they are placed by deciding if the new node is 'less than' or 'greater than' each node. Once it reaches a leaf node, it attaches itself at the appropriate point.

### Traversal Algorithms

Once a binary tree has been built, there are three traversal algorithms that one must be aware of:

* In-Order - Visit the left branch, then the node, then the right branch.
* Pre-Order - Visit the node, then left branch, then right branch
* Post-Order - Visit the left branch, right branch, then the node.

Here is an implementation of the Binary Tree data structure, and those three traversal algorithms

{% embed url="https://repl.it/@MarlingSharp/binary-tree-ts#index.ts" %}

## Graph

Graph's look a lot like trees, in that nodes are connected by links, but there are a couple of key differences.

* Graphs permit links between any given nodes, so there can be loops and there can be more than 2 links going out from any given node.
* Relationships between nodes can be specialised in the following ways
  * Weighted - Given some numerical value, this could relate to strength of relationship, or the physical distance between two navigation points.
  * Directed - The link only goes in one specific direction, social graphs might show person A following B, but B does not follow A.

Whilst potentially confusing, there is a special type of Graph that is called a Tree. A Tree is a graph that does not contain any loops. This is distinct from a Binary Tree, since any node can have any number of children. A Binary Tree limits you to two links, and each link is in a specific order.

### Traversal Algorithms

Once you have built a graph, there are a couple of traversal algorithms which you can use. Traversal algorithms have the following characteristics:

* They require a start vertex to be nominated when invoked
* They should visit every node that is connected to the start node (direct or transitively)

The two algorithms are:

* Depth First Search - Drill down a branch until you hit a leaf node, then double back and find the next path to go down. Repeat until all links have been exhausted. Uses a Stack to implement.
* Breadth First Search - Visit the node, then all its children, then all their children, radiating outwards until all links exhausted. Uses a Queue to implement.

One thing to note, there isn't usually a 'single correct answer' for the output of these traversals. Since for any given node the edges can be traversed in any order, there are usually multiple potential correct outputs for each traversal algorithm.

An implementation of Graph and it's two traversal algorithms can be found here

{% embed url="https://repl.it/@MarlingSharp/graph-ts#index.ts" %}
