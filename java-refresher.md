Basic program syntax:
```java
public class Main {
	public static void main(String[] args) {
		System.out.println("Hello world!");
	}
}
```
- Default string args
- Spring, dependency injection
## OOP

## Data structures

### Arrays

```java
// Creation
int[] arr = new int[5];
int[] arr = {1, 2, 3, 4, 5};
int[][] matrix = new int[3][4]; // 3 rows, 4 columns

// Operations
arr[0] = 10;               // Modify element
int value = arr[0];        // Access element
int length = arr.length;   // Get length

// Utility methods
import java.util.Arrays;
Arrays.sort(arr);                  // Sort in-place
Arrays.sort(arr, 1, 4);            // Sort range [1,4)
Arrays.sort(arr, Collections.reverseOrder()); // Descending (for Integer[] only)
int index = Arrays.binarySearch(arr, 3);  // Binary search (array must be sorted)
int[] copy = Arrays.copyOf(arr, arr.length);  // Create copy
int[] copy = Arrays.copyOfRange(arr, 1, 4);   // Copy range [1,4)
Arrays.fill(arr, 0);               // Fill entire array with value
Arrays.equals(arr1, arr2);         // Check equality
String s = Arrays.toString(arr);   // Convert to string representation

// Convert array to list
List<Integer> list = Arrays.asList(1, 2, 3);  // Fixed-size list
List<Integer> list = new ArrayList<>(Arrays.asList(1, 2, 3));  // Resizable list

// Java 8 streams with arrays
int sum = Arrays.stream(arr).sum();
int max = Arrays.stream(arr).max().getAsInt();
double avg = Arrays.stream(arr).average().getAsDouble();
```

### ArrayList

```java
// Creation
List<Integer> list = new ArrayList<>();
List<String> list = new ArrayList<>(Arrays.asList("a", "b", "c"));
List<Integer> list = new ArrayList<>(initialCapacity);

// Operations
list.add(4);                // Add to end
list.add(0, 5);             // Insert at index
list.set(1, 10);            // Replace at index
int value = list.get(0);    // Access element
list.remove(0);             // Remove by index
list.remove(Integer.valueOf(5)); // Remove by value
boolean exists = list.contains(3);  // Check existence
int size = list.size();     // Size
boolean isEmpty = list.isEmpty();  // Check if empty
list.clear();               // Remove all elements
int index = list.indexOf(5);  // First occurrence index (-1 if not found)
int lastIndex = list.lastIndexOf(5);  // Last occurrence index

// Iteration
for (Integer num : list) {
    // Process num
}

// Java 8 forEach
list.forEach(num -> System.out.println(num));

// Sorting
Collections.sort(list);  // Sort in ascending order
Collections.sort(list, Collections.reverseOrder());  // Sort in descending order
list.sort(Comparator.naturalOrder());  // Java 8 sort
list.sort(Comparator.reverseOrder());  // Java 8 reverse sort
list.sort(Comparator.comparing(String::length));  // Sort by custom key

// Sublist
List<Integer> subList = list.subList(1, 4);  // from index 1 to 3

// Convert to array
Integer[] array = list.toArray(new Integer[0]);
```

### LinkedList

```java
// Creation (implements List and Deque)
LinkedList<Integer> list = new LinkedList<>();
LinkedList<Integer> list = new LinkedList<>(Arrays.asList(1, 2, 3));

// List operations (same as ArrayList)
list.add(4);
list.add(0, 5);
list.remove(0);
int value = list.get(0);

// Queue/Deque operations
list.addFirst(0);       // Add to front
list.addLast(5);        // Add to end (same as add())
int first = list.getFirst();  // Get head without removing
int last = list.getLast();    // Get tail without removing
list.removeFirst();     // Remove and return head
list.removeLast();      // Remove and return tail
list.peek();            // Get head without removing
list.poll();            // Remove and return head
list.offer(6);          // Add to end (returns true)
```

### HashMap

