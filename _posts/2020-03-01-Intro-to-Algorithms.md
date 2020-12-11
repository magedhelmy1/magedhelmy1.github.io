---
title: What are Algorithms?
date: 2020-03-01 14:00:00 +0100
categories: [Blogging, Computer Science]
tags: [algorithms]
---
## Algorithms

When starting with any problem to solve. Clearly have the input stated and the output stated. Also, right down any edge cases as part of the input. The algorithm bridges the input with the output. The algorithm is a step-by-step procedure which defines the instructions to be executed in an order to get a desired output.

## Greedy Algorithms

Greedy Algorithms: It solves the problem by making a local optimal choice at each stage with the hope of finding a global optimum. However, generally greedy algorithms do not provide globally optimized solutions.

Greedy algorithms are quick. A lot faster than the two other alternatives (Divide & Conquer, and Dynamic Programming). They're used because they're fast.

Examples
Most networking algorithms use the greedy approach. Here is a list of few of them −

- Travelling Salesman Problem
- Prim's Minimal Spanning Tree Algorithm
- Kruskal's Minimal Spanning Tree Algorithm
- Dijkstra's Minimal Spanning Tree Algorithm
- Graph - Map Coloring
- Graph - Vertex Cover
- Knapsack Problem
- Job Scheduling Problem

## Divide and Conquer Algorithms

Divide and Conquer Algorithms: The problem is divided into smaller sub-problems and then each problem is solved independently. When we keep on dividing, it will reach into a stage where it cannot be divided anymore. It is recursive by nature. When you break the problem, it essentially remains the same. The solution of all sub-problems is merged in order to obtain the solution of an original problem. Examples include merge sort, quick sort, binary search, closest pair.

The following computer algorithms are based on divide-and-conquer programming approach −

- Merge Sort
- Quick Sort
- Binary Search
- Strassen's Matrix Multiplication
- Closest pair (points)

## Dynamic Algorithms

Dynamic Programming: Similar to divide and conquer in breaking down the problem into smaller problems. But unlike divide and conquer, these sub-problems are not solved independently, but rather it looks at the results of the previously solved sub-problems. The solutions of sub-problems are combined in order to achieve the best solution. It makes it efficient by storing intermediate results. It uses memoization. This can be thought of us caching which is a way to store values so we can use them later on.

A good example is Fibonacci where it has several recursion calls. The idea of dynamic programming is to reduce function calls of same methods. By storing the result of the function, we do not call it again. Using dynamic programming on Fibonacci, greedy algorithm is O(2^n) while dynamic programming is O(n). This technique of storing the results of already solved subproblems is called Memoization.

There are two methods:

1)	Top-down with Memoization: This approach tries to solve the bigger problem by recursively finding the solution to smaller sub-problems. Whenever we solve a sub-problem, we cache its results so that we don’t end up solving it repeatedly if it is called multiple times later. Instead, we return the saved results. This technique of storing the results of already solved subproblems is called Memoization.

2)	Bottom-up with Tabulation: This method avoids recursion, and works by solving an n-dimensional table. Since we know Fibonacci number is the sum of the two preceding numbers, we can use fact to populate table.

## Comparison
In contrast to greedy algorithms, where local optimization is addressed, dynamic algorithms are motivated for an overall optimization of the problem.

In contrast to divide and conquer algorithms, where solutions are combined to achieve an overall solution, dynamic algorithms use the output of a smaller sub-problem and then try to optimize a bigger sub-problem. Dynamic algorithms use Memoization to remember the output of already solved sub-problems. However, when a lot of recursive calls are required, memoization may cause memory problems because it might have stacked the recursive calls to find the solution of the deeper recursive call but we won't deal with this problem in tabulation.

Generally, memoization is also slower than tabulation because of the large recursive calls.

The following computer problems can be solved using dynamic programming approach −

- Fibonacci number series
- Knapsack problem
- Tower of Hanoi
- All pair shortest path by Floyd-Warshall
- Shortest path by Dijkstra
- Project scheduling
