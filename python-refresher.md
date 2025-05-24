## OOP
```python
class MyClass:
	
    def __init__(self, value):
        self.value = value
    
    def __str__(self):
        # User-friendly representation
        return f"Value: {self.value}"
    
    def __eq__(self, other):
        if not isinstance(other, self.__class__):
            return NotImplemented
        return self.value == other.value

    
    def __hash__(self):
        # If __eq__ is defined, __hash__ should be too
        return hash(self.value)
    
    def __bool__(self):
        # Define truthiness
        return bool(self.value)

# Always implement __repr__ 
# Implement __str__ only if you need user-friendly output
# If you implement __eq__, also implement __hash__
# Use NotImplemented for comparison methods when types don't match
```
## Data Structures

### Lists

```python
# Creation
arr = []
arr = [1, 2, 3]
arr = list(range(10))  # [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

# Operations
arr.append(4)          # Add to end: [1, 2, 3, 4]
arr.insert(1, 5)       # Insert at index: [1, 5, 2, 3, 4]
arr.pop()              # Remove & return last item
arr.pop(1)             # Remove & return item at index 1
arr.remove(3)          # Remove first occurrence of value
del arr[1]             # Delete item at index
arr.index(2)           # Find index of first occurrence
arr.count(2)           # Count occurrences of value
arr.extend([5, 6])     # Concatenate lists
arr.sort()             # Sort in-place
arr.sort(reverse=True) # Sort descending
sorted_arr = sorted(arr)  # Return sorted copy
arr.reverse()          # Reverse in-place

# Slicing
arr[2:5]               # Items from index 2 to 4
arr[:3]                # Items from start to index 2
arr[2:]                # Items from index 2 to end
arr[-2:]               # Last two items
arr[::2]               # Every second item
arr[::-1]              # Reversed list

# List comprehensions
squares = [x**2 for x in range(10)]
even_squares = [x**2 for x in range(10) if x % 2 == 0]
```

### Dictionaries

```python
# Creation
d = {}
d = {"a": 1, "b": 2}
d = dict(a=1, b=2)
d = {k: v for k, v in [("a", 1), ("b", 2)]}  # Dict comprehension

# Operations
d["c"] = 3             # Add or update
value = d["a"]         # Access (raises KeyError if not found)
value = d.get("z", 0)  # Access with default (0) if not found
d.pop("b")             # Remove & return value
del d["a"]             # Delete key
"a" in d               # Check if key exists
d.keys()               # View of keys
d.values()             # View of values
d.items()              # View of (key, value) pairs
d.update({"x": 10})    # Merge dictionaries

# Dictionary comprehension
letter_count = {char: s.count(char) for char in set(s)}
```

### Sets

```python
# Creation
s = set()
s = {1, 2, 3}
s = set([1, 2, 2, 3])  # From list, duplicates removed

# Operations
s.add(4)               # Add element
s.remove(2)            # Remove element (raises KeyError if not found)
s.discard(2)           # Remove if present (no error if not found)
s.pop()                # Remove and return arbitrary element
2 in s                 # Check membership
s1.union(s2)           # s1 | s2: Elements in either set
s1.intersection(s2)    # s1 & s2: Elements in both sets
s1.difference(s2)      # s1 - s2: Elements in s1 but not in s2
s1.symmetric_difference(s2)  # s1 ^ s2: Elements in either but not both

# Set comprehension
vowels = {char for char in "hello" if char in "aeiou"}
```

### Tuples

```python
# Creation
t = ()
t = (1,)               # Single element (note the comma)
t = (1, 2, 3)
t = tuple([1, 2, 3])   # From list

# Operations
value = t[0]           # Access (immutable, can't modify elements)
len(t)                 # Length
2 in t                 # Check membership
t1 + t2                # Concatenation
t * 3                  # Repetition

# Tuple unpacking
a, b, c = (1, 2, 3)    # Unpack tuple to variables
```