```java
// Creation
Map<String, Integer> map = new HashMap<>();
Map<String, Integer> map = new HashMap<>(initialCapacity, loadFactor);
Map<String, Integer> map = new HashMap<>(Map.of("a", 1, "b", 2));  // Java 9+

// Operations
map.put("a", 1);            // Add or update
map.putIfAbsent("a", 2);    // Add if key doesn't exist
int value = map.get("a");   // Get value (null if not found)
int value = map.getOrDefault("z", 0);  // Get with default
map.remove("a");            // Remove entry
boolean exists = map.containsKey("a");  // Check key existence
boolean hasValue = map.containsValue(1);  // Check value existence
int size = map.size();      // Number of entries
boolean isEmpty = map.isEmpty();  // Check if empty
map.clear();                // Remove all entries

// Iteration
for (Map.Entry<String, Integer> entry : map.entrySet()) {
    String key = entry.getKey();
    int value = entry.getValue();
}

// Java 8 forEach
map.forEach((key, value) -> System.out.println(key + " -> " + value));

// Views
Set<String> keys = map.keySet();       // View of keys
Collection<Integer> values = map.values();  // View of values
Set<Map.Entry<String, Integer>> entries = map.entrySet();  // View of entries

// Java 8 computations
map.compute("a", (key, oldValue) -> (oldValue == null) ? 1 : oldValue + 1);  // Update or insert
map.computeIfAbsent("b", key -> key.length());  // Compute value if key not present
map.computeIfPresent("a", (key, oldValue) -> oldValue + 1);  // Update if key present
map.merge("a", 1, (oldValue, value) -> oldValue + value);  // Merge values
```

### HashSet

```java
// Creation
Set<Integer> set = new HashSet<>();
Set<Integer> set = new HashSet<>(Arrays.asList(1, 2, 3));
Set<String> set = new HashSet<>(Set.of("a", "b", "c"));  // Java 9+

// Operations
set.add(4);              // Add element (returns true if added)
set.remove(2);           // Remove element
boolean exists = set.contains(3);  // Check existence
int size = set.size();   // Number of elements
boolean isEmpty = set.isEmpty();  // Check if empty
set.clear();             // Remove all elements

// Iteration
for (Integer num : set) {
    // Process num
}

// Java 8 forEach
set.forEach(num -> System.out.println(num));

// Set operations
Set<Integer> set1 = new HashSet<>(Arrays.asList(1, 2, 3));
Set<Integer> set2 = new HashSet<>(Arrays.asList(2, 3, 4));

// Union
Set<Integer> union = new HashSet<>(set1);
union.addAll(set2);  // Contains 1, 2, 3, 4

// Intersection
Set<Integer> intersection = new HashSet<>(set1);
intersection.retainAll(set2);  // Contains 2, 3

// Difference
Set<Integer> difference = new HashSet<>(set1);
difference.removeAll(set2);  // Contains 1

// Convert to array
Integer[] array = set.toArray(new Integer[0]);
```

### TreeMap & TreeSet (Sorted)

```java
// TreeMap - sorted by keys
TreeMap<String, Integer> treeMap = new TreeMap<>();  // Natural order
TreeMap<String, Integer> treeMap = new TreeMap<>(Comparator.reverseOrder());  // Custom order

// TreeMap-specific operations
Map.Entry<String, Integer> firstEntry = treeMap.firstEntry();
Map.Entry<String, Integer> lastEntry = treeMap.lastEntry();
Map.Entry<String, Integer> lowerEntry = treeMap.lowerEntry("c");  // Strictly less
Map.Entry<String, Integer> floorEntry = treeMap.floorEntry("c");  // Less or equal
Map.Entry<String, Integer> higherEntry = treeMap.higherEntry("c");  // Strictly greater
Map.Entry<String, Integer> ceilingEntry = treeMap.ceilingEntry("c");  // Greater or equal
SortedMap<String, Integer> subMap = treeMap.subMap("a", "d");  // Range [a,d)

// TreeSet - sorted set
TreeSet<Integer> treeSet = new TreeSet<>();  // Natural order
TreeSet<String> treeSet = new TreeSet<>(Comparator.reverseOrder());  // Custom order

// TreeSet-specific operations
Integer first = treeSet.first();
Integer last = treeSet.last();
Integer lower = treeSet.lower(10);  // Strictly less
Integer floor = treeSet.floor(10);  // Less or equal
Integer higher = treeSet.higher(10);  // Strictly greater
Integer ceiling = treeSet.ceiling(10);  // Greater or equal
SortedSet<Integer> subSet = treeSet.subSet(5, 10);  // Range [5,10)
```

### PriorityQueue (Heap)

