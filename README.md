# 8 Puzzle Solver

<p align="center">
  <img src="https://github.com/MuhannadFahmy/8-Puzzle-Solver/assets/20281531/b616a935-c5cd-435f-b6ad-15816f26e829" width="70%">
</p>


The project involves implementing a solution to the 8-puzzle problem using the A* search algorithm. The goal is to create two Java classes, Board and Solver. The Board class models an n-by-n board with sliding tiles, providing methods for various operations like computing Hamming and Manhattan distances, checking if it's the goal board, and generating neighboring boards. The Solver class utilizes the A* algorithm to find the minimum number of moves required to solve the puzzle and provides methods to check solvability, retrieve the solution steps, and display the solution.

We make a key observation: To solve the puzzle from
a given search node on the priority queue, the total number of moves we
need to make (including those already made) is at least its priority,
using either the Hamming or Manhattan priority function.
(For Hamming priority, this is true because each block that is out of place
must move at least once to reach its goal position.
For Manhattan priority, this is true because each block must move
its Manhattan distance from its goal position.
Note that we do not count the blank square when computing the
Hamming or Manhattan priorities.)
Consequently, when the goal board is dequeued, we
have discovered not only a sequence of moves from the
initial board to the goal board but one that makes the fewest number of moves. 
(Challenge for the mathematically inclined: prove this fact.)

<p><b>A critical optimization.</b></p>
Best-first search has one annoying feature:
Search nodes corresponding to the same board
are enqueued on the priority queue many times.
To reduce unnecessary exploration of useless search nodes,
when considering the neighbors of a search node, don't enqueue
a neighbor if its board is the same as the board of the
predecessor search node.

<pre><blockquote>
  8  1  3       8  1  3       8  1          8  1  3       8  1  3
  4     2       4  2          4  2  3       4     2       4  2  5
  7  6  5       7  6  5       7  6  5       7  6  5       7  6

predecessor   search node    neighbor       neighbor      neighbor
                                           (disallow)
</pre></blockquote>

<p><b>A second optimization.</b> </p>
To avoid recomputing the Manhattan priority of a search node from scratch each time during
various priority queue operations, pre-compute its value when you construct the search node;
save it in an instance variable, and return the saved value as needed.
This caching technique is broadly applicable: consider using it in any situation where you
are recomputing the same quantity many times and for which computing that quantity is a bottleneck 
operation.


# API Summary:

### Board Class:
* Constructor: Takes an n-by-n array of tiles.
* Methods:
  * toString(): Returns a string representation of the board.
  * dimension(): Returns the board dimension.
  * hamming(): Computes the Hamming distance.
  * manhattan(): Computes the Manhattan distance.
  * isGoal(): Checks if the board is the goal board.
  * equals(Object y): Compares two boards for equality.
  * neighbors(): Returns neighboring boards.
  * twin(): Returns a board obtained by exchanging any pair of tiles.
  
### Solver Class:

* Constructor: Takes an initial board and applies the A* algorithm.
* Methods:
  * isSolvable(): Checks if the initial board is solvable.
  * moves(): Returns the minimum number of moves to solve the puzzle.
  * solution(): Returns the sequence of boards in the shortest solution.
