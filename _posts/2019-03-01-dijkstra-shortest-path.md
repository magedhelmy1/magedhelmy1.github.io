---
title: Dijkstra Shortest Path
author: Maged Helmy
date: 2019-03-01 14:00:00 +0100
categories: [Blogging, Computer Science]
tags: [algorithms]
---

Shortest path by Dijkstra: The goal is to find the shortest path between two vertices. The objective is to find the shortest path from the starting vertices to any vertices. An example of greedy algorithms since we select the shortest distance every time. It makes local optimum decisions in the hope to make a good global optimum.
Vertex – Shortest Distance from A – Previous Vertex
A – 0
B – 3 - D
C – 7 - E
D – 1 - A
E – 2 – D
Dijkstra Path: We use two lists, one to keep track of the vertices we visited and one to keep track of the vertices we did not visit.


Example:
A – B-\-
| -/- |    C
D – E-/-
Have a table ready with
Vertex – Shortest Distance from A – Previous Vertex:
And a list of Visited=[] and unvisited=[]
How does this algorithm work?
	For the starting position, A, fill zero for vertex A and blank for previous vertex since they are empty and it’s the initial vertex.
	For the current vertex (A), examine its unvisited neighbors. In our case B and D
	We are currently visiting A and its unvisited neighbors are B and D. Update the list by adding A to the list of visited.
	For the current vertex, calculate the distance of each neighbor from the start vertex to D and to B. Update the table with the shortest distance. In our case add 6 to B, and 1 to D. Also fill out the previous index to A for both.
	Move to D, since it’s the shortest path and update the visited list. Examine its neighbors, in our case B and E.
	Calculate the shorted distance from A via D to its neighbors and update the list if it is less than the existing. In our case B will update to 3 and E will update to 2.
	Always Visit the unvisited vertex with the smallest cost. And update the table if the distance is shorter.
	Update the table and Visited and unvisited as you go along.
	And so on….
In other words:
1)	Let distance of start vertex from the start vertex = 0
2)	Let distance of all other vertices from start to infinity
3)	WHILE vertices remain unvisited
i.	Visit unvisited vertex with smallest known distance from start vertex, call this the current vertex
ii.	For each unvisited neighbor of the current vertex
iii.	If the calculated distance of this vertex is less than the known distance
1.	Update the shortest distance to this vertex
2.	Update the previous vertex with the current vertex
iv.	End if
b.	Next unvisited neighbor
c.	Add the current vertex to the list of visited vertices.
4)	End while

- update photo !

----------------------
Shortest path by Dijkstra: The goal is to find the shortest path between two vertices. The objective is to find the shortest path from the starting vertices to any vertices. An example of greedy algorithms since we select the shortest distance every time. It makes local optimum decisions in the hope to make a good global optimum.
Vertex – Shortest Distance from A – Previous Vertex
A – 0
B – 3 - D
C – 7 - E
D – 1 - A
E – 2 – D

Dijkstra Path: We use two lists, one to keep track of the vertices we visited and one to keep track of the vertices we did not visit.


Example:
A – B-\-
| -/- |    C
D – E-/-
Have a table ready with
Vertex – Shortest Distance from A – Previous Vertex:
And a list of Visited=[] and unvisited=[]
How does this algorithm work?
	For the starting position, A, fill zero for vertex A and blank for previous vertex since they are empty and it’s the initial vertex.
	For the current vertex (A), examine its unvisited neighbors. In our case B and D
	We are currently visiting A and its unvisited neighbors are B and D. Update the list by adding A to the list of visited.
	For the current vertex, calculate the distance of each neighbor from the start vertex to D and to B. Update the table with the shortest distance. In our case add 6 to B, and 1 to D. Also fill out the previous index to A for both.
	Move to D, since it’s the shortest path and update the visited list. Examine its neighbors, in our case B and E.
	Calculate the shorted distance from A via D to its neighbors and update the list if it is less than the existing. In our case B will update to 3 and E will update to 2.
	Always Visit the unvisited vertex with the smallest cost. And update the table if the distance is shorter.
	Update the table and Visited and unvisited as you go along.
	And so on….
In other words:
1)	Let distance of start vertex from the start vertex = 0
2)	Let distance of all other vertices from start to infinity
3)	WHILE vertices remain unvisited
i.	Visit unvisited vertex with smallest known distance from start vertex, call this the current vertex
ii.	For each unvisited neighbor of the current vertex
iii.	If the calculated distance of this vertex is less than the known distance
1.	Update the shortest distance to this vertex
2.	Update the previous vertex with the current vertex
iv.	End if
b.	Next unvisited neighbor
c.	Add the
-----