```java
// Creation
PriorityQueue<Integer> minHeap = new PriorityQueue<>();  // Min heap by default
PriorityQueue<Integer> maxHeap = new PriorityQueue<>(Collections.reverseOrder());  // Max heap
PriorityQueue<String> customHeap = new PriorityQueue<>(Comparator.comparing(String::length));  // Custom order

// Operations
minHeap.add(3);          // Add element
minHeap.offer(1);        // Add element (preferred)
int top = minHeap.peek();  // Get top without removing
int top = minHeap.poll();  // Remove and return top
int size = minHeap.size();  // Number of elements
boolean isEmpty = minHeap.isEmpty();  // Check if empty
minHeap.remove(3);       // Remove specific element (slow O(n))
minHeap.clear();         // Remove all elements

// Iteration (not in sorted order)
for (Integer num : minHeap) {
    // Process num
}

// To get elements in sorted order
while (!minHeap.isEmpty()) {
    System.out.println(minHeap.poll());
}

// Using custom class
class Task implements Comparable<Task> {
    int priority;
    String name;
    
    public Task(int priority, String name) {
        this.priority = priority;
        this.name = name;
    }
    
    @Override
    public int compareTo(Task other) {
        return Integer.compare(this.priority, other.priority);
    }
}

// Alternative with comparator
PriorityQueue<Task> taskQueue = new PriorityQueue<>(
    (t1, t2) -> Integer.compare(t1.priority, t2.priority)
);
```

### Stack & Queue

```java
// Stack (prefer Deque implementation)
Stack<Integer> stack = new Stack<>();  // Legacy class
stack.push(1);           // Add to top
int top = stack.pop();   // Remove and return top
int top = stack.peek();  // Get top without removing
boolean isEmpty = stack.isEmpty();  // Check if empty

// Better stack using Deque
Deque<Integer> stack = new ArrayDeque<>();
stack.push(1);          // Add to front
int top = stack.pop();  // Remove and return front
int top = stack.peek(); // Get front without removing

// Queue using Deque
Queue<Integer> queue = new LinkedList<>();  // LinkedList implements Queue
Queue<Integer> queue = new ArrayDeque<>();  // More efficient
queue.add(1);           // Add to end (throws exception if full)
queue.offer(2);         // Add to end (returns false if full)
int front = queue.remove();  // Remove and return front (throws exception if empty)
int front = queue.poll();    // Remove and return front (returns null if empty)
int front = queue.element(); // Get front without removing (throws exception if empty)
int front = queue.peek();    // Get front without removing (returns null if empty)
```

## Algorithms

### Sorting

```java
// Basic sorting with comparable
Arrays.sort(arr);  // For primitive arrays
Arrays.sort(objects);  // For objects implementing Comparable

// Sort with custom comparator
Arrays.sort(strings, String::compareToIgnoreCase);  // Method reference
Arrays.sort(people, Comparator.comparing(Person::getAge));  // Sort by age
Arrays.sort(people, Comparator.comparing(Person::getAge).reversed());  // Reverse order
Arrays.sort(people, Comparator.comparing(Person::getLastName)
                             .thenComparing(Person::getFirstName));  // Multiple fields

// Sort list
Collections.sort(list);  // Natural order (elements must implement Comparable)
list.sort(Comparator.naturalOrder());  // Java 8 alternative
list.sort(Comparator.comparing(String::length));  // Custom comparator

// Partial sort - find kth smallest
public int findKthSmallest(int[] nums, int k) {
    Arrays.sort(nums);
    return nums[k-1];
}

// Better: use partial sorting with QuickSelect or PriorityQueue
public int findKthSmallest(int[] nums, int k) {
    PriorityQueue<Integer> maxHeap = new PriorityQueue<>(Collections.reverseOrder());
    for (int num : nums) {
        maxHeap.offer(num);
        if (maxHeap.size() > k) {
            maxHeap.poll();
        }
    }
    return maxHeap.peek();
}
```

### Binary Search

```java
// Binary search on sorted array
public int binarySearch(int[] nums, int target) {
    int left = 0;
    int right = nums.length - 1;
    
    while (left <= right) {
        int mid = left + (right - left) / 2;  // Avoid integer overflow
        
        if (nums[mid] == target) {
            return mid;
        } else if (nums[mid] < target) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }
    
    return -1;  // Not found
}

// Using built-in binary search
int index = Arrays.binarySearch(nums, target);
// If found, returns index >= 0
// If not found, returns -(insertion point) - 1

// Find first occurrence
public int findFirstOccurrence(int[] nums, int target) {
    int left = 0;
    int right = nums.length - 1;
    int result = -1;
    
    while (left <= right) {
        int mid = left + (right - left) / 2;
        
        if (nums[mid] == target) {
            result = mid;  // Save result and continue searching left
            right = mid - 1;
        } else if (nums[mid] < target) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }
    
    return result;
}

// Binary search on custom predicate
public int binarySearchWithPredicate(int[] nums, Predicate<Integer> condition) {
    int left = 0;
    int right = nums.length - 1;
    
    while (left < right) {
        int mid = left + (right - left) / 2;
        
        if (condition.test(nums[mid])) {
            right = mid;
        } else {
            left = mid + 1;
        }
    }
    
    return left;
}
```

