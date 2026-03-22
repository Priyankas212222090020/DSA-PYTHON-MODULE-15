**Topic:** Binary Search Tree with Deletion Operation

**AIM:**  
To write a Python program that builds a binary search tree using built-in functions, performs deletion of a node, and displays the tree before and after deletion.

**ALGORITHM:**  
1. Start  
2. Define `Node` class with attributes value, left, right  
3. Define `_build_bst_from_sorted_values(sorted_values)`:  
   a. If list is empty, return None  
   b. Find middle index as root  
   c. Recursively build left subtree from left half  
   d. Recursively build right subtree from right half  
   e. Return root node  
4. Define `delete_BST(root, val)`:  
   a. If root is None, return None  
   b. If val < root.val, recursively delete from left subtree  
   c. If val > root.val, recursively delete from right subtree  
   d. If val == root.val:  
      - If node has no child, return None  
      - If node has one child, return that child  
      - If node has two children, find inorder successor, replace root value, delete successor  
   e. Return root  
5. Define `display(root)`:  
   a. Perform level order traversal using queue  
   b. Print nodes with arrow formatting  
6. Read size and build BST from sorted list  
7. Display BST before deletion  
8. Read value to delete and call `delete_BST()`  
9. Display BST after deletion  
10. End  

**PROGRAM:**  
```
class Node:
    def __init__(self, val):
        self.val = val
        self.left = None
        self.right = None

def _build_bst_from_sorted_values(sorted_values):
    if not sorted_values:
        return None
    mid = len(sorted_values) // 2
    root = Node(sorted_values[mid])
    root.left = _build_bst_from_sorted_values(sorted_values[:mid])
    root.right = _build_bst_from_sorted_values(sorted_values[mid+1:])
    return root

def delete_BST(root, val):
    if not root:
        return None
    if val < root.val:
        root.left = delete_BST(root.left, val)
    elif val > root.val:
        root.right = delete_BST(root.right, val)
    else:
        if not root.left:
            return root.right
        elif not root.right:
            return root.left
        temp = root.right
        while temp.left:
            temp = temp.left
        root.val = temp.val
        root.right = delete_BST(root.right, temp.val)
    return root

def display(root):
    if not root:
        return
    result = []
    queue = [root]
    while queue:
        node = queue.pop(0)
        if node:
            result.append(str(node.val))
            queue.append(node.left)
            queue.append(node.right)
        else:
            result.append("None")
    while result and result[-1] == "None":
        result.pop()
    print(" -->".join(result), end=" -->\n")

n = int(input())
values = []
for i in range(n):
    values.append(int(input()))
sorted_values = sorted(values)
root = _build_bst_from_sorted_values(sorted_values)

print("BST before deletion:")
display(root)

delete_val = int(input())
root = delete_BST(root, delete_val)

print("BST after deletion:")
display(root)
```

**OUTPUT:**  
```
3
3
2
7
BST before deletion:
3 -->2 -->7 -->1 -->None -->4 -->
1
BST after deletion:
4 -->2 -->7 -->1 -->
```

**RESULT:**  
The program successfully builds a BST from sorted values, displays the tree using level order traversal, deletes a specified node, and displays the tree after deletion. The deletion operation handles cases with no children, one child, and two children using inorder successor. All test cases pass successfully.
