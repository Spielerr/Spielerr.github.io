---
layout: page
title: Generic Programming in C
description: implementation of generic programming features in C using pre-processor directives
img: assets/img/generic.jpg
importance: 5
category: work
---

[[Project Report]]({{ '/assets/pdf/Design_Patterns_Project_Report.pdf' | relative_url }})
[[Project Readme]]({{ '/assets/pdf/Design_Patterns_Project_Readme.pdf' | relative_url }})
[[Code]](https://github.com/Spielerr/Generic-Programming-in-C)

### Summary
A project aimed at implementing Generic Programming features as a design pattern in C, using pre-processor directives. This project involved the implementation of generic containers like list, stack, queue, vector, and hashmap, iterators for each of these containers, and generic algorithms like find, find_if, count, count_if, min, max, and accumulate that make use of these iterators. This project was developed and implemented as part of the Design Patterns Course during my Undergraduate Study.

### Implementation Details
The generic containers, iterators, and generic algorithms have been implemented as a header file that the user can include as a library in their client program. These features have been implemented through the extensive use of pre-processor directives as explained below:

* **Generic Containers**: The user can create an interface for a particular container and data type combination, for example, LIST(double_l, double). In the background, the defined interface maps to the #define directives and results in the generation of the structures and functions required to define a list of double type and all its supported operations. Thus, double_l now represents a list of double type. This is essentially a new type that the user can use to declare corresponding variables, like double_l l1. Consequently, this variable can be used to invoke the operations of a list, like l1.insert_at_beg(&l1, 5).
* **Iterators**: The definition of an interface for a container and type also results in the creation of the iterator for that container and type combination. In the above example, double_l_iterator represents an iterator to a list of double type. This can be used to declare variables representing iterators like double_l_iterator it1 and can be used to invoke the operations supported for that iterator like it1.get_value(&it1). Every container includes the implementation of a specific type of iterator and its operations as mandated by the expected behavior of that container. For example, the list iterator is implemented as a forward iterator supporting the equality, inequality, get_value, set_current, next, has_next, and advance operations.
* **Generic Algorithms**: Adhering to the C++ concept of decoupling the containers and algorithms using iterators, the algorithms are implemented such that they are independent of the containers. The algorithms exclusively use iterators (a pair of iterators representing the operating range for the container under consideration) for implementing the required functionalities. Thereby, these algorithms are generic and can be invoked for any of the containers as long as the container supports an iterator of a specific type as mandated by the algorithm. For example, the find algorithm requires an input iterator, at the very least, for its functionality. Thereby, a list iterator, which is implemented as a forward iterator, can be used to invoke the find algorithm because a forward iterator is more powerful than an input iterator and supports all the functionalities expected of an input iterator.

### Generic Containers
#### List

The List container has been implemented as a doubly linked list that supports various operations expected for a list, such as insertion of an element at the beginning and at the end of the list, deletion from the beginning and from the end of the list, deletion of a particular key from the list, display of the contents of the list, and initializing the begin and end iterators for the list. The list iterator has been implemented as a forward iterator supporting the following operations - equality, inequality, get_value, set_current, next, has_next, and advance.

#### Stack

The Stack container has been implemented as a doubly linked list that supports various operations expected for a stack, such as push, pop, peek, display, and initializing the begin and end iterators for the stack. The stack iterator has been implemented as a forward iterator supporting the following operations - equality, inequality, get_value, set_current, next, has_next, and advance.

#### Queue

The Queue container has been implemented as a doubly linked list that supports various operations expected for a queue, such as enqueue, dequeue, peek, display, and initializing the begin and end iterators for the queue. The queue iterator has been implemented as a forward iterator supporting the following operations - equality, inequality, get_value, set_current, next, has_next, and advance.

#### Vector

The Vector container has been implemented using a dynamic table that supports various operations expected for a vector, such as push_back, pop_back, random access of an element based on an index, freeing of the dynamic table associated with the vector, display, and initializing the begin and end iterators for the vector. The vector iterator has been implemented as a forward iterator supporting the following operations - equality, inequality, get_value, set_current, next, has_next, and advance.

#### Hashmap

The Hashmap container has been implemented using an array of structures, hashing, and separate chaining to handle collisions during hashing. It supports various operations expected for a hashmap, such as insertion of a key-value pair into the map, deletion of a key-value pair from the map, retrieving the value associated with a key, display of the contents of the map, and initializing the begin and end iterators for the hashmap. The hashmap iterator has been implemented as a forward iterator supporting the following operations - equality, inequality, get_value, set_current, next, has_next, and advance.

### Generic Algorithms
#### Find

The Find algorithm takes in a pair of iterators (first and last) and the key to be found. The functionality of the find algorithm mandates that these iterators are of type Input Iterator and above. The find function moves the first iterator until it points to the required key. If the required key is not found in the mentioned range, the first iterator will be pointing to the last iterator, thereby indicating that the key has not been found.

#### Find_if

The Find_if algorithm takes in a pair of iterators (first and last) and a predicate (a function pointer). The functionality of the find_if algorithm mandates that these iterators are of type Input Iterator and above. The find_if function moves the first iterator until it points to the key that satisfies the predicate. If a key satisfying the predicate is not found in the mentioned range, the first iterator will be pointing to the last iterator, thereby indicating that a key satisfying the predicate has not been found.

#### Count

The Count algorithm takes in a pair of iterators (first and last), the key whose count is to be found, and the variable that will store the count. The functionality of the count algorithm mandates that these iterators are of type Input Iterator and above. The count function traverses the container until the first iterator points to the last iterator and counts the number of times the given key occurs in this range.

#### Count_if

The Count_if algorithm takes in a pair of iterators (first and last), the predicate (function pointer), and the variable that will store the count. The functionality of the count_if algorithm mandates that these iterators are of type Input Iterator and above. The count function traverses the container until the first iterator points to the last iterator and counts the number of times a key satisfying the predicate occurs in this range.

#### Min

The Min algorithm takes in a pair of iterators (first and last), a variable (min) that will hold the minimum value, and a flag variable denoting if the min variable has been set to a valid value. The functionality of the min algorithm mandates that these iterators are of type Input Iterator and above. The min function traverses the container until the first iterator points to the last iterator and finds the minimum key that occurs in this range. If the first and last iterator point to the same node, it means that the range of the container to be traversed is empty, then the flag variable is set to 0 indicating that the value of the min variable is garbage and does not hold the actual min value. Otherwise, the min variable is set to the appropriate value, and the flag is set to 1.

#### Max

The Max algorithm takes in a pair of iterators (first and last), a variable (max) that will hold the maximum value, and a flag variable denoting if the max variable has been set to a valid value. The functionality of the max algorithm mandates that these iterators are of type Input Iterator and above. The max function traverses the container until the first iterator points to the last iterator and finds the maximum key that occurs in this range. If the first and last iterator point to the same node, it means that the range of the container to be traversed is empty, then the flag variable is set to 0, indicating that the value of the max variable is garbage and does not hold the actual max value. Otherwise, the max variable is set to the appropriate value, and the flag is set to 1.

#### Accumulate

The Accumulate algorithm takes in a pair of iterators (first and last) and a variable (acc) that holds the accumulated value. The functionality of the accumulate algorithm mandates that these iterators are of type Input Iterator and above. The accumulate function traverses the container until the first iterator points to the last iterator, accumulating the keys that are found in this range. The accumulated value is stored in the acc variable.