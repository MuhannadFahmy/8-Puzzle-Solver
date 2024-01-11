# 8-Puzzle-Solver

<p align="center">
  <img src="https://github.com/MuhannadFahmy/8-Puzzle-Solver/assets/20281531/b616a935-c5cd-435f-b6ad-15816f26e829" width="70%">
</p>


The project involves implementing a solution to the 8-puzzle problem using the A* search algorithm. The goal is to create two Java classes, Board and Solver. The Board class models an n-by-n board with sliding tiles, providing methods for various operations like computing Hamming and Manhattan distances, checking if it's the goal board, and generating neighboring boards. The Solver class utilizes the A* algorithm to find the minimum number of moves required to solve the puzzle and provides methods to check solvability, retrieve the solution steps, and display the solution.


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
