# Solve the Nonogram with CUDA C
## 0. Introduce

This is my project when I take the course of Parallel Programming. I wanted to solve puzzle which name is a Nonogram using CUDA C.  There's a lot of code for solving this puzzle but it is hard to find the version of CUDA. That's what I wanted to start the project with this subject.

### 0.1 What is the Nonogram
Nonogram is the puzzle game which is developed in Japan and it has other names such as griddlers, picross, and logic puzzle. Generally, there is a given grid with arbitrary size and several numbers that are located on the left side and upper side of the grid. The numbers indicate the hint of each row and column, which implies the number of cells to be colored. The aim of this puzzle is that making pictures according to the hints of each row and column. (See Fig. 1.)  Here is the rule for the puzzle.  
- __Rule 1__: Color the cells consecutively according to the hints.  
- __Rule 2__: At least make one blank between the hints.
- __Rule 3__: The order of the hints is identical with the order of the colored cells.
