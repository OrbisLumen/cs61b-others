# Algorithm Evaluation

## Time Complexity

### Calculation
1. Consider only the worst case
2. Eliminate low order terms
3. Eliminate multiplicative constants

### $\varTheta$ Definition

$R(N) \in \varTheta(f(N))$ 

means there exist positive constants $k_1$ and $k_2$ such that:

$k_1 \cdot f(N) \le R(N) \le k_2 \cdot f(N)$

for all values of N greater than some $N_0$. (i.e. very large N)

### $O$ and ($\varOmega$)

$R(N) \in O(f(N))$ -> $ R(N) \le k_2 \cdot f(N)$
$R(N) \in \Omega(f(N))$ -> $ R(N) \le k_2 \cdot f(N)$

### Amortized Runtime

Any single operation may take longer, but if we use it over many operations, we're guranteed to have a better average performance.


# Data Structure

## Linked Data Structures

### Basic

1. IntNode (Basic Structure)

    ```java
    public class IntNode {

        public int item;
        public IntNode next;

        public IntNode(int f, IntNode r) {
            item = f;
            next = r;
        }
    }
    ```
2. Generics List

    - Using `Generics` to build list

### SLList 
(Singly Linked List)
[(Here is the code)](./Blocks/SLList.md)
   
```
(sentinel)
+--------+     +--------+     +--------+     +--------+
|   0    | --> |  item  | --> |  item  | --> |  item  | --> null
+--------+     +--------+     +--------+     +--------+
```
 - Promotions :
      - `size`
      - `sentinel`
  
### DLList 
(Doubly Linked List)
(Circular Sentinel)

```
    +--------+      +--------+      +--------+      +--------+
    |sentinel| <--> |  item  | <--> |  item  | <--> |  item  |
    +--------+      +--------+      +--------+      +--------+
        ^                                               ^
        |_______________________________________________|
```

- Promotions :
       - `last` (quicker access)

## Array (java)

### Basic
1. Arrays are a special kind of object which consists of a **numbered** sequence of memory boxes.
2. Array's length cannot be changed.
3. Arrays do not have method.
4. Create a new array :
    ```java
    int[] x = new int[5];                   
    int[] y = new int[]{0, 1, 2, 95, 4};
    int[] z = {0, 1, 2, 3, 4};
    ```
5. Arrays have an attribute `length`.
6. Copy arrays
    ```java
    System.arraycopy(a, 0, b, 2, 3); //Java
    ```
    ```python 
    b[2:5] = a[0:3] "Python"
    ```

### AList
(Resizing Array)
[(Here is the code)](./Blocks/AList.md)

## Disjoint Sets (并查集)

### Basic
The Disjoint Sets data structure has two operations:
- connect(x, y): Connects x and y
- isConnected(x, y): Returns true if x and y are connected. Connections can be transitive, i.e. they don't need to be direct.

```java
public interface DisjointSets {
    /** Connects teo items P and Q.*/
    void connect(int p, int q);

    /** Checks to see if two items are connected. */
    boolean isConnected(int p, int q);
}
```

### Asymptotics
1. ListOfSetsDS
    List of sets. 

    | Constructor | connect | isConnected |
    | --- | --- | --- |
    |$$\varTheta(N)$$ | $$O(N)$$ | $$O(N)$$ |


2. QuickFindDS
    List of integers where ith entry gives set number(a.k.a. "id") of item i.

    [Here is the code](./Blocks/QuickFindDS.md)
    | Constructor | connect | isConnected |
    | --- | --- | --- |
    | $$\varTheta(N)$$ |  $$\varTheta(N)$$ |  $$\varTheta(1)$$ |

3. QuickUnionDS
    Trees of connected items.
    - In the parent array, each index represents an item, and the value at that index represents that item's parent.
    - The root-item's value in the parent array is `-1`.

    [Here is the code](./Blocks/QuickUnionDS.md) 
    | Constructor | connect | isConnected |
    | --- | --- | --- |
    | $$\varTheta(N)$$ | $$O(N)$$ | $$O(N)$$ |

    (Trees can get very tall, so isConnected is O(N))

4. WeightedQuickUnionDS
    The improvement of QuickUnionDS, avoiding too tall tree.
    - In the parent array, each index represents an item, and the value at that index represents that item's parent.
    - The rule to merge two trees is based on weight, not height. (Simply because the weighted QuickUnion is easier to code, and both of them are $O(\log N)$)
    - The root stores the `negative size`(weight) of its tree in the parent array.

    | Constructor | connect | isConnected |
    | --- | --- | --- |
    | $$\varTheta(N)$$ | $$O(\log N)$$ | $$O(\log N)$$ |

### Completion

**Weighted QuickUnion with Path Compression**

The improvement of WeightedQuickUnionDS, using path compression.
- During find, perform `path compression` by making every node on the path point directly to the root. (Recursively)

[Here is the code](./Blocks/WeightedQuickUnionWithPathCompression.md)
| Constructor | connect | isConnected |
| --- | --- | --- |
| $$\varTheta(N)$$ | $$O(\alpha(N))$$ | $$O(\alpha(N))$$ |

(where α(N) is the inverse Ackermann function, which grows so slowly that for any practical N, it is less than 5.)

**Weighted Quick Union with Path Compression has almost constant time operations.**

## Trees

### Definition
1. Trees
   - A set of nodes.
   - A set of edges that connect those nodes.
     - Constraint: There is exactly one path between any two nodes.

2. Rooted Tree
   - In a rooted tree, we call one noede the root.
   - Every node N except the root has exactyly one parent, defined as the first node on the path from N to the root.
   - The root is usually depicted at the top of the tree.
   - A node with no child is called a leaf.

3. Rooted Binary Tree
   - Every node has either 0, 1 or 2 children (subtrees).

## Binary Search Trees

### Definition
A binary search tree is a rooted binary tree with the BST property.

**BST Property**. For evety node X in the Tree:
- Every key in the `left` subtree is `less` than X's key.
- Every key in the `right` subtree is `greater` than the X's key.

Ordering must be complete, transitive, and antisymmetric

No duplicate keys allowed.