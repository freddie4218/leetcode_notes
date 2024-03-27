# Selection Sort

> Suppose we had a collection of elements where every element is an integer. Selection sort will build up the sorted list by <mark>**repeatedly finding the minimum element in that list and moving it to the front of the list through a swap**</mark>. It will proceed to swap elements appropriately until the entire list is sorted..

#### Code Sample:

```
def selection_sort(self, lst: List[int]) -> None:
    for i in range(len(lst)):
        min_index = i
        for j in range(i + 1, len(lst)):
            # Update minimum index
            if lst[j] < lst[min_index]:
                min_index = j
        # Swap current index with minimum element in rest of list
        lst[min_index], lst[i] = lst[i], lst[min_index]
```

#### Complexity:

Time: $O(n^2)$
Space: $O(1)$
Stability: Non-stable

---

# Bubble Sort

> Conceptually, bubble sort is an implementation of a rather simple idea. Suppose we have a collection of integers that we want to sort in ascending order. <mark>**Bubble sort proceeds to consider two adjacent elements at a time. If these two adjacent elements are out of order (in this case, the left element is strictly greater than the right element), bubble sort will swap them. It then proceeds to the next pair of adjacent elements**</mark>. In the first pass of bubble sort, it will process every set of adjacent elements in the collection once, making swaps as necessary. The core idea of bubble sort is <mark>**it will repeat this process until no more swaps are made in a single pass**</mark>, which means the list is sorted.

#### Code Sample:

```
def bubble_sort(self, lst: List[int]) -> None:
        has_swapped = True
        # if no swap occurred, lst is sorted
        while has_swapped:
            has_swapped = False
            for i in range(len(lst) - 1):
                if lst[i] > lst[i + 1]:
                    # Swap adjacent elements
                    lst[i], lst[i + 1] = lst[i + 1], lst[i]
                    has_swapped = True
```

#### Complexity:

Time: $O(n^2)$
Space: $O(1)$
Stability: Stable [^1]

[^1] This is because equal elements would not be swapped, since the condition for swapping is that the left element is **strictly** greater than the right element.

---
# Insertion Sort
> Given a collection of integers, you can sort the list by <mark> **proceeding from the start of the list, and every time you encounter an element that is out of order, you can continuously swap places with previous elements until it is inserted in its correct relative location based on what you’ve processed thus far**</mark>.
#### Code Sample:
```
def insertion_sort(self, lst: List[int]) -> None:
        for i in range(1, len(lst)):
            current_index = i
            
            while current_index > 0 and lst[current_index - 1] > lst[current_index]:
                # Swap elements that are out of order
                lst[current_index], lst[current_index - 1] = lst[current_index - 1], lst[current_index]
                current_index -= 1
```
#### Complexity:

Time: $O(n^2)$
Space: $O(1)$
Stability: Stable

---

# Heap Sort

The key idea for in-place heapsort involves a balance of two central ideas:  
>(a) Building a heap from an unsorted array through a “bottom-up heapification” process, and  
(b) Using the heap to sort the input array.


#### Code Sample:
```
class Solution:
    def heap_sort(self, lst: List[int]) -> None:
        """
        Mutates elements in lst by utilizing the heap data structure
        """
        def max_heapify(heap_size, index):
            left, right = 2 * index + 1, 2 * index + 2
            largest = index
            if left < heap_size and lst[left] > lst[largest]:
                largest = left
            if right < heap_size and lst[right] > lst[largest]:
                largest = right
            if largest != index:
                lst[index], lst[largest] = lst[largest], lst[index]
                max_heapify(heap_size, largest)

        # heapify original lst
        for i in range(len(lst) // 2 - 1, -1, -1):
            max_heapify(len(lst), i)

        # use heap to sort elements
        for i in range(len(lst) - 1, 0, -1):
            # swap last element with first element
            lst[i], lst[0] = lst[0], lst[i]
            # note that we reduce the heap size by 1 every iteration
            max_heapify(i, 0)
```

#### Complexity:

Time: $O(NlogN)$  
Space: $O(1)$  
Stability: Non-stable

---

# Count Sort

> The basic idea behind Counting Sort is to <mark> count the frequency of each distinct element in the input array and use that information to place the elements in their correct sorted positions</marks>.


#### Code Sample:
```
    def counting_sort(self, lst: List[int]) -> None:
        """
        Sorts a list of integers (handles shifting of integers to range 0 to K)
        """
        shift = min(lst)
        K = max(lst) - shift
        counts = [0] * (K + 1)
        for elem in lst:
            counts[elem - shift] += 1

        # we now overwrite our original counts with the starting index
        # of each element in the final sorted array
        starting_index = 0
        for i, count in enumerate(counts):
            counts[i] = starting_index
            starting_index += count

        sorted_lst = [0] * len(lst)
        for elem in lst:
            sorted_lst[counts[elem - shift]] = elem
            # since we have placed an item in index counts[elem], we need to
            # increment counts[elem] index by 1 so the next duplicate element
            # is placed in appropriate index
            counts[elem - shift] += 1

        # common practice to copy over sorted list into original lst
        # it's fine to just return the sorted_lst at this point as well
        for i in range(len(lst)):
            lst[i] = sorted_lst[i]
        return lst
```

#### Complexity:

Time: $O(N + K)$, where $N$ is the size of the input array and $K$ is the maximum value in the array  
Space: $O(N + K)$  
Stability: Stable