### Heaps (Priority Queues)

```python
import heapq

# Min heap operations
nums = [3, 1, 4, 1, 5, 9]
heapq.heapify(nums)              # Convert list to heap in-place
heapq.heappush(nums, 2)          # Push item onto heap
smallest = heapq.heappop(nums)   # Pop and return smallest item
smallest = nums[0]               # Peek at smallest item

# For max heap, negate values
nums = [3, 1, 4, 1, 5, 9]
nums = [-n for n in nums]        # Negate all values
heapq.heapify(nums)              # Heapify
heapq.heappush(nums, -2)         # Push negative value
largest = -heapq.heappop(nums)   # Pop and negate to get max
```

### Collections Module

```python
from collections import defaultdict, Counter, deque, OrderedDict

# defaultdict - dict with default values
dd = defaultdict(int)    # Default value 0 for new keys
dd = defaultdict(list)   # Default value [] for new keys
dd = defaultdict(lambda: "unknown")  # Custom default

# Counter - count occurrences
counter = Counter("hello world")  
counter.most_common(2)   # Two most common elements
counter["e"] += 1         # Increment count

# deque - double-ended queue
queue = deque([1, 2, 3])
queue.append(4)          # Add to right: [1, 2, 3, 4]
queue.appendleft(0)      # Add to left: [0, 1, 2, 3, 4]
queue.pop()              # Remove from right: [0, 1, 2, 3]
queue.popleft()          # Remove from left: [1, 2, 3]
queue.rotate(1)          # Rotate right: [3, 1, 2]
queue.rotate(-1)         # Rotate left: [1, 2, 3]

# OrderedDict - remembers insertion order (less needed in Python 3.7+ as regular dicts maintain order)
od = OrderedDict()
od["a"] = 1
od["b"] = 2
od.move_to_end("a")      # Move key to end
od.popitem(last=False)   # Remove first item (FIFO)
```

## Algorithms

### Sorting

```python
# Built-in sort
arr.sort()                # In-place sort
arr.sort(reverse=True)    # Descending
arr.sort(key=lambda x: x[1])  # Sort by custom key

# Custom sort for objects
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

people = [Person("Alice", 30), Person("Bob", 25)]
people.sort(key=lambda p: p.age)  # Sort by age

# Sort stable in Python (maintains relative order of equal elements)
# Time complexity: O(n log n)
```

### Binary Search

```python
def binary_search(arr, target):
    left, right = 0, len(arr) - 1
    
    while left <= right:
        mid = left + (right - left) // 2  # Avoid integer overflow
        if arr[mid] == target:
            return mid
        elif arr[mid] < target:
            left = mid + 1
        else:
            right = mid - 1
            
    return -1  # Not found

# Bisect module (binary search in sorted lists)
import bisect
bisect.bisect_left(arr, x)   # Index to insert x (leftmost)
bisect.bisect_right(arr, x)  # Index to insert x (rightmost)
bisect.insort_left(arr, x)   # Insert x maintaining order (left)
```

### Graph Traversal

#### Depth-First Search (DFS)

```python
# DFS for a graph represented as adjacency list
def dfs(graph, start, visited=None):
    if visited is None:
        visited = set()
    
    visited.add(start)
    print(start)  # Process node
    
    for neighbor in graph[start]:
        if neighbor not in visited:
            dfs(graph, neighbor, visited)
            
# Iterative DFS using stack
def dfs_iterative(graph, start):
    visited = set()
    stack = [start]
    
    while stack:
        node = stack.pop()
        if node not in visited:
            visited.add(node)
            print(node)  # Process node
            
            # Add neighbors to stack (in reverse order to match recursive DFS)
            for neighbor in reversed(graph[node]):
                if neighbor not in visited:
                    stack.append(neighbor)
```

#### Breadth-First Search (BFS)

