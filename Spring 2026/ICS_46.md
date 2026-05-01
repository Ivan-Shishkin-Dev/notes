# Lecture 1: Algorithms & Analysis

**Algorithm**

- A clearly specified set of instructions to be followed to solve a specific problem
	- Adding two n-digit numbers
	- Sorting a list of n names
	- Finding one student's name among N students
- This N is important
	- The number of items we are dealing with
	- What happens as N grows very large

- Sequential search → O(N) time
- Binary search → O(log N) time, but the list must be sorted
- 2³² is 4 billion → only 32 comparisons to search all 8 billion people if you cut in half each time

**Important Questions About Algorithms**

- Is it correct?
- How much extra memory does it require? → memory complexity → [[ICS_51#Lecture 2: System Organization|see how memory is physically organized in ICS 51]]
- How long does it take? → time complexity

The analysis of these two questions is critical to algorithm selection

**T(N)**

- The time required for an algorithm to run on input of size N
- Simple instructions → +1 operation (+, −, ·, /, ...)
- Loops → sum of nested instructions times the number of loop iterations
- Function calls → T(N) of the called function
- If/else → maximum of either branch plus the cost of the condition
	- Only one branch executes, so take the worst case PLUS the additional check of the condition (which can involve multiple checks)

**How to Report T(N)**

- State the actual polynomial and say it is equal to the following
- Count the number of run-time instructions

**Example: Summing 1 to N**

```cpp
int sum( int N )
{  
    int result = 0; // 1
    for( int i=1;   // 1
          i <= N; ++i )     // 2        LOOP N TIMES -> N * ( 2 + 2 = 4)
            result = result + i;  // 2
    return result;  // 1
}
```

- T(N) = 4N + 3

```cpp
int sum( int N )
{     
    return N * ( N + 1 ) / 2;
}
```

- T(N) = 4
- The return adds 1 plus all the expressions

**Example: Strange Sum**

```cpp
int strangeSum( int A[N] )
{
        int total = 0; //1
        for(int i=0; //1
         i < N; ++i ) // n-1, 1
            total = total + A[i-1] * A[i]; //4
        return total; //1
}
```

- Array indexing → cost of the index plus 1 (same rule as return)
- T(N) = 8N + 3
	- Outside of loop there are 3 operations
	- The 8 inner operations happen from 0 to N times → total of N times

**Example: Bubble Sort**

```cpp
void swap( int & a, int & b )  // T(N) = 3
{
    int t = a; a = b; b = t;
}

void bubbleSort( int A[N] )  // A tricky one...
{
  for ( int a = 0; a < N; a++ ) // RUNS N times
      for ( int b = N - 1; b > a; b-- ) // sum of all N integers with the combination of 2 loops
          if ( A[b-1] > A[b] )    // condition is 4  // IF is 4 + max(6,0) = 10
              swap( A[b-1], A[b] ); // then part is 6 (the accessing is 3 plus the call of the function)
}
```

- N · (N − 1) / 2 is the closed form for the sum of N integers
- T(N) = 10 · (N · (N + 1)) / 2 →
- 5 · (N² + N) →
- 5N² + 5N + 1 → final form

**GitCodings**

```cpp
// What is T(N) of strlen(), if N is the length of s?
int strlen( char *s ) { 
    int len = 0;
     for ( int i = 0; s[i] != 0; ++i )
          ++len;
     return len;
}

// My Guess: T(N) = 4N + 3
// Right Answer: T(N) = 4N + 3
```

```cpp
int strchr( char c, char *s ) // V1
{
       for ( int i=0; i < strlen(s); ++i )
               if ( s[i] == c )
                      return i;
       return -1;
} 
// My Guess: T(N) = 2(4N + 3) + 2
```

- The strlen is 4N + 3 plus 2 for the other 2 operations in the for loop
	- N · (4N + 5 + 3) for the if statement, then plus 2 for the outside of the loop
	- T(N) = 4N² + 8N + 2

```cpp
int strchr( char c, char *s )  // V2
{
       int len = strlen(s);
       for ( int i=0; i < len; ++i )
               if ( s[i] == c )
                      return i;
       return -1;
}
```

- T(N) =
	- First: initialize len plus strlen → 4N + 3 + 1
	- Loop runs N times with 5 operations inside
	- Return → +2
- 4N + 4
- 5N + 2
- T(N) = 9N + 6 → correct answer!

```cpp
// What is T(N) of strchr(), if N is the length of s?
int strchr( char c, char *s )  // V3
{
       for ( int i=0; s[i] != '\0'; ++i )
               if ( s[i] == c )
                      return i;
       return -1;
}
```

- 1 for the initialization
- 6N + 2 → confident
- Real answer is: that I am a dawg

**Asymptotic Analysis**

- As N gets larger, what is the performance hit?
- When you multiply by large numbers, things grow rapidly
- Best Case
- Worst Case
- Expected Case (Middle)

**Big-O Notation**

- As N gets large, the lower-order terms are negligible
- We care most about the highest-order term
- T(N) = 4N² + 6N + 40
- T(N) = 2N⁴ + 1000N² + 30N + 2000
- Big-O (pronounced "big oh")
	- T(N) = O(f(N)) if there are positive constants c and n₀ such that T(N) ≤ c · f(N) when N ≥ n₀
	- Don't care about low orders of N
	- Find what it is bounded by
- Big-O → upper bound (the closest function that bounds it from above)
- Omega → lower bound
- Theta → tightly bound (strictly exactly there)

**Typical Growth Rates**

| Function | Name |
| --- | --- |
| C | constant |
| log N | logarithmic |
| N | linear |
| N log N | log-linear |
| N² | quadratic |
| 2ᴺ | exponential |
| N! | factorial |

- 2³² is 4 billion
- 2³³ is 8 billion
- 10¹⁰⁰ is about 70!

**Ranking of Big-O (Slowest Growth to Fastest)**

1. O(1)
2. O(log N)
3. O(N log N)
4. O(N²)
5. O(2ᴺ)
6. O(N!)

Reporting Big-O → just say "Big-O of N²" and that's all

**Activity**

1. T(N) = 10N⁴ + 2N² log N − N³ → O(N⁴)
2. T(N) = log₂ N + N log N + N² → O(N²)
3. T(N) = Nᴺ + N! → O(Nᴺ)
4. T(N) = 2^(N/2) + 3N log N → O(2ᴺ)

# Lecture 2: Unordered Lists

**Unordered Lists**

- Lists may be
	- Unordered
	- Ordered
	- Sorted
- Typical operations
	- insert, find, remove, length, print
- Lists may be implemented as
	- An array list (within an array) → [[ICS_51#Memory View|memory is a linear array at the hardware level]]
	- A linked list (using nodes with links/pointers)
- Always consider time complexities → [[ICS_46#Lecture 1: Algorithms & Analysis|Big-O from Lecture 1]]

**Unordered List: Implemented as Array**

- What data members do we need?
	- The array
	- Capacity → physical size (possible), don't exceed capacity
	- Current size → logical size (actual size)
- Think about each operation (algorithm)
	1. insert
	2. find
	3. remove
- How can each be implemented efficiently given the requirements? (Unordered)

**Unordered Array List**

```cpp
// Example is a List of char

class UnorderedArrayList {
    char * buf;  // an array of List Elements (char)
    int capacity;
    int size;
public:
    UnorderedArrayList(int cap)
        :buf{new char[cap]}, capacity{cap}, size{0}
    { }
```

**Adding to Front vs Adding to End**

- `size` is the index of the next available slot
- Adding to the front causes you to shift all existing elements over

**Efficiency on Removal**

- Removal can be done by replacing with the last element and decrementing size
- Don't have to null out values → they are effectively gone

**Insert**

```cpp
void error(string msg) {
    cerr << "WTH: Error: Who wrote this code" << msg << endl;
}

// adds 'c' where it belongs in this list 
void insert(char c) {

    // This was added post checking the first normal case
    if (is_full()) {error("UAList::insert() into full list");}
       
    buf[size++] = c;
    // Notice the post-increment: it uses the original value and THEN increments 
}
```

1. Write the first normal case
2. Add error checking (beginning in this case)

**Find**

```cpp
// returns index of 'c' 
int find(char c) { 
     for (int i = 0; i < size; ++i) {
       if (buf[i] == c) {return i;}
     }
   error("Not found");
}
```

**Remove**

```cpp
// removes first occurrence of c

int remove(char c) { 
    for (int i = find(c); i < size - 1; i++) {
        arr[i] = arr[i + 1];
    }
    --size;
}
```

- Not sure about this one → figure it out later

**Measuring Performance**

- Divide the data into partitions (e.g., 10)
- Measure on first partition 
	- Then first and second
	- Then first, second, third, etc.
- Plot N vs T(N)
- Graph shows the time complexity of the function
- Must be careful to time only the work of interest
	- start() and stop() timer around the work
- We measure insert_all(), find_all(), remove_all() → why?
	- There is jitter (variation) in data, and under large data sets it's more visible

![[ICS_46-1775773956342.webp|433]]

- No zigzag line → should be a smooth curve
- 45,392 words is specific to our word set
	- Start with 1/10th of the data, then 2/10ths, etc.

**Framework vs Library**

- A library works within your software. Your software works inside a framework.
- To build a framework you need virtual functions and abstract classes
- Write the measurement code only once → that's the framework's job

**Architecture vs Framework (Aside)**

- Architecture → high-level, abstract plan for a system defining major components and their interactions
- Framework → concrete, reusable set of code and libraries that helps implement an application within the boundaries set by the architecture

**Unordered List Implemented as Linked List**

- Use a helper class `ListNode`
	- Two data members:
		- `data` (string in this case)
		- `next` (pointer to next `ListNode`)
- Useful to write helper methods
	- Allows more re-use of helper functions
	- Allows recursion
	- Simplifies non-static list methods
- Think about each operation:
	- `insert` → insert at head (unordered, so position doesn't matter)
	- `find`
	- `remove`

**Singly Linked List Node**


```cpp
// ListNode helper class
struct ListNode {
    char data;
    ListNode * next;
};

ListNode * p = nullptr;          // the empty list
p = new ListNode{d, p};          // adds d onto front of p
// Uses curly-brace (aggregate) initialization, not parens
// Data members must all be public for this to work
```

**Linked List insert()**

```cpp
class UnorderedLinkedList {
    struct ListNode {
        char data;
        ListNode * next;
    };
    ListNode * head;

public:
    UnorderedLinkedList() : head{nullptr} { }

    void insert(char c) {
        head = new ListNode{c, head};
    }
};
```

**Linked List find()**

```cpp
class UnorderedLinkedList {
    // private static helper — searches from node L
    static ListNode * find(char c, ListNode * L) {
        for (ListNode * p = L; p != nullptr; p = p->next) {
            if (p->data == c)
                return p;
        }
        return nullptr;
    }

public:
    char & find(char c) {
        ListNode * p = find(c, head);
        if (p != nullptr)
            return p->data;
        // else: do whatever is appropriate
        // e.g., could add c to head of list, then return head->data
    }
};
```

**Linked List length()**

```cpp
class UnorderedLinkedList {
    static int length(ListNode * L) {
        int count = 0;
        for (ListNode * p = L; p != nullptr; p = p->next)
            ++count;
        return count;
    }
    ListNode * head;

public:
    int size() {
        return length(head);
    }
};
```

**Linked List remove()**

```cpp
class UnorderedLinkedList {
    static ListNode * remove(char c, ListNode * L) {
        // implementation left as exercise
    }
    ListNode * head;

public:
    void remove(char c) {
        head = ListNode::remove(c, head);
    }
};
```

# Lecture 3: Sorted Lists & Binary Search

**Benchmarking Unordered Lists — Theory vs. Reality**

![[ICS_46-1776205956700.webp|500x269]]

- The measured times don’t match the predicted Big-O complexities — why?
- **Array List anomalies:**
	- **Insert all** → predicted O(1) per insert, measured O(N) total — makes sense, we’re calling O(1) insert N times
		- Inserting at the end in the same order as the file → truly O(1) each
	- **Find all words** → predicted O(N) per find, but measured ~100× slower than insert
		- Calling O(N) find N times → O(N²) total
	- **Remove all words** → should also be O(N²) like find-all, but measured at roughly **half** the time of find-all
		- Why half? The "swap-to-back" removal trick: find the word, swap it with the last element, decrement size → the removal itself is O(1)
		- Each successive removal shrinks the array, so on average you’re searching through N/2 elements → total work ≈ N²/2
		- First removals are fast (element might be near the front or the array is large but you get lucky), later removals search a smaller array but from the start
- **Linked List:**
	- **Insert all** → O(1) per insert (prepend to head), O(N) total
	- **Find all words** → O(N) per find × N words → O(N²) total
	- **Remove all words** → O(N) per remove × N words → O(N²) total
- **Why does the array’s remove-all take half the time but the linked list’s doesn’t?**
	- Array remove uses the swap-to-back trick → each removal is O(1) after finding, and the shrinking array means average search length is N/2
	- Linked list remove has no such shortcut — you traverse to find the node, then unlink it (O(1) unlink, but still O(N) traversal each time), and unlinking doesn’t reduce traversal time the same way because you still walk from the head every time
	- Both end up O(N²), but the array version has a constant factor of ~½

- **Aside:** What does N · log N look like? → just a tiny bit more than O(N) — nearly linear

**Other List Types**

- We’ve studied unordered lists, but there are others:
- **Circular lists** → e.g., repeat playlist in a music player — last node points back to first
- **Doubly Linked List** → e.g., `std::list` in C++
	- O(1) insert(), O(1) remove() (given a pointer to the node), O(N) find()
- **Ordered lists** → items retained in insertion order
	- Operations: insert, find, remove
	- e.g., `std::string` (characters in order of insertion)
- **Sorted lists** → items retained in **sorted** order
	- e.g., student roster, phone book
- **Performance tradeoff aside:**
	- `find` is the most frequently called operation in practice
	- Unordered lists → insert is the fast one (O(1) prepend/append)
	- Sorted lists → find is faster (binary search possible on arrays)

**Sorted Lists**

- Similar to unordered lists, but items are maintained in sorted order
	- Order may be ascending or descending
	- Approach: insert incrementally in the right spot (not "dump everything in, then sort" — that’s eager sorting and it’s wasteful)
	- e.g., student roster, phone book, book index
- Typical operations: insert, find, remove, length, print
- May be implemented as:
	- **Array list:**
		- `find` → O(log N) using binary search
		- `insert` → O(log N) to find position + O(N) to shift elements right → **O(N)** total
		- `remove` → O(log N) to find + O(N) to shift elements left → **O(N)** total
	- **Linked list:**
		- `find` → O(N) linear scan (can’t do binary search — no random access)
		- `insert` → O(N) to walk to the right spot + O(1) to link → **O(N)** total
		- `remove` → O(N) to find + O(1) to unlink → **O(N)** total
- How to keep it sorted? → **Incrementally** — insert each new element in its correct position

**Quick recall:** 2³² = ~4 billion, 2³³ = ~8 billion

**Sorted Array List — Class Definition**

```cpp
class SortedArrayList {
    char * buf;
    int capacity;
    int size;
public:
    SortedArrayList(int cap)
        : buf{new char[cap]}, capacity{cap}, size{0}
    { }
};
```

- **Member initializer list order:** the initialization happens in **order of declaration** of data members, NOT the order they appear in the initializer list
	- Here the declaration order is: `buf`, `capacity`, `size` — so they initialize in that order
	- This is correct and safe here because `buf`’s initialization (`new char[cap]`) uses the constructor parameter `cap`, not the member `capacity`
	- If `buf`’s init depended on `capacity` being set first, we’d have a bug since `buf` is declared (and thus initialized) before `capacity`

**Binary Search (Array)**

```cpp
// Returns the index where ‘c’ IS or WHERE IT WOULD GO if inserted
// This lets us reuse binary_search for find, insert, AND remove
int binary_search(char c, char A[], int low, int high) {
    while (low <= high) {
        int mid = low + (high - low) / 2;  // avoid overflow vs (low+high)/2
        if (A[mid] == c)
            return mid;          // found it
        else if (A[mid] < c)
            low = mid + 1;       // search right half
        else
            high = mid - 1;      // search left half
    }
    return low;  // not found — low is the insertion point
}
```

- Returns the **insertion point** — the index where `c` would go to maintain sorted order
- If the element exists, it returns its index; if not, it returns where it *should* be
- Complexity: **O(log N)** — halving the search space each iteration

**Binary Search on a Linked List?**

- You technically can’t do efficient binary search on a linked list — there’s no O(1) random access
- To reach the "middle" node you’d have to walk N/2 links → O(N)
- Doing that recursively still ends up **O(N)** total (N/2 + N/4 + N/8 + ... ≈ N)
- So linked list find remains **O(N)** — binary search doesn’t help here
- This is the key advantage of sorted **array** lists over sorted **linked** lists

**Using binary_search as a Helper**

- `binary_search()` is the core helper — `find`, `insert`, and `remove` all use it
- **find(c):** call `binary_search(c, buf, 0, size-1)` → get index `i` → check if `buf[i] == c` → O(log N)
- **insert(c):** call `binary_search` to get insertion point → shift elements right → place `c` → O(N) due to shifting
- **remove(c):** call `binary_search` to find it → shift elements left → O(N) due to shifting
- **Not all O(N) are equal** — the constant factor matters when complexities are the same

**Sorted Array List: find()**

```cpp
// Uses binary_search helper — O(log N)
bool find(char c) {
    int i = binary_search(c, buf, 0, size - 1);
    return (i < size && buf[i] == c);
}
```

**copy_down — Shifting Elements Left (for remove)**

```cpp
// Array version — shift elements left to fill the gap at index ‘pos’
void copy_down(char A[], int pos, int size) {
    for (int i = pos; i < size - 1; ++i)
        A[i] = A[i + 1];
}
```

- Used in `remove()`: find the element via binary search, then shift everything after it one position left
- O(N) in the worst case (removing the first element)

**copy_up — Shifting Elements Right (for insert)**

```cpp
// Array version — shift elements right to make room at index ‘pos’
void copy_up(char A[], int pos, int size) {
    for (int i = size; i > pos; --i)
        A[i] = A[i - 1];
}
```

- Used in `insert()`: binary search for the insertion point, shift everything right, then place the new element
- O(N) in the worst case (inserting at position 0)

**Sorted Array List: insert() and remove()**

```cpp
void insert(char c) {
    int pos = binary_search(c, buf, 0, size - 1);
    copy_up(buf, pos, size);  // make room
    buf[pos] = c;
    ++size;
}

void remove(char c) {
    int pos = binary_search(c, buf, 0, size - 1);
    if (pos < size && buf[pos] == c) {
        copy_down(buf, pos, size);
        --size;
    }
}
```

**Unordered List: equal()**

```cpp
// Two unordered lists are equal if they have the same elements (in the same order for this version)
bool equal(const UnorderedArrayList & other) const {
    if (size != other.size) return false;
    for (int i = 0; i < size; ++i) {
        if (buf[i] != other.buf[i]) return false;
    }
    return true;
}
```

**Testing Aside**

- **Nominal testing** → test normal/expected inputs (the "happy path")
- **Boundary conditions** → test edge cases:
	- Front and end of structure
	- Empty string and single-character string in `reverse_string`
	- Empty list, single-element list, duplicate elements

# Lecture 4: Linked Lists

**Sorted Linked List: Find**
- If the list is sorted and we pass the value we're searching for → stop early
	- No point continuing once `curr->data > c`

**Writing Methods Recursively**
- Watch out for large N on an O(n) recursion → blows the stack
- Prefer iteration when depth can grow with input size

**Pointers**
- Pointers are cheap
- Common pattern for traversal/mutation → `prev`, `curr`, `next`

**Sorted Linked List: insert()**

```cpp
// return list with c added in the correct (sorted) spot
static ListNode * ListNode::insert(char c, ListNode * L) {
    ListNode * node = new ListNode(c);

    // empty list or insert at front
    if (L == nullptr || c <= L->data) {
        node->next = L;
        return node;
    }

    // find the node after which c belongs
    ListNode * curr = L;
    while (curr->next != nullptr && curr->next->data < c) {
        curr = curr->next;
    }
    node->next = curr->next;
    curr->next = node;
    return L;
}
```

**Sorted Linked List: find()**

```cpp
// return pointer to node containing c, nullptr otherwise
// sequential search down L, stop when c >= L->data (sorted list)
static ListNode * ListNode::find(char c, ListNode * L) {
    while (L != nullptr && L->data < c) {
        L = L->next;
    }
    if (L != nullptr && L->data == c) return L;
    return nullptr;
}
```

**Sorted Linked List: remove()**

```cpp
// return list with c removed
static ListNode * ListNode::remove(char c, ListNode * L) {
    if (L == nullptr) return nullptr;

    // case: removing the first node
    if (L->data == c) {
        ListNode * rest = L->next;
        delete L;
        return rest;
    }

    // walk with prev/curr, stop at match or past-it (sorted)
    ListNode * prev = L;
    ListNode * curr = L->next;
    while (curr != nullptr && curr->data < c) {
        prev = curr;
        curr = curr->next;
    }
    if (curr != nullptr && curr->data == c) {
        prev->next = curr->next;
        delete curr;
    }
    return L;
}
```
- **Three cases to test**:
	1. Maintain a `prev` pointer
	2. Test on a middle node
	3. Test on the first node
	4. Test on the last node

**Recursive Linked List remove()**

```cpp
// not suitable for O(N), but fun to write
static ListNode * ListNode::remove(char c, ListNode * L) {
    if (L == nullptr)
        return nullptr;
    else if (L->info == c) {
        ListNode * ret = remove(c, L->next); // remove all? or first?
        delete L;
        return ret;
    }
    else {
        L->next = remove(c, L->next);
        return L;
    }
}
```

**SLL Remove Challenge**

- Given pointer `P` to node containing item `V` → remove V in O(1) time
- Others may have pointer to same node P points to
- How can you do this?
- Hint: data is not tied to the ListNode

**SLL Remove Clever Trick**

```cpp
// data is not tied to the ListNode!!!
static void remove(ListNode * P) {
    // P is pointing to node with value to remove
    ListNode * to_die = P->next;   // gonna delete next node instead
    P->info = P->next->info;       // copy data & next from P->next
    P->next = P->next->next;
    delete to_die;                 // delete the next node
}
// does not handle deleting the last element of the list
// works for insert() V before value at P too!
```

**Bubble Sort**

```cpp
void bubble_sort(int A[], int N) {
    int i, j;
    for (i = 0; i < N; ++i)
        for (j = 0; j < N - i; ++j)
            if (A[j] > A[j+1])
                swap(A[j], A[j+1]);
}
```

# Lecture 5: Stacks & Queues

**Overview**
- Containers for elements → element type is a template parameter
- Elements are inserted and removed → the difference is the order they come out
- Useful for many algorithms
	- Browser back button
	- Line of customers waiting to check out
	- Print requests
	- Matching parentheses
	- etc. (toooo many options)

**Pre-Test Self-Check**
- What is the insert/remove behavior of a queue?
	- FIFO → First-In-First-Out, elements come out in the same order they went in
- What are the standard operations on a queue?
	- `enqueue`, `dequeue`, `front`/`peek`, `is_empty`, `is_full`
- How can you implement a queue using an array (with an initial capacity) so each operation is O(1)?
	- Circular buffer with `front` and `rear` indices → enqueue at rear, dequeue from front, both O(1)
- How can you implement a queue using a singly linked list so each operation is O(1)?
	- Keep both `head` and `tail` pointers → insert at tail, pop at head
- What errors are likely with a queue?
	- `dequeue()` or `peek()` on an empty queue
	- `enqueue()` on a full queue

**Queues**
- Works like the check-out line at the grocery store → FIFO
- Applications:
	- Print queue on a computer
	- Real waiting lines → food, movie tickets, etc.
	- Communication between concurrent tasks
	- Waiting list to get into a full class

**Queue Interface**
- `type "object"` can be any type

- `void enqueue(object v)` → inserts v into rear of Queue
- `object dequeue()` → removes and returns object from front of Queue
- `object front()` or `peek()` → returns object at front of Queue without removing it
- `bool is_empty()` → true iff Queue is empty
- `bool is_full()` → true iff Queue is full
- `void error(char msg[])` → prints message, throws exception

**Queue Errors**
- `dequeue()` or `front()`/`peek()` on an empty Queue
- `enqueue()` on a full Queue
- Queue user should check before calling
- Any error should:
	- Print a specific error message
	- (maybe) throw an appropriate exception

**Queue As An Array**

Circular buffer → key to O(1) operations
- Fixed-size array with `front` and `rear` indices
- When an index walks past the end of the array → wraps back around to the start
- Advance indices via modulo → `rear = (rear + 1) % capacity`
- Example: capacity = 5, rear = 4 → after one enqueue, `rear = (4 + 1) % 5 = 0`

How to detect when the array queue is empty?
- `front == rear`

How to detect when the array queue is full?
- Problem: if we just use `front == rear`, that's ALSO true when the queue is empty → ambiguous
- Two standard fixes:
	- **Leave one slot unused** → allocate `capacity + 1` slots, queue is full when `(rear + 1) % capacity == front`. That's the reason for the `+1` in the constructor — it reserves one slot so full and empty have different signatures.
	- **Keep a size counter** → queue is full when `size == capacity`. Simpler logic but now `size`, `front`, and `rear` all have to stay in sync on every operation → more bookkeeping.

```cpp
class ArrayQueue {
    object * buf;  // base of circular array
    int capacity, front, rear;

    ArrayQueue(int maxSize)
        : capacity(maxSize + 1), front(0), rear(0),
          buf(new object[maxSize + 1])  // +1 reserves a slot to disambiguate full vs. empty
    { }
};
```

Aside → Exit & main()
- `main()` isn't called directly by the user → the runtime's hand-coded startup assembly sets up argc/argv and calls it
- `exit()` flushes and closes all open files before the process terminates

**Queue As An Array: Operations**

```cpp
void enqueue(object v) {
    if (is_full()) error("enqueue on full queue");
    buf[rear] = v;
    rear = (rear + 1) % capacity;
}

object dequeue() {
    if (is_empty()) error("dequeue on empty queue");
    object result = buf[front];
    front = (front + 1) % capacity;
    return result;
}

bool is_empty() { return front == rear; }
bool is_full()  { return (rear + 1) % capacity == front; }
```

- Pattern → check error cases first, then do the normal operation last

**Queue As Linked List**
- For O(1) operations → must keep both `head` and `tail` pointers
	- Head is the front, tail is the rear → enqueue at tail, dequeue at head
	- Add to either end in O(1)
	- Cannot remove from the tail in O(1) (singly linked → no prev pointer, would need to walk the list to find the new tail)
- When dequeuing the last element → must fix up both `head` and `tail` back to `nullptr`

```cpp
class LinkedQueue {
    LinkNode * head;
    LinkNode * tail;

    LinkedQueue() : head(nullptr), tail(nullptr) { }
    bool is_empty() { return head == nullptr; }
    bool is_full()  { return false; }  // limited only by heap

    void enqueue(object v) {
        LinkNode * node = new LinkNode(v, nullptr);
        if (is_empty()) head = tail = node;
        else {
            tail->next = node;
            tail = node;
        }
    }

    object dequeue() {
        if (is_empty()) error("dequeue on empty queue");
        LinkNode * old = head;
        object result = old->data;
        head = head->next;
        if (head == nullptr) tail = nullptr;  // queue now empty → fix tail too
        delete old;
        return result;
    }
};
```

**Queue In C++ STL**

```cpp
#include <iostream>
#include <queue>
using namespace std;
int main() {
    queue<int> Q;
    for (int i = 0; i < 5; ++i)
        Q.push(i);
    for (; !Q.empty(); Q.pop())
        cout << Q.front() << ' ';
    cout << endl;
}
```

**Pre-Test Self-Check**
- What is the insert/remove behavior of a stack?
	- LIFO → Last-In-First-Out
- What are the standard operations on a stack?
	- `push`, `pop`, `top`
- How can you implement a stack using an array (with an initial capacity) so each operation is O(1)?
	- `top` index starts at 0 (next available slot) → `buf[top++] = value` for push, `--top` for pop
	- All operations on the same end of the array → no shifting needed
	- `find` is O(N) — but find isn't a stack operation anyway
- How can you implement a stack using a singly linked list so each operation is O(1)?
	- Insert at head → `head = new ListNode(head, data)`
	- Remove from head
	- Search would still be O(N), but again not a stack op
- What errors are likely with a stack?
	- `pop()` or `top()` on an empty stack
	- `push()` on a full stack

**Guard Clauses**
- Write the happy path first → the normal-case logic
- Then add error checks above it as guards
- Keeps the main logic uncluttered and the error cases obvious at the top

**Stacks**
- Works like a stack of plates in a cafeteria → LIFO
- Applications:
	- Forward/back in a web browser
	- Balancing parentheses
	- Call stack for function parameters and return addresses
	- Evaluating arithmetic expressions
	- Holding nodes during graph traversals

**Stack Interface**
- `type "object"` can be any type

- `void push(object v)` → places v on the top
- `object pop()` → removes and returns the object from top
- `object top()` → returns object at top without removing it
- `bool is_empty()` → true iff stack is empty
- `bool is_full()` → true iff stack is full
- `void error(char msg[])` → prints msg, throws exception

**Stack Errors**
- `pop()` or `top()` on an empty stack
- `push()` on a full stack
- Stack user should check before calling
- Always write an `error` helper:
	- `void error(string msg) { cerr << "Error: " << msg << endl; }`
- Any error should:
	- Print a specific error message
	- (maybe) throw an appropriate exception, or `exit()`

**Stack As An Array**

To ensure O(1) operations → push/pop at the same end (the top index).

```cpp
class ArrayStack {
    int capacity, tp;
    object * buf;  // base of array

    ArrayStack(int maxSize)
        : capacity(maxSize), tp(0),
          buf{new object[maxSize]}
        /* Curly braces are preferred for initialization because there's
           one case where parens are ambiguous:
             int i();   → function declaration that returns an int
             int j{};   → default-initialized variable (preferred)
             int k;     → uninitialized — unknown contents
             int m(0);  → variable m initialized to 0 (works, but parens
                         are ambiguous in the i() case above)
        */
    { }
};
```

**Stack As An Array: Operations**

```cpp
void push(object v) {
    if (is_full()) error("push on full stack");
    buf[tp++] = v;
}

object pop() {
    if (is_empty()) error("pop on empty stack");
    return buf[--tp];
}

object top() {
    if (is_empty()) error("top on empty stack");
    return buf[tp - 1];
}

bool is_empty() { return tp == 0; }
bool is_full()  { return tp >= capacity; }
```

- Pattern → guard the error case first, then do the normal operation

**Stack As A Linked List**
- For O(1) operations → only need a `head` pointer
	- Push and pop both happen at the head → no need for a tail
- Never "full" → limited only by heap memory

```cpp
class LinkedStack {
    LinkNode * head;

    LinkedStack() : head(nullptr) { }
    bool is_empty() { return head == nullptr; }
    bool is_full()  { return false; }

    void push(object v) {
        head = new LinkNode(v, head);  // new node points to old head
    }

    object pop() {
        if (is_empty()) error("pop on empty stack");
        LinkNode * old = head;
        object result = old->data;
        head = head->next;
        delete old;
        return result;
    }

    object top() {
        if (is_empty()) error("top on empty stack");
        return head->data;
    }
};
```

**Stack In C++ STL**

```cpp
#include <iostream>
#include <stack>
using namespace std;
int main() {
    stack<int> S;
    for (int i = 0; i < 5; ++i)
        S.push(i);
    for (; !S.empty(); S.pop())
        cout << S.top() << ' ';
    cout << endl;
}
```

**Classic Use of Stack: Balanced Parentheses**

Check whether `(`, `[`, `{` are properly matched and nested → push openers, pop and compare on closers.

```cpp
#include <stack>
#include <string>
using namespace std;

bool balanced(const string& s) {
    stack<char> S;
    for (char c : s) {
        if (c == '(' || c == '[' || c == '{') {
            S.push(c);
        } else if (c == ')' || c == ']' || c == '}') {
            if (S.empty()) return false;          // closer with no opener
            char open = S.top(); S.pop();
            if ((c == ')' && open != '(') ||
                (c == ']' && open != '[') ||
                (c == '}' && open != '{'))
                return false;                     // mismatched pair
        }
    }
    return S.empty();                             // leftover openers → unbalanced
}
```


# Lecture 6: Hashing & Hash Tables

**Hashing & Hash Tables Overview**
- Hash function has to be O(1) to compute → really hard without collisions
- Settle for some collisions (different keys hashing to the same index) in exchange for O(1) average search

**Table (a.k.a. Map, Dictionary)**
- In Python, lookup by value is O(N)
- Tables connect a value with some key
- Value can be anything → e.g., address and phone number
- Key is used to find the information → e.g., person's last name, first name
- Table implementation options:
	- **Search List** → linked list where find is O(N) and insert is O(1) → bad since find is the most common operation
	- **Hash Table** → in a perfect environment, find/insert/remove are all O(1), but no guarantees
		- Can degenerate → need to know what causes that and how to fix it
	- **Binary Search Tree** → O(log N) for all operations on average
		- Worst case is O(N) when the tree degenerates into a singly linked list (inserts in sorted order, no self-balancing) → balanced BSTs (AVL, Red-Black) guarantee O(log N)
- Operations: insert, find, remove

**Hash Table Structure**
- Contains an array of slots (each with key/value)
- A hash function computes the index for each key → spreads keys across the array
- For complexity → may divide N by the array size (capacity)

**Hash Functions**
- A good hash function:
	- Spreads keys across the array to minimize collisions
	- Covers the entire index range of the table
	- Must be O(1) and cheap to compute
- What is a good distribution? → [NIST handbook](https://www.itl.nist.gov/div898/handbook/eda/section3/eda366.htm)
	- Normal? Poisson? Uniform?
		- Don't want normal → values pile up in the middle → many collisions
		- **Uniform is ideal** → every slot has equal probability → collisions are minimized for a given load factor

**Collision Resolution Policy**
1. Linear probing → move to the next viable slot
	- When too many keys cluster together → degeneration (primary clustering)

**Activities**
- Activity 1 → hash signed integers
	- `int hash(int key, int N) { return 0; }`
	- Takes in a key and the table size N
	- Return value must be in [0, N-1] inclusive
	- Must ensure positive and in range
	- Bitwise operations: `&`, `|`, `~` (negation) → not logical operators
- Activity 2 → hash strings
	- `int hash(string key, int N) { return 0; }`

**Hash Functions for Strings — Poor Choices**
- Summing all ASCII codes
	- Leads to a normal distribution
	- May not cover the entire table range if the table is large
- Multiplying ASCII codes together
	- Common factors cause collisions → mostly even values
- Neither is sensitive to character order → `"abc"` and `"cba"` give the same result

**Hash Function 1 — Shift-and-OR**
```cpp
int hash(string key, int N) {
	const unsigned shift = 6;
	const unsigned zero = 0;
	unsigned mask = ~zero >> (32 - shift);   // low 6 bits on
	unsigned result = 0;
	int len = key.size();
	for (int i = 0; i < len; i++)
		result = (result << shift) | (key[i] & mask);
	return result % N;
}
```
- Unsigned int gives the full 2³² range (~4 billion) all positive
- **Why only the low 6 bits of each char?** → For alphanumeric ASCII (`'0'`–`'9'`, `'A'`–`'Z'`, `'a'`–`'z'`), the upper bits barely vary; the distinguishing information lives in the low 6 bits
	- ASCII is a 7-bit encoding → bit 7 is always 0 for standard ASCII (historically the 8th bit was used for parity / error checking)
- **URL problem — which letters dominate the hash?**
	- Each iteration shifts `result` left by 6 bits. After ~5–6 characters, the bits from earlier characters get shifted out of the 32-bit word
	- → The **last ~5 characters** of the string dominate the final hash value
	- For URLs, the last characters are usually `.com` / `.org` / `.edu` → all URLs collide because their tails are nearly identical
	- (Earlier guess of "the `.com` and all that" was right *as the cause*, but it's the **last** chars that dominate, not the first)

**Hash Function 2 — First-6 Cap (broken fix)**
```cpp
int hash(string key, int N) {
	const unsigned shift = 6;
	const unsigned zero = 0;
	unsigned mask = ~zero >> (32 - shift);   // low 6 bits on
	unsigned result = 0;
	int len = min(key.size(), 6);   // cap to first 6 chars
	for (int i = 0; i < len; i++)
		result = (result << shift) | (key[i] & mask);
	return result % N;
}
```
- Caps the loop at 6 chars so earlier chars stay in the result
- **Doesn't fix URLs** → most URLs start with `https:` or `www.` → first 6 are again nearly identical → same collision problem on the other end

**Fix for URLs — take the middle 6 characters**
```cpp
int hash(string key, int N) {
	const unsigned shift = 6;
	const unsigned zero = 0;
	unsigned mask = ~zero >> (32 - shift);   // low 6 bits on
	unsigned result = 0;
	int len = key.size();
	int start = (len > 6) ? (len - 6) / 2 : 0;   // center a 6-char window
	int end   = (len > 6) ? start + 6        : len;
	for (int i = start; i < end; i++)
		result = (result << shift) | (key[i] & mask);
	return result % N;
}
```
- Skips both the common prefix (`https://www.`) and the common suffix (`.com`) → samples the part of the URL that actually varies (the domain name itself)

**Learning C++ Bitwise Operations**
- `print_binary()` prints an unsigned int in binary → call after each iteration in the hash function to watch the hash value build up

```cpp
#include <iostream>
#include <limits>
#include <bitset>

void print_binary(unsigned value) {
    constexpr unsigned numBits = std::numeric_limits<unsigned>::digits;
    std::bitset<numBits> binary(value);
    std::cout << binary << std::endl;
}
```

**Dealing with Collisions**
- **Open addressing**
	- Key/value pairs stored directly in array slots
	- Collisions / clustering → require probing
	- Deletions → mark as deleted (tombstone) so probes can still walk past to find later keys
- **Separate chaining** → [visualization](https://www.cs.usfca.edu/~galles/visualization/OpenHash.html)
	- Each array slot is a SearchList (linked list)
	- Avoids clustering
	- Never gets 'full'
	- Deletions are easy → linked list removal
		- (Open addressing deletions are hard because removing a slot would break probe chains for other keys)
	- Can still degenerate → if all keys hash to one slot, the chain becomes a long linked list

- **Primary clustering** → clustering near the original hash value
- **Rehashing** → create a larger table and rehash all entries

**Probing After Collision**
- **Linear probing** → [interactive viz](http://iswsa.acm.org/mphf/openDSAPerfectHashAnimation/perfectHashAV.html)
	- `hash(k, i, N) = (hash1(k) + i) mod N`
	- Increment hash value by a constant (1) until an open slot is found
	- Simplest to implement
	- Leads to **primary clustering**
- **Quadratic probing**
	- `hash(k, i, N) = (hash1(k) + c1·i + c2·i²) mod N`
	- Leads to **secondary clustering**
- **Double hashing**
	- `hash(k, i, N) = (hash1(k) + i·hash2(k)) mod N`
	- Avoids clustering

**Table Size Issues**
- **Load Factor** = N (# elements) / M (# slots) → measure of how full the table is → 0.75 is high
- Table size is usually **prime** to avoid bias from modulo
- Too large → wasted space
- Too small → more collisions
- What happens to a chained hash table as table size → 1? → degenerates into a single singly linked list
- Record the **max and min chain length** when measuring chained hashing
- Up to ~20 items, linear search is fine
- → If chains can hold ~10 each, 10,000 entries only need ~1,000 slots

**Time Complexity (Hash Table)**
- `insert()` → compute hash O(1), push O(1) → **O(1) average**
- `find()` → compute hash O(1), then O(length of chain)
- `remove()` → compute hash O(1), then O(length of chain)

**C++ Hashing — STL**
- STL provides hash functions → [cppreference](https://en.cppreference.com/w/cpp/utility/hash)
- STL provides [unordered associative containers](https://en.wikipedia.org/wiki/Unordered_associative_containers_\(C%2B%2B\))

```cpp
#include <unordered_map>
int main() {
    unordered_map<string, int> months;
    months["february"]  = 28;
    months["april"]     = 30;
    months["september"] = 30;
    months["december"]  = 31;
    cout << "september -> " << months["september"] << endl;
    cout << "april     -> " << months["april"]     << endl;
    cout << "december  -> " << months["december"]  << endl;
    cout << "february  -> " << months["february"]  << endl;
}
```

**STL Example: unordered_map of Months**

```cpp
#include <iostream>
#include <string>
#include <unordered_map>
int main() {
    std::unordered_map<std::string, int> months{
        {"january", 31}, {"february", 28}, {"march", 31},
        {"april", 30},   {"may", 31},      {"june", 30},
        {"july", 31},    {"august", 31},   {"september", 30},
        {"october", 31}, {"november", 30}, {"december", 31}};
    for (auto [month, days] : months)
        std::cout << month << " " << days << std::endl;
}
// In the structured binding `auto [month, days] : months`,
// month → pair::first, days → pair::second
```

- Sample output (Klefstad's run):
	- december 31, november 30, july 31, may 31, october 31, august 31, april 30, september 30, june 30, february 28, march 31, january 31
- Order looks scrambled → that's because it's an `unordered_map` (hash table) → no ordering guarantees
- Want it ordered? → use `std::map` (red-black tree) → keys come out in sorted order
- This data structure is essentially an **array that you can index with strings** → an *associative array*
- Both BSTs and hash tables give good performance for this

**Aside: lvalue vs rvalue**

- Named after the **left** and **right** sides of an assignment statement
- **lvalue** → the memory cell being assigned to (has an address)
- **rvalue** → the value being assigned from (a temporary/expression)

**Other Asides**

- The words in the homework word list come from a Linux dictionary file (e.g., `/usr/share/dict/words`) → words used by spell checkers
- **Why only the low 6 bits per char in the hash function?** → For printable ASCII (especially alphanumerics), the upper bits barely change across characters
	- ASCII is a 7-bit encoding → bit 7 is always 0 for standard ASCII
	- The high bits within the 7 (bits 5–6) only flip between digit/letter/case ranges, not character-to-character
	- The actual *distinguishing* information lives in the low bits → e.g., `'a'` (0x61) and `'b'` (0x62) differ only in the low bits
	- → Discarding the upper bits loses almost no entropy and packs more characters into each 32-bit word
- **45,392** → the number of word entries in the homework word set

**Homework 5: Hash Table Trade-offs**

What efficiency trade-offs are we exploring?

- **Collision resolution policy?** → could be linear probing, quadratic probing, double hashing, or chaining
	- We're using **chained hash tables** in this class → already decided, not a variable
- **Hash function distribution?** → yes, interesting → measure several different hash functions
	- A poor hash function (sum of ASCII, multiply, etc.) clusters keys into a few slots → long chains, slow finds
	- A good hash function (uniform distribution) spreads keys evenly → short, balanced chains → near-O(1) finds
	- We measure this by holding table size constant and swapping in different `Hasher` implementations
- **Table size effect?** → yes, interesting → measure several table sizes for the same hash function
	- The **load factor** N/M drives chain length → smaller table → longer chains → slower find/remove
	- Larger table → shorter chains but more wasted memory
	- A prime table size avoids modulo-induced bias for non-uniform hashes
- **How do we compare?** → collect statistics so comparisons are meaningful
	- Chain length: mean, stddev, min, max, number of empty chains
	- Operation timings: insert-all (I), find-all (F), remove-all (R)

**Designing a Pluggable Hashing Framework**

- Sketch the hash table class
- Sketch a `Hasher` class hierarchy → abstract base + many concrete subclasses → swap in/out via polymorphism
- Sketch the chain implementation with reusable static helpers

**Pluggable Hasher Framework**

```cpp
struct Hasher {
    virtual size_t hash(string key, size_t N) = 0;
    // = 0 → pure virtual function
    // A class with ≥ 1 pure virtual is an abstract class (cannot instantiate)
    // A "concrete" class implements every pure virtual it inherits
};

// Provide 10+ concrete hashers for comparison...

struct SumHasher : public Hasher {  // public inheritance → "is-a" Hasher
    size_t hash(string key, size_t N) override {
        // `override` is a keyword (not a reserved word) → identifies intent to
        // override a base virtual. Compiler errors if no matching virtual exists.
        // → NOT strictly necessary (the override happens regardless), but it's a
        // safety net: catches typos in the signature that would silently create
        // a brand-new function instead of overriding.
        size_t ret = 0;
        for (auto c : key)
            ret += c;
        return ret % N;
    }
};
```

**HashTable Class**

```cpp
class HashTable {
    size_t size;
    ListNode ** T;            // array of linked-list heads
    const Hasher & hasher;    // const reference → must be initialized in the
                              // member-initializer list (refs cannot be reseated)
public:
    HashTable(const Hasher & h, size_t cap);
    void insert(string key);
    bool find(string key);
    void remove(string key);
    Stats get_statistics();
};
// Compare: STL's unordered_map<KType, VType> stores key/value pairs
```

**ListNode and Static Helpers**

```cpp
struct ListNode {
    string data;             // could be std::pair<KType, VType>
    ListNode * next;
    static ListNode * insert(string key, ListNode * L);
    static ListNode * find(string key, ListNode * L);
    static ListNode * remove(string key, ListNode * L);
    static void delete_list(ListNode * L);
};
// Same pattern as our unordered linked list helpers from earlier
```

**Measured Results: STLHasher at Varying Table Sizes**

All runs use 45,392 dictionary entries with the STL hash function. I = insert-all time, F = find-all time, R = remove-all time (seconds).

| Chains (M) | Load N/M | Min chain | Max chain | I (s) | F (s) | R (s) |
| --- | --- | --- | --- | --- | --- | --- |
| 1000 | 45.4 | 21 | 64 | 0.0350 | 0.1012 | 0.1121 |
| 100 | 453.9 | 399 | 520 | 0.0342 | 0.6295 | 0.6913 |
| 10 | 4539.2 | 4469 | 4668 | 0.0340 | 5.4639 | 6.2930 |
| 1 | 45392 | 45392 | 45392 | 0.0339 | 49.38 | 60.93 |

- **Insert times are flat** → chained insert is O(1) per insert regardless of chain length (we prepend at head) → table size doesn't affect it
- **Find/remove scale with chain length** → both must walk the chain → degrade linearly as M shrinks
- At M = 1, the hash table degenerates into a single linked list → find-all is O(N²), confirming the ~50s vs ~0.1s blow-up
- **Why does the gap between min and max chain shrink as M increases?** → with a good hash function, chain lengths follow roughly a Poisson distribution
	- Larger M → smaller load factor → expected chain length is small → absolute spread (max − min) is small
	- Smaller M → bigger expected chain length → same *relative* variance produces a much larger absolute spread
	- A *bad* hash function would show big min/max gaps even at large M because keys cluster into a few slots while others stay empty

**Coding the Hash Table**

```cpp
class HashTable {
    size_t size;
    ListNode ** T;
    const Hasher & hasher;   // size_t hash(string key, size_t N)
};
```

Activities:
- Write the constructor → `HashTable(const Hasher & h, size_t cap)`
- Write `void HashTable::insert(string key);`
- Write `bool HashTable::find(string key);`
- Write `void HashTable::remove(string key);`

```cpp
void HashTable::insert(string key) {
    size_t h = hasher.hash(key, size);
    T[h] = ListNode::insert(key, T[h]);
}
```

**Perfect Hashing**

- When the set of keys is **known beforehand** (e.g., the reserved words of C++)
- We can construct a function that guarantees **no collisions** → a *Perfect Hash Function* → [wiki](https://en.wikipedia.org/wiki/Perfect_hash_function)
- May require **more than N slots** in the table
- A *Minimal Perfect Hash Function* uses **exactly N slots** → [wiki](https://en.wikipedia.org/wiki/Perfect_hash_function#Minimal_perfect_hash_function)
- Not appropriate for a general-purpose hash table → only works when the key set is fixed and known up front

<!-- last cleaned: end of Lecture 6 (Perfect Hashing) -->
