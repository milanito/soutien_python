# 🌳 Python Algorithmic Exercises: Binary Trees & Matrices 🌳

## 👨‍🏫 Rules
- ❌ **No Python sugar syntax** (no list comprehensions, lambda functions, etc.)
- ❌ **No returns inside loops** (use variables to store results instead)
- ✅ **Everything runs in one file**
- ✅ **Focus on functions over classes**
- ✅ **Encourage algorithmic thinking**
- ✅ **Visual output to make learning fun**

Each exercise builds on the previous one, ensuring that students **must complete them in order** to progress.

---

## **📝 Exercise 1: Setting Up the Basics**

### **📄 Task**
Create a `TreeNode` class and a function to print a matrix.

### **📝 Instructions**
1. Implement a `TreeNode` class with:
   - `val` (integer value)
   - `left` (left child)
   - `right` (right child)
2. Implement `print_matrix(matrix)`, which prints a given matrix row by row.
3. Print a sample matrix to verify your function.

### **💡 Example**
#### **Input**
```python
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]
print_matrix(matrix)
```
#### **Expected Output**
```
Matrix:
1 2 3
4 5 6
7 8 9
```

### **🏆 Correction**
```python
class TreeNode:
    def __init__(self, val, left, right):
        self.val = val
        self.left = left
        self.right = right 

def print_matrix(matrix):
    print("Matrix:")
    for row in matrix:
        line = ""
        for value in row:
            line += str(value) + " "
        print(line)
```

---

## **🌱 Exercise 2: Building a Binary Tree from a List**

### **📄 Task**
Implement a function to **convert a list into a binary tree** using **level-order insertion**.

### **📝 Instructions**
- Implement `list_to_tree(lst)`, which **builds a binary tree**.
- Follow a **level-order** insertion.
- Use the `TreeNode` class from **Exercise 1**.
- Print the tree using an **in-order traversal** implementing the `print_inorder` function.

### **💡 Example**
#### **Input**
```python
tree = list_to_tree([1, 2, 3, 4, 5, None, 7])
print_inorder(tree)
```
#### **Expected Output**
```
4 2 5 1 3 7
```

### **🏆 Correction**
```python
def list_to_tree(lst):
    if len(lst) == 0:
        return None

    nodes = []
    for val in lst:
        if val is None:
            nodes.append(None)
        else:
            nodes.append(TreeNode(val, None, None))

    for i in range(len(lst)):
        if nodes[i] is not None:
            left_index = 2 * i + 1
            right_index = 2 * i + 2
            if left_index < len(lst):
                nodes[i].left = nodes[left_index]
            if right_index < len(lst):
                nodes[i].right = nodes[right_index]

    return nodes[0]

def print_inorder(root):
    if root:
        print_inorder(root.left)
        print(root.val, end=" ")
        print_inorder(root.right)
```


---

## **🛏 Exercise 3: Finding a Path in a Matrix**

### **📄 Task**
Find **a path that sums to a target value** by moving **right** or **down**.

### **📝 Instructions**
- Start at `(0,0)`.
- Move **right or down** only.
- If the path sums to the target, print `"Found a path!"`, otherwise `"No path found"`.

### **💡 Example**
#### **Input**
```python
matrix = [
    [1, 3, 1],
    [1, 5, 1],
    [4, 2, 1]
]
find_path(matrix, 11)
```
#### **Expected Output**
```
Found a path!
```

### **🏆 Correction**
```python
def find_path(matrix, target):
    def explore(i, j, total):
        if i >= len(matrix) or j >= len(matrix[0]):
            return False
        total += matrix[i][j]
        if i == len(matrix) - 1 and j == len(matrix[0]) - 1:
            if total == target:
                print("Found a path!")
                return True
            return False
        return explore(i + 1, j, total) or explore(i, j + 1, total)

    if not explore(0, 0, 0):
        print("No path found")
```

---

## **🛠 Exercise 4: Counting Leaf Nodes in a Binary Tree**

### **📄 Task**
Implement a function to **count the number of leaf nodes** in a binary tree.

### **📝 Instructions**
- Use the `TreeNode` class from **Exercise 1**.
- Implement `count_leaves(root)`, which **counts all leaf nodes**.

### **💡 Example**
#### **Input**
```python
tree = list_to_tree([1, 2, 3, 4, 5, None, 7])
print(count_leaves(tree))
```
#### **Expected Output**
```
3
```

### **🏆 Correction**
```python
def count_leaves(root):
    if not root:
        return 0
    if not root.left and not root.right:
        return 1
    return count_leaves(root.left) + count_leaves(root.right)
```

---

## **💰 Exercise 5: Finding the Maximum Sum Path in a Binary Tree**

