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
4 2 5 1 7 3
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
    [1, 4, 7, 10],
    [2, 5, 8, 11],
    [3, 6, 9, 12],
]
search_matrix(matrix, 9)
```
#### **Expected Output**
```
Brute-force: Found 9 in 0.0004 seconds
Optimized: Found 9 in 0.0001 seconds
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

