

# Sudoku JS

Sudoku is generated computationally through backtracking, I decided to code it up for fun. I also took advantage of doing this project to improve my bare knowledge of Javascript, HTML, and CSS. 


## Overview of the Code
### Solver Algorithm
1. Recursively iterate through each cell in the 9x9 grid.
2. At each cell, find all the possible values by checking that a value isn't already in the row, the column, and/or the 3x3 subgrid. 
3. Set the value of the cell to a selected possible value.
4. Recursive call iterating to the next cell until all cells are filled.
5. If a cell has no candidate value, backtrack and select a new possible value.



### Generator Algorithm
1. Observe that all 3x3 subgrids along a diagonal are independent of each other. Randomly generate 1 to 9 and fill in each of those subgrids.
    * Ex:
    
    4 6 3 _ _ _ _ _ _
    
    7 8 1 _ _ _ _ _ _
    
    5 9 2 _ _ _ _ _ _
    
    _ _ _ 7 4 1 _ _ _
    
    _ _ _ 9 5 3 _ _ _
    
    _ _ _ 6 8 2 _ _ _
    
    _ _ _ _ _ _ 3 8 6 
    
    _ _ _ _ _ _ 1 5 9 
    
    _ _ _ _ _ _ 7 2 4 
2. Fill the grid by running the Solver with a slight modification to randomly shuffle the list of possible values for each cell. 


## To-Do
#### Puzzle Algorithm
* Right now, the puzzle is taking a while to generate on some iterations. An optimization to make in the Solver is when getting valid candidates, start with the analysis of the previous step and modify it by removing values along the row, column, and box of the last-modified cell. This will bring down the time complexity from O(N<sup>3</sup>) to O(N).
* Review my difficulty estimation algorithm. Something is wrong with the code. Difficulty 0 for some generations.
* Use the better difficulty estimation algorithm in the article I referenced.
* Use the difficulty score to generate Easy, Medium, Hard puzzles. Currently, I just continue removing clues until there are 16 left or all the list of shuffle cells to go through is exhausted.
#### Front-End
* Make the puzzle grid scalable with the window.
* Allow users to make notes inside of each cell, similar to how the New York Times Sudoku does.
* Timer
* Help section where  a user can get hints, check cells, reveals cells, check the puzzle, and reveal the solution.
* Functional Easy, Medium, Hard buttons.