### **📄 Task**
Find the **maximum root-to-leaf path sum** in a binary tree.

### **📝 Instructions**
- Use the `TreeNode` class from **Exercise 1**.
- Implement `max_sum_path(root)`, which finds the **max sum path**.

### **💡 Example**
#### **Input**
```python
tree = list_to_tree([10, 5, 20, 4, 8, 15, 25])
print(max_sum_path(tree))
```
#### **Expected Output**
```
55
```

### **🏆 Correction**
```python
def max_sum_path(root):
    if not root:
        return 0
    return root.val + max(max_sum_path(root.left), max_sum_path(root.right))
```
---

## **⚡ Exercise 6: Brute-Force vs. Optimized Matrix Search**

### **📄 Task**
Compare two methods for **searching for a number in a sorted matrix**.

### **📝 Instructions**
- Implement `search_matrix_brute(matrix, target)`, which searches **all elements**.
- Implement `search_matrix_optimized(matrix, target)`, which starts from the **top-right** and moves **left or down**.

### **💡 Example**
#### **Input**
```python
matrix = [
    [1, 4, 7, 11],
    [2, 5, 8, 12],
    [3, 6, 9, 16],
    [10, 13, 14, 17]
]
search_matrix(matrix, 9)
```
#### **Expected Output**
```
Brute-force: Found 9 in 0.0004 seconds
Optimized: Found 9 in 0.0001 seconds
```

### **🏆 Correction**
```python
import time

def search_matrix_brute(matrix, target):
    start = time.time()
    for row in matrix:
        for value in row:
            if value == target:
                print(f"Brute-force: Found {target} in {time.time() - start:.4f} seconds")
                return
    print("Not found")

def search_matrix_optimized(matrix, target):
    start = time.time()
    i, j = 0, len(matrix[0]) - 1
    while i < len(matrix) and j >= 0:
        if matrix[i][j] == target:
            print(f"Optimized: Found {target} in {time.time() - start:.4f} seconds")
            return
        elif matrix[i][j] > target:
            j -= 1
        else:
            i += 1
    print("Not found")
```

---

## **🌳 Exercise 7: Printing All Paths from Root to Leaf in a Binary Tree**

### **📄 Task**
Print **all root-to-leaf paths** in a binary tree.

### **📝 Instructions**
- Use the `TreeNode` class from **Exercise 1**.
- Implement `print_all_paths(root)`, which **prints every root-to-leaf path**.

### **💡 Example**
#### **Input**
```python
tree = list_to_tree([1, 2, 3, 4, 5, 6, 7])
print_all_paths(tree)
```
#### **Expected Output**
```
1 → 2 → 4
1 → 2 → 5
1 → 3 → 6
1 → 3 → 7
```

### **🏆 Correction**
```python
def print_all_paths(root, path=""):
    if not root:
        return
    new_path = path + str(root.val) + " → "
    if not root.left and not root.right:
        print(new_path[:-3])
    print_all_paths(root.left, new_path)
    print_all_paths(root.right, new_path)
```

---

## **🏆 Exercise 8: Comparing Brute-Force vs. DP in a Matrix**

### **📄 Task**
Solve the **longest increasing path** in a matrix using **brute-force** and **dynamic programming**.

### **📝 Instructions**
- Implement `longest_path_brute(matrix)`, which checks all paths.
- Implement `longest_path_dp(matrix)`, which uses **memoization**.

### **💡 Example**
#### **Input**
```python
matrix = [
    [9, 9, 4],
    [6, 6, 8],
    [2, 1, 1]
]
compare_methods(matrix)
```
#### **Expected Output**
```
Brute-force: 0.4 seconds
Optimized DP: 0.002 seconds
```

### **🏆 Correction**
```python
import time

def longest_path_brute(matrix, i, j, prev_val):
    if i < 0 or j < 0 or i >= len(matrix) or j >= len(matrix[0]) or matrix[i][j] <= prev_val:
        return 0
    return 1 + max(
        longest_path_brute(matrix, i + 1, j, matrix[i][j]),
        longest_path_brute(matrix, i, j + 1, matrix[i][j])
    )

def longest_path_dp(matrix):
    dp = [[-1] * len(matrix[0]) for _ in range(len(matrix))]
    def explore(i, j, prev_val):
        if i < 0 or j < 0 or i >= len(matrix) or j >= len(matrix[0]) or matrix[i][j] <= prev_val:
            return 0
        if dp[i][j] != -1:
            return dp[i][j]
        dp[i][j] = 1 + max(explore(i + 1, j, matrix[i][j]), explore(i, j + 1, matrix[i][j]))
        return dp[i][j]
    return explore(0, 0, -1)
```



