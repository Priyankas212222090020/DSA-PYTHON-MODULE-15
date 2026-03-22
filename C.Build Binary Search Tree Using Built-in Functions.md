**Topic:** Build Binary Search Tree Using Built-in Functions

**AIM:**  
To write a Python program that builds a binary search tree using recursion from sorted values, prints the postorder traversal, displays the right subtree, and verifies whether the tree is a valid BST.

**ALGORITHM:**  
1. Start  
2. Define `Node` class with attributes value, left, right  
3. Define `_build_bst_from_sorted_values(sorted_values)`:  
   a. If list is empty, return None  
   b. Find middle index as root  
   c. Recursively build left subtree from left half  
   d. Recursively build right subtree from right half  
   e. Return root node  
4. Define `right_subtree(root)`:  
   a. Traverse and display right subtree nodes in preorder  
   b. Print with arrow formatting  
5. Define `postorder(root)`:  
   a. Recursively traverse left, right, then root  
   b. Collect nodes in list  
6. Define `is_bst(root, min_val, max_val)`:  
   a. If root is None, return True  
   b. Check if root value is within range  
   c. Recursively check left and right subtrees  
7. Read size and list values from user  
8. Sort the list and build BST  
9. Print postorder traversal  
10. Print right subtree  
11. Check and print if tree is BST  

**PROGRAM:**  
```
class Node:
    def __init__(self, val):
        self.val = val
        self.left = None
        self.right = None
    
    def __repr__(self):
        return f"Node({self.val})"

def _build_bst_from_sorted_values(sorted_values):
    if not sorted_values:
        return None
    mid = len(sorted_values) // 2
    root = Node(sorted_values[mid])
    root.left = _build_bst_from_sorted_values(sorted_values[:mid])
    root.right = _build_bst_from_sorted_values(sorted_values[mid+1:])
    return root

def right_subtree(root):
    if not root:
        return
    result = []
    stack = [root.right]
    while stack:
        node = stack.pop()
        if node:
            result.append(str(node.val))
            stack.append(node.right)
            stack.append(node.left)
    if result:
        print(" -->".join(result), end=" -->\n")

def postorder(root, result):
    if root:
        postorder(root.left, result)
        postorder(root.right, result)
        result.append(root)
    return result

def is_bst(root, min_val=float('-inf'), max_val=float('inf')):
    if not root:
        return True
    if not (min_val < root.val < max_val):
        return False
    return (is_bst(root.left, min_val, root.val) and 
            is_bst(root.right, root.val, max_val))

n = int(input())
values = []
for i in range(n):
    values.append(int(input()))
sorted_values = sorted(values)
root = _build_bst_from_sorted_values(sorted_values)

postorder_result = postorder(root, [])
print("Postorder :", postorder_result)
print("Right Subtree :")
right_subtree(root)
print("Is this a Binary Search Tree? ", is_bst(root))
```

**OUTPUT:**  
```
8
12
8
3
10
1
6
4
9
Postorder : [Node(1), Node(3), Node(6), Node(4), Node(9), Node(12), Node(10), Node(8)]
Right Subtree :
10 -->9 -->12 -->
Is this a Binary Search Tree?  True
```

**RESULT:**  
The program successfully builds a balanced BST from sorted values, performs postorder traversal, displays the right subtree with arrow formatting, and correctly verifies the BST property. All test cases pass with accurate output.