```python
from collections import deque

def bfs(graph, start):
    visited = set([start])
    queue = deque([start])
    
    while queue:
        node = queue.popleft()
        print(node)  # Process node
        
        for neighbor in graph[node]:
            if neighbor not in visited:
                visited.add(neighbor)
                queue.append(neighbor)
```

### Dynamic Programming

```python
# 1. Fibonacci with memoization
def fib(n, memo={}):
    if n in memo:
        return memo[n]
    if n <= 1:
        return n
    memo[n] = fib(n-1, memo) + fib(n-2, memo)
    return memo[n]

# 2. Bottom-up approach
def fib_bottom_up(n):
    if n <= 1:
        return n
    
    dp = [0] * (n + 1)
    dp[1] = 1
    
    for i in range(2, n + 1):
        dp[i] = dp[i-1] + dp[i-2]
    
    return dp[n]

# 3. Space-optimized
def fib_optimized(n):
    if n <= 1:
        return n
    
    a, b = 0, 1
    for _ in range(2, n + 1):
        a, b = b, a + b
    
    return b
```

## Common Patterns

### Two Pointers

```python
# Find pair with given sum in sorted array
def two_sum_sorted(arr, target):
    left, right = 0, len(arr) - 1
    
    while left < right:
        current_sum = arr[left] + arr[right]
        if current_sum == target:
            return [left, right]
        elif current_sum < target:
            left += 1
        else:
            right -= 1
            
    return [-1, -1]  # No solution found
```

### Sliding Window

```python
# Find max sum subarray of size k
def max_sum_subarray(arr, k):
    if len(arr) < k:
        return None
    
    # Initial window sum
    window_sum = sum(arr[:k])
    max_sum = window_sum
    
    # Slide window and track max
    for i in range(len(arr) - k):
        window_sum = window_sum - arr[i] + arr[i + k]
        max_sum = max(max_sum, window_sum)
        
    return max_sum
```

### Fast and Slow Pointers

```python
# Detect cycle in linked list
def has_cycle(head):
    if not head or not head.next:
        return False
    
    slow = head
    fast = head
    
    while fast and fast.next:
        slow = slow.next
        fast = fast.next.next
        
        if slow == fast:
            return True
            
    return False
```

### Backtracking

```python
# Generate all subsets
def subsets(nums):
    result = []
    
    def backtrack(start, current):
        result.append(current[:])  # Add copy of current subset
        
        for i in range(start, len(nums)):
            current.append(nums[i])
            backtrack(i + 1, current)
            current.pop()  # Backtrack
    
    backtrack(0, [])
    return result
```


## Python Tricks

### One-liners

```python
# List flattening
flat_list = [item for sublist in nested_list for item in sublist]

# Filter even numbers
even_numbers = list(filter(lambda x: x % 2 == 0, numbers))

# Check if all elements satisfy condition
all_positive = all(x > 0 for x in numbers)

# Check if any element satisfies condition
has_negative = any(x < 0 for x in numbers)

# Get max/min with custom key
longest_string = max(strings, key=len)

# Swap values without temp variable
a, b = b, a

# Ternary operator
result = "Even" if num % 2 == 0 else "Odd"
```

### String Operations

```python
# String joining
words = ["Hello", "world"]
sentence = " ".join(words)  # "Hello world"

# String splitting
words = "Hello,world".split(",")  # ["Hello", "world"]

# Check if string starts/ends with
s.startswith("Hello")
s.endswith(".py")

# String formatting
f"Name: {name}, Age: {age}"  # f-strings (Python 3.6+)
"Name: {}, Age: {}".format(name, age)
"Name: %s, Age: %d" % (name, age)  # Old style
```

### Lambda Functions

```python
# Sort by custom key
sorted(students, key=lambda s: s.gpa)

# Map values
list(map(lambda x: x**2, numbers))

# Combine/chain functions
from functools import reduce
reduce(lambda x, y: x + y, numbers)  # Sum of all elements
```

