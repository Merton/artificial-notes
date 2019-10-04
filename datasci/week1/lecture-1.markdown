# Lecture 1

## What is an algorithm?
Its a well-defined procedure that takes a value or set of values as **input** 


One function in an interface may be implemented by many different algorithms

## Why do we need to consider algorithms carefully in data sci?

- We want to process large volumes of data as quickly as possibly
- How many seconds, minutes, hours or days will it take to process the data?
- How much of the data do we need in main memory at the same time?
- How much disk storage do we need? How fast can we access it?
- How can we speed processing up? Will adding another "Node" mean processing speeds up or slows down?

## Data types
- Programming languages typically support a number of atomic data types:-
    - Integer
    - Foating point number
    - String
    - CHaracter
    - Boolean
- A single item can be stored in a variable:
    `name = "Merton Lansley"`


## Data Structures
A data structure is a collection of data items stored in memory plus a number of operations for manipulating that collection

Specifies how the data is organised (at least conceptually) and how it should be accessed


### Static arrays
- The array is probably the most fundamental of data structures
- fixed type and fixed length
- elements accessed via index
- memory location = start + index * width•indispensable in C and C++
- Not standard in Python (although tuples are fixed length; and numpy arrays are declared of fixed length)

### Linked list
- Dynamic, grows and can change size over time
- Does not store pointers or indices to every item
- Stores a link or pointer from each item to the next
- perfect when data is going to be accessed sequentially 
- easy to add/append items•easy to concatenate two lists 
- expensive to access ith item 
   - worst case, follow all n links
   - O(n)
   
### Python Lists
Pythons list is implemented as a underlying C array. To get around the variable length it over-allocates the required memory
for the stored data. This means that if you surpass the allocated size it has to re-write the array with a larger memory allocation

This means fixed cost random access time
    - Ie, time to access ith element is independent of the length of the list n
    - O(1)


### Maps / Dictionaries

- Not all data is sequential
- Conceptually a map or dictionary is  collection of (key -> value) pairs
- A dictionary is implementated under the hood as a hashtable. 
- Because of this, the key has to be hashable, ie, a standard datatype like int, string etc. However, you could use 
an object if it implements `__hash__()` and `__eq__()`

### Hash tables
- Store the element with key _k_ at slot h(k) where h is ahash function which maps k to a number in the range {0,...,n-1}
#### Collisions
If you had two items that are the same, you can create the same hash, creating a collision. So when 2 or more different keys match the same slot.
You can minimise this by using a good hash function

A good hash function satisfies the assumption of simple uniform hashing: each key is equally likely to hash any of the n slots
An example is radix-128 function
ted = t * 128^2 + e * 128 + e = x

Chaining resolves collisions by putting all elements that hash to the same slot in a linked list
    - analogous to putting folders that collide in same slot and searching through them at access time
    
Open addressing successibely probes the hash tables until a match or an empty slot is found