### Graph Traversal

#### Depth-First Search (DFS)

```java
// DFS for a graph represented as adjacency list
public void dfs(Map<Integer, List<Integer>> graph, int start, Set<Integer> visited) {
    visited.add(start);
    System.out.println(start);  // Process node
    
    for (int neighbor : graph.getOrDefault(start, Collections.emptyList())) {
        if (!visited.contains(neighbor)) {
            dfs(graph, neighbor, visited);
        }
    }
}

// Iterative DFS using stack
public void dfsIterative(Map<Integer, List<Integer>> graph, int start) {
    Set<Integer> visited = new HashSet<>();
    Stack<Integer> stack = new Stack<>();
    stack.push(start);
    
    while (!stack.isEmpty()) {
        int node = stack.pop();
        
        if (!visited.contains(node)) {
            visited.add(node);
            System.out.println(node);  // Process node
            
            // Add neighbors to stack (in reverse order to match recursive DFS)
            List<Integer> neighbors = graph.getOrDefault(node, Collections.emptyList());
            for (int i = neighbors.size() - 1; i >= 0; i--) {
                int neighbor = neighbors.get(i);
                if (!visited.contains(neighbor)) {
                    stack.push(neighbor);
                }
            }
        }
    }
}
```

#### Breadth-First Search (BFS)

```java
// BFS for a graph represented as adjacency list
public void bfs(Map<Integer, List<Integer>> graph, int start) {
    Set<Integer> visited = new HashSet<>();
    Queue<Integer> queue = new LinkedList<>();
    
    visited.add(start);
    queue.offer(start);
    
    while (!queue.isEmpty()) {
        int node = queue.poll();
        System.out.println(node);  // Process node
        
        for (int neighbor : graph.getOrDefault(node, Collections.emptyList())) {
            if (!visited.contains(neighbor)) {
                visited.add(neighbor);
                queue.offer(neighbor);
            }
        }
    }
}

// BFS with distance tracking
public Map<Integer, Integer> bfsWithDistance(Map<Integer, List<Integer>> graph, int start) {
    Map<Integer, Integer> distances = new HashMap<>();
    Queue<Integer> queue = new LinkedList<>();
    
    distances.put(start, 0);
    queue.offer(start);
    
    while (!queue.isEmpty()) {
        int node = queue.poll();
        int distance = distances.get(node);
        
        for (int neighbor : graph.getOrDefault(node, Collections.emptyList())) {
            if (!distances.containsKey(neighbor)) {
                distances.put(neighbor, distance + 1);
                queue.offer(neighbor);
            }
        }
    }
    
    return distances;
}
```

### Dynamic Programming

```java
// 1. Fibonacci with memoization
public int fib(int n, Map<Integer, Integer> memo) {
    if (memo.containsKey(n)) {
        return memo.get(n);
    }
    
    if (n <= 1) {
        return n;
    }
    
    int result = fib(n - 1, memo) + fib(n - 2, memo);
    memo.put(n, result);
    return result;
}

// 2. Bottom-up approach
public int fibBottomUp(int n) {
    if (n <= 1) {
        return n;
    }
    
    int[] dp = new int[n + 1];
    dp[1] = 1;
    
    for (int i = 2; i <= n; i++) {
        dp[i] = dp[i - 1] + dp[i - 2];
    }
    
    return dp[n];
}

// 3. Space-optimized
public int fibOptimized(int n) {
    if (n <= 1) {
        return n;
    }
    
    int a = 0, b = 1;
    for (int i = 2; i <= n; i++) {
        int next = a + b;
        a = b;
        b = next;
    }
    
    return b;
}

// Example: Longest Increasing Subsequence
public int lengthOfLIS(int[] nums) {
    if (nums.length == 0) {
        return 0;
    }
    
    int[] dp = new int[nums.length];
    Arrays.fill(dp, 1);
    int max = 1;
    
    for (int i = 1; i < nums.length; i++) {
        for (int j = 0; j < i; j++) {
            if (nums[i] > nums[j]) {
                dp[i] = Math.max(dp[i], dp[j] + 1);
            }
        }
        max = Math.max(max, dp[i]);
    }
    
    return max;
}
```

