# Algorithm Evaluation

## Time Complexity

### Calculation
1. Consider only the worst case
2. Eliminate low order terms
3. Eliminate multiplicative constants

### Big-Theta Notation Definition

$R(N) \in \varTheta(f(N))$ 

means there exist positive constants $k_1$ and $k_2$ such that:

$k_1 \cdot f(N) \le R(N) \le k_2 \cdot f(N)$

for all values of N greater than some $N_0$. (i.e. very large N)

### Big-O and (Big-Omega)

$R(N) \in O(f(N))$ -> $ R(N) \le k_2 \cdot f(N)$
$R(N) \in \Omega(f(N))$ -> $ R(N) \le k_2 \cdot f(N)$


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

### SLList (Singly Linked List)
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
  
### DLList (Doubly Linked List)
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

### Resizing Array (AList)
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

### ListOfSetsDS
List of sets. 
| Constructor | connect | isConnected |
| --- | --- | --- |
| $\varTheta(N)$ | O(N) | O(N) |


### QuickFindDS
List of integers where ith entry gives set number(a.k.a. "id") of item i.
[Here is the code](./Blocks/QuickFindDS.md)
| Constructor | connect | isConnected |
| --- | --- | --- |
| $\varTheta(N)$ |  $\varTheta(N)$ |  $\varTheta(1)$ |

### QuickUnionDS
Trees of connected items.
[Here is the code](./Blocks/QuickUnionDS.md) 
| Constructor | connect | isConnected |
| --- | --- | --- |
| $\varTheta(N)$ | O(N) | O(N) |

(Trees can get very tall, so isConnected is O(N))

### ⭐Weighted QuickUnion
The improvement of QuickUnionDS, avoid too tall tree.
The rule to merge two trees is based on weight, not height.
| Constructor | connect | isConnected |
| --- | --- | --- |
| $\varTheta(N)$ | $O(\log n)$ | $O(\log n)$ |


