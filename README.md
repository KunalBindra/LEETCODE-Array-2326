# LEETCODE-Array-2326
Let's walk through a dry run of your `spiralMatrix` solution, step by step:

### Initial Setup:
- **Input variables**:
  - `m`: Number of rows in the matrix.
  - `n`: Number of columns in the matrix.
  - `head`: The head node of a linked list containing values to be placed into the matrix.
- **Matrix `ans`**:
  - An `m x n` matrix is initialized with all elements set to `-1`.
- **Directions** (`dirs` array):  
  This will control the direction in which the algorithm traverses the matrix.
  - `dirs[0] = {0, 1}`: move right.
  - `dirs[1] = {1, 0}`: move down.
  - `dirs[2] = {0, -1}`: move left.
  - `dirs[3] = {-1, 0}`: move up.
- **Initial coordinates**: 
  - `x = 0`, `y = 0`: starting at the top-left corner of the matrix.
  - `d = 0`: starting by moving right (initial direction).

### Loop:
The algorithm fills the matrix in a spiral pattern until the linked list is exhausted. For each element:
1. Set the matrix position `ans[x][y]` to the value of the current node `curr.val`.
2. Check if the next position based on the current direction is either out of bounds or already filled (value is not `-1`).
3. If it is, change the direction by updating `d = (d + 1) % 4` (move in a clockwise manner).
4. Move to the next position by updating `x` and `y` based on the current direction.

### Example Dry Run:
Consider a 3x3 matrix (`m = 3`, `n = 3`), and a linked list: `1 -> 2 -> 3 -> 4 -> 5 -> 6 -> 7 -> 8 -> 9`.

1. Initialize the matrix `ans`:
   ```
   ans = [[-1, -1, -1],
          [-1, -1, -1],
          [-1, -1, -1]]
   ```

2. Traverse the linked list, and fill the matrix in a spiral:

   - Start at `x = 0, y = 0, d = 0` (moving right):
     - `ans[0][0] = 1`: Move right.
     ```
     ans = [[1, -1, -1],
            [-1, -1, -1],
            [-1, -1, -1]]
     ```

   - `ans[0][1] = 2`: Move right.
     ```
     ans = [[1, 2, -1],
            [-1, -1, -1],
            [-1, -1, -1]]
     ```

   - `ans[0][2] = 3`: Move down.
     ```
     ans = [[1, 2, 3],
            [-1, -1, -1],
            [-1, -1, -1]]
     ```

   - `ans[1][2] = 4`: Move down.
     ```
     ans = [[1, 2, 3],
            [-1, -1, 4],
            [-1, -1, -1]]
     ```

   - `ans[2][2] = 5`: Move left.
     ```
     ans = [[1, 2, 3],
            [-1, -1, 4],
            [-1, -1, 5]]
     ```

   - `ans[2][1] = 6`: Move left.
     ```
     ans = [[1, 2, 3],
            [-1, -1, 4],
            [-1, 6, 5]]
     ```

   - `ans[2][0] = 7`: Move up.
     ```
     ans = [[1, 2, 3],
            [-1, -1, 4],
            [7, 6, 5]]
     ```

   - `ans[1][0] = 8`: Move right.
     ```
     ans = [[1, 2, 3],
            [8, -1, 4],
            [7, 6, 5]]
     ```

   - `ans[1][1] = 9`: Finished filling the matrix.
     ```
     ans = [[1, 2, 3],
            [8, 9, 4],
            [7, 6, 5]]
     ```

### Final Matrix Output:
```
[[1, 2, 3],
 [8, 9, 4],
 [7, 6, 5]]
```

### Summary:
The algorithm successfully fills the matrix in a spiral order, and the linked list elements are placed accordingly until no more nodes are left.