## Common Patterns

### Two Pointers

```java
// Find pair with given sum in sorted array
public int[] twoSum(int[] nums, int target) {
    int left = 0;
    int right = nums.length - 1;
    
    while (left < right) {
        int sum = nums[left] + nums[right];
        
        if (sum == target) {
            return new int[] { left, right };
        } else if (sum < target) {
            left++;
        } else {
            right--;
        }
    }
    
    return new int[] { -1, -1 };  // No solution found
}

// Remove duplicates from sorted array
public int removeDuplicates(int[] nums) {
    if (nums.length == 0) {
        return 0;
    }
    
    int i = 0;  // Position to write next unique element
    
    for (int j = 1; j < nums.length; j++) {
        if (nums[j] != nums[i]) {
            i++;
            nums[i] = nums[j];
        }
    }
    
    return i + 1;  // Length of unique elements
}
```

### Sliding Window

```java
// Find max sum subarray of size k
public int maxSumSubarray(int[] nums, int k) {
    if (nums.length < k) {
        return -1;
    }
    
    // Compute sum of first window
    int windowSum = 0;
    for (int i = 0; i < k; i++) {
        windowSum += nums[i];
    }
    
    int maxSum = windowSum;
    
    // Slide window and update maxSum
    for (int i = k; i < nums.length; i++) {
        windowSum = windowSum - nums[i - k] + nums[i];
        maxSum = Math.max(maxSum, windowSum);
    }
    
    return maxSum;
}

// Longest substring with at most k distinct characters
public int lengthOfLongestSubstringKDistinct(String s, int k) {
    if (s == null || s.length() == 0 || k == 0) {
        return 0;
    }
    
    Map<Character, Integer> charCount = new HashMap<>();
    int left = 0;
    int maxLength = 0;
    
    for (int right = 0; right < s.length(); right++) {
        char rightChar = s.charAt(right);
        charCount.put(rightChar, charCount.getOrDefault(rightChar, 0) + 1);
        
        // Shrink window while we have more than k distinct chars
        while (charCount.size() > k) {
            char leftChar = s.charAt(left);
            charCount.put(leftChar, charCount.get(leftChar) - 1);
            if (charCount.get(leftChar) == 0) {
                charCount.remove(leftChar);
            }
            left++;
        }
        
        maxLength = Math.max(maxLength, right - left + 1);
    }
    
    return maxLength;
}
```

### Fast and Slow Pointers

```java
// Detect cycle in linked list
public boolean hasCycle(ListNode head) {
    if (head == null || head.next == null) {
        return false;
    }
    
    ListNode slow = head;
    ListNode fast = head;
    
    while (fast != null && fast.next != null) {
        slow = slow.next;
        fast = fast.next.next;
        
        if (slow == fast) {
            return true;
        }
    }
    
    return false;
}

// Find middle of linked list
public ListNode findMiddle(ListNode head) {
    if (head == null) {
        return null;
    }
    
    ListNode slow = head;
    ListNode fast = head;
    
    while (fast != null && fast.next != null) {
        slow = slow.next;
        fast = fast.next.next;
    }
    
    return slow;  // Middle node
}
```

### Backtracking

```java
// Generate all subsets
public List<List<Integer>> subsets(int[] nums) {
    List<List<Integer>> result = new ArrayList<>();
    backtrack(result, new ArrayList<>(), nums, 0);
    return result;
}

private void backtrack(List<List<Integer>> result, List<Integer> current, int[] nums, int start) {
    result.add(new ArrayList<>(current));  // Add a copy of current subset
    
    for (int i = start; i < nums.length; i++) {
        current.add(nums[i]);
        backtrack(result, current, nums, i + 1);
        current.remove(current.size() - 1);  // Backtrack
    }
}

// Generate all permutations
public List<List<Integer>> permute(int[] nums) {
    List<List<Integer>> result = new ArrayList<>();
    backtrack(result, new ArrayList<>(), nums, new boolean[nums.length]);
    return result;
}

private void backtrack(List<List<Integer>> result, List<Integer> current, int[] nums, boolean[] used) {
    if (current.size() == nums.length) {
        result.add(new ArrayList<>(current));
        return;
    }
    
    for (int i = 0; i < nums.length; i++) {
        if (used[i]) continue;
        
        current.add(nums[i]);
        used[i] = true;
        
        backtrack(result, current, nums, used);
        
        current.remove(current.size() - 1);
        used[i] = false;
    }
}
```

