**Topic:** Convert Binary Search Tree to Heap Tree

**AIM:**  
To write a Python program that converts a given Binary Search Tree (BST) into a heap tree using appropriate Python packages and functions.

**ALGORITHM:**  
1. Start  
2. Define function `heaptree(arr)` that takes a list of BST elements  
3. Import heapq module for heap operations  
4. Convert the given BST elements into a min heap using `heapq.heapify()`  
5. Display the resulting heap as a list  
6. End  

**PROGRAM:**  
```
import heapq

def heaptree(arr):
    heapq.heapify(arr)
    print(f"The created Heap is {arr}")

heaptree([5,3,8,2,4,6,10])
```

**OUTPUT:**  
```
The created Heap is [2, 3, 6, 5, 4, 8, 10]
```

**RESULT:**  
The program successfully converts the given Binary Search Tree elements into a heap tree using the `heapq` module. The `heapify()` function transforms the list into a min heap structure, satisfying the heap property where each parent node is less than or equal to its children.
