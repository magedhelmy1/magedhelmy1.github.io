---
title: Searching Techniques
author: Maged Helmy
date: 2018-07-01 14:00:00 +0100
categories: [Blogging, Computer Science]
tags: [data_structures]
---

## Hash Table

Hash table is a data structure which stores data in an associative manner. In a hash table, data is stored in an array format, where each data value has its own unique index value. Thus, it becomes a data structure in which insertion and search operations are very fast irrespective of the size of the data. Hash tables are known as dictonaries in python.

Moreover, hashing is a technique that converts a range of key values into a range of indexes of an array. This stores the items in the (key,value) format. This can also be referred to as a hash function. A hash function generates the key/index where the value will be stored.

## Basic operations

Basic operations: the basic operations of a hash table are

-	Search: Searches an element in a hash table
-	Insert: Inserts an element in a hash table
-	Delete: Deletes an element from the hash table


A hash table allows the fast retrieval of data no matter how much data there is. Each index number can be calculated using the value itself. So, the values are placed in an array according to a calculation. For example, the name TIM. The ASCII key is 84, 105 and 109. We can sum up all the values (84 + 105 + 109) = 298. We can divide that by 11 (for example, if that was the length of the array), and the remainder is 1. This can be position of the ASCII key in the array list, at 1. This can be mathematically represented as

```
	Index number= sum (ASCII codes) Mod (size of array)
```
To retrieve an item, we use the value to do a fast retrieval look up using the hash function above.

To revisit, a hashing algorithm or a hash function, is the calculation applied to a key to transform it to an index number which corresponds to a position in the hash table.

To generatlize, for numeric keys, it is common to take the key and divide it by the number of available addresses, n, and take the remainder as the index. For alphanumeric keys, divide the sum of the ASCII codes in a key by the number of available addresses, n, and take the remainder as shown in the example above.

Another method to calculate the hash is the folding method (best for storing phone numbers), where we divide th key into equal parts then adds the part together. There are different types of hash table. Some are more appropriate than other depending on the size of data and length of available memory.

## Collisions

When generating an index for two items yields the same index value, this is called collisions as the index "collides".There are two ways to deal with this, open addressing and closed addresing.

One type of open addressing is linear probing. Linear probing is where you place an item with a colliding index in the next available slot. And when you want to retrieve this data you apply hashing function + linear probing method. In other words, open addressing is placing an item in the next open space.

Disadvantage of Linear Probing is that it might cause clustering of data if the index values are too close. At worse case, it may involve linear search if the data is the same size as the has table.

Other examples of open addressing are:
-	Plus 3 rehash: To deal with clustering issue of linear probing, instead of adding in the next available space, add in the 3rd available place.
-	Quadratic probing: square the number of failed attempts. The distance from the collision rapidly grows rapidly
-	Double hashing: applies a second hash function. The result of the second hashing is the distance to try next from the distance of collision

Another way, is to make the table storing the data bigger than needed. For example, to make only 70% of the hash table to be only occupied. This is called the load factor, where the total data occupied is less than the actual size of the array. A dynamic sizing can be applied, where if the database reaches the value of the loading factor the database will increase. If the load factor is low, then hashing with linear probing should work well.

Another way to deal with collision is to use chaining which is known as closed addressing. This is adding items on the colliding indexes by using a linked list. We can then search the item by traversing the linked list. The look up is better in comparison to the linear probing. If the load factor is slow, open addressing is better.

The best hash function should:

-	Minimize Collisions
-	Uniform distribution of hash values
-	The hash function should be easy to calculate
-	Resolve any collisions

## To summarize

-	The address of each key is calculated using the key itself
-	Collison’s resolved with open or closed addressing
-	Hashing is widely used in database indexing, compilers, cashing etc.
-	The insertion, deletion and retrieve occur in constant time in the best case scenario. Not when there is a collision.