### Generator Expressions

```python
# More memory efficient than list comprehensions
sum_of_squares = sum(x**2 for x in range(1000000))

# Lazy evaluation
first_ten = list(itertools.islice((x for x in infinite_generator()), 10))
```

### File Operations

```python
# Reading file
with open("file.txt", "r") as f:
    content = f.read()  # Read entire file
    lines = content.splitlines()  # Split into lines
    
# Alternative line reading
with open("file.txt", "r") as f:
    for line in f:  # Memory efficient
        process(line.strip())
        
# Writing file
with open("output.txt", "w") as f:
    f.write("Hello\n")
    f.writelines(["Line 1\n", "Line 2\n"])
```

## Libraries

### copy
```python 
import copy

# Shallow copy gotcha
original = [[1, 2, 3], [4, 5, 6]]
shallow = copy.copy(original)
shallow[0][0] = 999

print(original)  # [[999, 2, 3], [4, 5, 6]] - original affected!
print(shallow)   # [[999, 2, 3], [4, 5, 6]]

# Deep copy solution
original = [[1, 2, 3], [4, 5, 6]]
deep = copy.deepcopy(original)
deep[0][0] = 999

print(original)  # [[1, 2, 3], [4, 5, 6]] - original unchanged
print(deep)      # [[999, 2, 3], [4, 5, 6]]
```
### itertools

```python
import itertools

# Combinations
itertools.combinations([1, 2, 3], 2)  # (1,2), (1,3), (2,3)

# Permutations
itertools.permutations([1, 2, 3], 2)  # (1,2), (1,3), (2,1), (2,3), (3,1), (3,2)

# Cartesian product
itertools.product([1, 2], [3, 4])  # (1,3), (1,4), (2,3), (2,4)

# Infinite counter
for i in itertools.count(start=10, step=2):
    if i > 20:
        break
    print(i)  # 10, 12, 14, 16, 18, 20
```

### functools

```python
import functools

# Caching function results
@functools.lru_cache(maxsize=None)
def fibonacci(n):
    if n <= 1:
        return n
    return fibonacci(n-1) + fibonacci(n-2)

# Reduce function
functools.reduce(lambda x, y: x + y, [1, 2, 3, 4])  # 10

# Partial functions
from functools import partial
base_two = partial(int, base=2)
base_two('10010')  # 18
```

### math and random

```python
import math
import random

# Common math operations
math.gcd(12, 15)  # 3
math.lcm(12, 15)  # 60 (Python 3.9+)
math.factorial(5)  # 120
math.sqrt(16)  # 4.0
math.ceil(4.2)  # 5
math.floor(4.8)  # 4

# Random operations
random.randint(1, 10)  # Random int between 1 and 10
random.choice([1, 2, 3, 4])  # Random element
random.shuffle(arr)  # Shuffle in-place
random.sample(range(100), 10)  # 10 unique random numbers from 0-99
```

## Debugging

### Print debugging

```python
print(f"Variable x: {x}")
print(f"Type of x: {type(x)}")
print(f"Length: {len(x)}")
```

### Assert statements

```python
assert condition, "Error message if condition is False"
```

### Timing code execution

```python
import time

start = time.time()
# Code to time
end = time.time()
print(f"Execution time: {end - start} seconds")
```

## Common Mistakes

1. Forgetting edge cases (empty input, single element, negative numbers)
2. Off-by-one errors in array indices
3. Not checking for `None` or empty collections
4. Modifying a collection while iterating through it
5. Using mutable default arguments (e.g., `def func(arr=[])`)
6. Recursion without base case (stack overflow)
7. Inefficient algorithms (e.g., O(n²) when O(n) is possible)
8. Not handling exceptions properly
9. Indentation
10. Using `is` for identity checks, not '\=='
## References
- [dunder methods](https://www.pythonmorsels.com/every-dunder-method/)
- 