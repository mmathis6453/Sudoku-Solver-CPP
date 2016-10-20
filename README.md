# Sudoku-Solver-CPP
This is a C++ program that very efficiently solves sudoku puzzles. 

It uses only the standard C++ library, and can be compiled with g++ or whatever other C++ compiler you'd prefer.

It works by iteratively trying each available move, resolving the avalable moves at each iteration, and backtracking when it gets stuck. 

The program is run via the command line, and takes in a file as the first and only argument that defines the sudoku puzzle to be solved. 
The format of the file is a simple .txt document with 9 lines that are 9 characters in length with no whitespace. Zeros in places where the number on the initial sudoku puzzle is undefined.

Examples of these files are included in the repository. 

game.txt is considered one of the hardest puzzles to solve, and the algorithm solves it in ~5 seconds.

game2.txt is considered a very easy puzzle to solve, and the algorithm solves it near instantaneously. 

I am yet to find a puzzle the algorithm can't solve within a few seconds.


Here is a little more detail of how the algorithm works:
For simplicity, let's assume that no moves have been resolved (this would never actually happen as we always start with a given game)
In this scenario, we have 9 possible moves to make:

  9 9 9 9 9 9 9 9 9  
  9 9 9 9 9 9 9 9 9  
  9 9 9 9 9 9 9 9 9  
  9 9 9 9 9 9 9 9 9  
  9 9 9 9 9 9 9 9 9  
  9 9 9 9 9 9 9 9 9  
  9 9 9 9 9 9 9 9 9  
  9 9 9 9 9 9 9 9 9  
  9 9 9 9 9 9 9 9 9  

Now let's say that the algorithm wants to put a 2 at x = 2, y = 2
The 2D array of moves would now look like this:

  **8 8 8** 9 9 9 9 9 9  
  **8 8 8** 9 9 9 9 9 9   
  **8 8 1 8 8 8 8 8 8**  
  9 9 **8** 9 9 9 9 9 9  
  9 9 **8** 9 9 9 9 9 9  
  9 9 **8** 9 9 9 9 9 9  
  9 9 **8** 9 9 9 9 9 9  
  9 9 **8** 9 9 9 9 9 9  
  9 9 **8** 9 9 9 9 9 9  
  
  
As this continues, if the number of moves for any cell reaches 0, we backtrack 
