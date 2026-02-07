# Collection Framework

## Array List

A resizable array. Ordered. Indexed.

- Key traits
  - Maintains insertion order
  - Allows duplicates
  - Allows multiple `null`
  - Fast random access
  - Slow middle insert/delete


```Java
List<String> list = new ArrayList<>();

list.add("Java");
list.add("Kotlin");
list.add("Java");   // duplicate allowed
list.add(null);     // allowed

System.out.println(list);       // [Java, Kotlin, Java, null]
System.out.println(list.get(1)); // Kotlin
```

## HashSet

A set backed by HashMap.

- Key traits
  - No duplicates
  - No order guarantee
  - Allows one `null`
  - Fast operations `O(1)`
  - Depends on `hashCode()` and `equals()`

```Java
Set<String> set = new HashSet<>();

set.add("Java");
set.add("Kotlin");
set.add("Java");   // ignored
set.add(null);

System.out.println(set); // Order not guaranteed
```

## TreeSet

A sorted set backed by a Red-Black Tree.

- Key traits
  - No duplicates
  - Always sorted
  - No `null`
  - `O(log n)` operations
  - Uses `Comparable` or `Comparator`

```Java
Set<Integer> treeSet = new TreeSet<>();

treeSet.add(50);
treeSet.add(10);
treeSet.add(30);

System.out.println(treeSet); // [10, 30, 50]
```

## HashMap

A hash table-based key–value store.

- Key traits
  - Keys are unique
  - Values can repeat
  - One `null` key allowed
  - Multiple `null` values allowed
  - Average `O(1)`

```Java
Map<Integer, String> map = new HashMap<>();

map.put(1, "Java");
map.put(2, "Kotlin");
map.put(1, "Scala"); // overwrites

map.put(null, "NoKey");

System.out.println(map);
System.out.println(map.get(2)); // Kotlin
```

## TreeMap

A sorted map backed by a Red-Black Tree.

- Key traits
  - Keys are sorted
  - No `null` keys
  - Values can be `null`
  - `O(log n)`
  - Uses `Comparable` or `Comparator`

```Java
Map<Integer, String> treeMap = new TreeMap<>();

treeMap.put(3, "C");
treeMap.put(1, "A");
treeMap.put(2, "B");

System.out.println(treeMap); // {1=A, 2=B, 3=C}
```

## # Summary

| Collection | Order  | Duplicates | Nulls  | Complexity  |
|------------|--------|------------|--------|-------------|
| ArrayList  | Yes    | Yes        | Yes    | Access O(1) |
| HashSet    | No     | No         | One    | O(1)        |
| TreeSet    | Sorted | No         | No     | O(log n)    |
| HashMap    | No     | Key: No    | 1 key  | O(1)        |
| TreeMap    | Sorted | Key: No    | No key | O(log n)    |

## Sorting

`Collections.sort()`

```Java
List<Integer> list = new ArrayList<>(List.of(3, 1, 4, 2));
Collections.sort(list);

System.out.println(list); // [1, 2, 3, 4]
```

- Features:
  - Sorts in-place
  - Uses TimSort

- TimSort:
  - Hybrid of merge sort + insertion sort
  - Stable
  - Optimized for partially sorted data

Time Complexity: `O(n log n)`
Space Complexity: `O(log n)`

## Reverse

```Java
List<Integer> list = new ArrayList<>(List.of(1, 2, 3));
Collections.reverse(list);

System.out.println(list); // [3, 2, 1]
```

## Min and Max

```Java
List<Integer> list = List.of(10, 40, 20);

System.out.println(Collections.min(list)); // 10
System.out.println(Collections.max(list)); // 40
```

Time Complexity: `O(n)`

## Frequency

```Java
List<String> list = List.of("Java", "Kotlin", "Java");
int count = Collections.frequency(list, "Java");

System.out.println(count); // 2
```

Time Complexity: `O(n)`
