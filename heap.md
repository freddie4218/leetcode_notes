# Heap

#### Definition
> 1. Is a complete binary tree;
> 2. The value of each node must be no greater than (or no less than) the value of its child nodes.

#### Properties:
> 1. Insertion of an element into the Heap has a time complexity of $O(logN)$;
> 2. Deletion of an element from the Heap has a time complexity of $O(logN)$;
> 3. The maximum/minimum value in the Heap can be obtained with 
$O(1)$ time complexity.

#### Classificaitons:
Max Heap:
> Each node in the Heap has a value no less than its child nodes. Therefore, the top element (root node) has the largest value in the Heap.

Min Heap:
> Each node in the Heap has a value no larger than its child nodes. Therefore, the top element (root node) has the smallest value in the Heap.

#### Applications in Python:

##### Construct a Heap: 

> Complexities of heapq.heapify():  
Time Complexity: $O(N)$  
Space Complexity: $O(N)$

```
import heapq

# Construct a Heap with Initial values
# this process is called "Heapify"
# The Heap is a Min Heap

heapWithValues = [3,1,2]
heapq.heapify(heapWithValues)

# Constructing a Max Heap

maxHeap = [1,2,3]
maxHeap = [-x for x in maxHeap]
heapq.heapify(maxHeap)

# The top element of maxHeap is -3
# Convert -3 to 3, which is the maximum value in the original maxHeap
```

##### Inserting an Element:
> Complexities of heapq.heappush():  
Time Complexity: $O(logN)$  
Space Complexity: $O(1)$

```
# Insert an element to the Min Heap
heapq.heappush(minHeap, 5)

# Insert an element to the Max Heap
# Multiply the element by -1
heapq.heappush(maxHeap, -1 * 5)
```

##### Getting the Top Element of the Heap:
> Complexities of minHeap[0]:  
Time Complexity: $O(logN)$  
Space Complexity: $O(1)$

```
# Get top element from the Min Heap
minHeap[0]

# Get top element from the Max Heap
-1 * maxHeap[0]
```

##### Deleting the top element:
> Complexities of heapq.heappop():  
Time Complexity: $O(logN)$  
Space Complexity: $O(1)$

```
# Delete top element from the Min Heap
heapq.heappop(minHeap)

# Delete top element from the Max Heap
heapq.heappop(maxHeap)
```

##### Getting the Length of a Heap:
> Complexities of len(minHeap):  
Time Complexity: $O(1)$  
Space Complexity: $O(1)$

```
# Length of the Min Heap
len(minHeap)

# Length of the Max Heap
len(maxHeap)
```

