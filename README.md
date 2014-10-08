05_Hashing_Lab
==============

Implement a hash table in C++

Requirements
------------

1. `keyExists`, `find`, `remove`, and `size` should all be O(1)
2. `add` should be reasonably fast. Use linear probing to find an open slot in the hash table. This will be O(1), on average, except when `grow` is called.
3. `grow` should be O(n)
4. Do not leak memory


Reading
=======
"Open Data Structures," Chapter 5, except for 5.2.3. http://opendatastructures.org/ods-cpp/5_Hash_Tables.html

Questions
=========

#### 1. Which of the above requirements work, and which do not? For each requirement, write a brief response.

1. works.  although some of them use calcIndex() which must iterate until in finds the entry for given key, that is usually O(1) time
2. works.  grow() is only called when 2 * total elements in array > backingArraySize
3. works.  only has to iterate through each element of the old array size to copy them to the new array
4. works.  the only thing that needs to be done in the destructor and grow is delete[] on the backingArray

#### 2. I decided to use two function (`keyExists` and `find`) to enable lookup of keys. Another option would have been to have `find` return a `T*`, which would be `NULL` if an item with matching key is not found. Which design do you think would be better? Explain your reasoning. You may notice that the designers of C++ made the same decision I did when they designed http://www.cplusplus.com/reference/unordered_map/unordered_map/

Having two seperate functions is better because the act of finding a key that exists and checking if a key exists are two different functionalities, so it is best to seperate them into different functions.  also, returning NULL from find() wouldn't be a good idea because NULL is a possible value for an element in the backingArray, it doesnt tell you whether or not you found the item.

#### 3. What is one question that confused you about this exercise, or one piece of advice you would share with students next semester?

advice would be to make sure you do the reading assigned for the HW, it really helped, and look stuff up online if you want even more information on HashTables.
