# Sorting

## Definition

An **ordering relation** < for keys a, b, and c has the following properties:
- Law of Trichotomy: Exactly one of a < b, a = b, b > a is true.
- Law of Transitivity: If a < b, and b < c, then a < c.

A **sort** is a permutation (re-arrangement) of a sequence of elements that puts the keys into non-decreasing order relative to a given ordering relation.

An **inversion** is a pair of elements that are out of order with respect to <.

## Selection Sort

Selection sorting N items:
- Find the smallest item in the unsorted portion of the array.
- Move it to the end of the sorted portion of the array.
- Selection sort the remaining unsorted items.

**Run Time** $O(N^2)$

## Heap Sort

Heap sort can be viewed as an optimized version of selection sort.
Using **max heap** to select max item.

**In-place heap sort**:
  - Bottom-up heapify input array:
    - Sink nodes in reverse level order.
  - Repeat N times:
    - Delete largest item from the max heap.
    - Swapping root with last item in the heap.
    - Maintain the max heap.

**Run Time** $O(N \log N)$
**Extra Space** $\Theta (N)$ for new heap, $\Theta (1)$ for in-place heap.

## Merge Sort

Mergesort:
- Split items into 2 roughly even pieces.
- Mergesort each half. (Recursively)
- Merge the two sorted halves to form the final result.

**Run Time** $\Theta(N \log n)$
**Extra Space** $\Theta(N)$

## Insertion Sort

Repeat for i = 0 to N - 1:
- Designate item i as the traveling item.
- Swap item backwards until traveller is in the right place among all previously examined items.

**Run Time** $O (N^2)$