## Java 8 Features

### Lambda Expressions & Functional Interfaces

```java
// Basic lambda syntax
Runnable runnable = () -> System.out.println("Hello");
Consumer<String> consumer = s -> System.out.println(s);
Predicate<Integer> isEven = n -> n % 2 == 0;
Function<String, Integer> strLength = s -> s.length();
BiFunction<Integer, Integer, Integer> sum = (a, b) -> a + b;
Supplier<Double> randomValue = () -> Math.random();
Comparator<String> byLength = (s1, s2) -> Integer.compare(s1.length(), s2.length());

// With method references
Consumer<String> printer = System.out::println;
Function<String, Integer> lengthFunc = String::length;
BiPredicate<String, String> isEqual = String::equals;
```

### Stream API

```java
// Creating streams
Stream<Integer> stream = Stream.of(1, 2, 3, 4);
Stream<String> stream = Arrays.stream(new String[] {"a", "b", "c"});
Stream<Integer> stream = list.stream();
Stream<Integer> stream = IntStream.range(1, 5).boxed();  // 1, 2, 3, 4

// Common operations
// Filter
List<Integer> evens = numbers.stream()
    .filter(n -> n % 2 == 0)
    .collect(Collectors.toList());

// Map
List<Integer> lengths = words.stream()
    .map(String::length)
    .collect(Collectors.toList());

// FlatMap
List<String> allWords = sentences.stream()
    .flatMap(s -> Arrays.stream(s.split(" ")))
    .collect(Collectors.toList());

// Sort
List<String> sorted = words.stream()
    .sorted()
    .collect(Collectors.toList());

// Custom sort
List<String> sortedByLength = words.stream()
    .sorted(Comparator.comparing(String::length))
    .collect(Collectors.toList());

// Limit & Skip
List<Integer> firstFive = numbers.stream()
    .limit(5)
    .collect(Collectors.toList());

List<Integer> afterFive = numbers.stream()
    .skip(5)
    .collect(Collectors.toList());

// Distinct
List<Integer> unique = numbers.stream()
    .distinct()
    .collect(Collectors.toList());

// Peek (for debugging)
List<Integer> result = numbers.stream()
    .peek(n -> System.out.println("Processing: " + n))
    .filter(n -> n > 5)
    .collect(Collectors.toList());

// Terminal operations
boolean allMatch = numbers.stream().allMatch(n -> n > 0);
boolean anyMatch = numbers.stream().anyMatch(n -> n > 10);
boolean noneMatch = numbers.stream().noneMatch(n -> n < 0);

Optional<Integer> first = numbers.stream().findFirst();
Optional<Integer> any = numbers.stream().findAny();

long count = numbers.stream().count();
int max = numbers.stream().max(Integer::compare).orElse(0);
int min = numbers.stream().min(Integer::compare).orElse(0);

// Reduction
int sum = numbers.stream().reduce(0, Integer::sum);
int product = numbers.stream().reduce(1, (a, b) -> a * b);
String concat = words.stream().reduce("", (a, b) -> a + b);

// Primitive streams
int sum = IntStream.of(1, 2, 3, 4).sum();
double avg = IntStream.of(1, 2, 3, 4).average().orElse(0);
int max = IntStream.of(1, 2, 3, 4).max().orElse(0);
long count = IntStream.of(1, 2, 3, 4).count();

// Ranges
IntStream.range(1, 5);      // 1, 2, 3, 4
IntStream.rangeClosed(1, 5);  // 1, 2, 3, 4, 5

// Collectors
List<String> list = stream.collect(Collectors.toList());
Set<String> set = stream.collect(Collectors.toSet());
String joined = stream.collect(Collectors.joining(", "));

Map<Integer, List<String>> groupByLength = words.stream()
    .collect(Collectors.groupingBy(String::length));

Map<Boolean, List<Integer>> partitioned = numbers.stream()
    .collect(Collectors.partitioningBy(n -> n % 2 == 0));

String csv = stream.collect(Collectors.joining(", ", "Start: ", " :End"));
```

### Optional

```java
// Creating Optional
Optional<String> optional = Optional.of("value");      // Non-null value
Optional<String> optional = Optional.ofNullable(value);  // May be null
Optional<String> empty = Optional.empty();             // Empty optional

// Using
```- Polymorphism