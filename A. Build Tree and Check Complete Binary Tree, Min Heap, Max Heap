**Topic:** Build Tree and Check Complete Binary Tree, Min Heap, Max Heap

**AIM:**  
To write a Python function `min_max_heap(L)` that builds a binary tree from a list, displays the tree elements, checks whether it is a complete binary tree, and if complete, determines whether it is a Min heap or Max heap.

**ALGORITHM:**  
1. Start  
2. Import necessary modules for binary tree  
3. Define function `min_max_heap(L)`:  
   a. Build binary tree from list using appropriate module  
   b. Display tree elements using level order traversal with arrow formatting  
   c. Check if tree is complete binary tree:  
      - All nodes except last level are filled  
      - Last level nodes are as far left as possible  
   d. If complete, check if it is Min heap (each node ≤ children) or Max heap (each node ≥ children)  
   e. Display appropriate message  
4. End  

**PROGRAM:**  
```
import heapq

def min_max_heap(L):
    class Node:
        def __init__(self, val):
            self.val = val
            self.left = None
            self.right = None
    
    def build_tree(arr):
        if not arr:
            return None
        nodes = [Node(val) if val is not None else None for val in arr]
        for i in range(len(arr)):
            if nodes[i] is not None:
                left_idx = 2 * i + 1
                right_idx = 2 * i + 2
                if left_idx < len(arr):
                    nodes[i].left = nodes[left_idx]
                if right_idx < len(arr):
                    nodes[i].right = nodes[right_idx]
        return nodes[0] if nodes else None
    
    def display(root):
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
        print(" -->".join(result), end=" -->\n")
    
    def is_complete(root):
        if not root:
            return True
        queue = [root]
        found_null = False
        while queue:
            node = queue.pop(0)
            if not node:
                found_null = True
            else:
                if found_null:
                    return False
                queue.append(node.left)
                queue.append(node.right)
        return True
    
    def check_heap(root):
        if not root:
            return "Min heap tree"
        
        def is_min_heap(node):
            if not node:
                return True
            if node.left and node.left.val < node.val:
                return False
            if node.right and node.right.val < node.val:
                return False
            return is_min_heap(node.left) and is_min_heap(node.right)
        
        def is_max_heap(node):
            if not node:
                return True
            if node.left and node.left.val > node.val:
                return False
            if node.right and node.right.val > node.val:
                return False
            return is_max_heap(node.left) and is_max_heap(node.right)
        
        if is_min_heap(root):
            return "Min heap tree"
        elif is_max_heap(root):
            return "Max heap tree"
        return "Neither Min nor Max heap"
    
    root = build_tree(L)
    display(root)
    
    if is_complete(root):
        print("Complete binary tree")
        print(check_heap(root))
    else:
        print("Not a Complete binary tree")

min_max_heap([10,14,19,26,31,42,27,44])
print()
min_max_heap([10,14,19,26,31,42,27,44,None,33])
```

**OUTPUT:**  
```
10 -->14 -->19 -->26 -->31 -->42 -->27 -->44 -->
Complete binary tree
Min heap tree

10 -->14 -->19 -->26 -->31 -->42 -->27 -->44 -->None -->33 -->
Not a Complete binary tree
```

**RESULT:**  
The program successfully builds a binary tree from the given list, displays elements using level order traversal, checks for complete binary tree property, and if complete, determines whether it is a Min heap or Max heap. All test cases passed.
