# Solve the Nonogram with CUDA C
## 0. Introduce

This is my project when I take the course of Parallel Programming. I wanted to solve puzzle which name is a Nonogram using CUDA C.  There's a lot of code for solving this puzzle but it is hard to find the version of CUDA. That's what I wanted to start the project with this subject.

### 0.1 What is the Nonogram
Nonogram is the puzzle game which is developed in Japan and it has other names such as griddlers, picross, and logic puzzle. Generally, there is a given grid with arbitrary size and several numbers that are located on the left side and upper side of the grid. The numbers indicate the hint of each row and column, which implies the number of cells to be colored. The aim of this puzzle is that making pictures according to the hints of each row and column. (See Fig. 1.)  Here is the rule for the puzzle.  
- __Rule 1__: Color the cells consecutively according to the hints.  
- __Rule 2__: At least make one blank between the hints.
- __Rule 3__: The order of the hints is identical with the order of the colored cells.

__0.1.1 Input__  
The first line of the input gives two integers, let N and M. N is the size of rows and M is the size of columns. The next N lines of input which consist of an arbitrary number of integers inform how many cells will be colored from the 1st row to Nth row. The next M lines of input inform how many cells will be colored from 1st column to Mth column.

__0.1.2 Output__  
The output will show the hidden picture. For convinience, I would use white and black box, which correspond to blank and hint. 


### 0.2 How to Solve it?  
There is a lot of effort to solve the Nonogram with computer programming with lots of techniques, and most of them seek for efficient method only using CPU. For example, one can conduct solving nonograms with the backtracking method which determines the possibility of the next row based on the current row case. Because the backtracking method does not scan every case for the puzzle, it can reduce searching time. However, this method works serial way, it is hard to apply in a parallel way. For solving the nonogram with the parallel method, I use straightforward but possible to do a parallel way, which is using the basic technique for solving a puzzle. Therefore, I tried to use straight-forward but easily parallable strategy.  It is basic technique for solving puzzle. Let’s see the steps.  
- __Step 1__: Find every possible case for each row and column.  
- __Step 2__: Compare every case and find common cell.  
- __Step 3__: Reduce case according to the common cell from Step 2.  
- __Step 4__: Repeat Step 2 and 3 until puzzle is solved.  
For example, one can find every possible case for the row of width 5 and with hints 1 and 2. (See Fig. 3. a.) Since there are only three possible cases and one can find only 4th cell is colored in every case so it can be determined that the 4th cell of this row will be colored. After that, using a determined cell from row hints, it is possible to reduce the possibility and determine whether some cells will be colored or not. Assume the hint of the 4th column is 3. (See Fig. 3. b.) It is easy to figure out that there are 2 possible cases, one is that to color from the first cell to the third cell and the other is that to color from the second cell to the last cell. Since the first cell of the column is colored by the previous step, the only possible way is to color this column from the first cell. The only thing we have to solve this puzzle is that repeat these methods until the puzzle is solved. It has a limitation that considers every possible case for rows and columns so it would take more time than the backtracking method when conducting serial ways. However, it can make a parallel way for the most part of the method and because consider every case, I expect that it will make an accurate result with reducing much time.
