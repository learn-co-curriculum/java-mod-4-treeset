# TreeSet

## Learning Goals

- Understand the difference between a HashSet and a TreeSet.
- Create TreeSets.
- Insert, Retrieve, and Remove elements from TreeSets.

## What is a TreeSet?

A TreeSet extends the AbstractSet class and implements the Set, SortedSet, and
NavigableSet interfaces. It stores non-duplicate elements in sorted order.

The data is stored in a binary search tree which offers O(log n) performance for
add, remove, and contains operations.

## TreeSet vs HashSet

Although both TreeSets and HashSets store non-duplicate elements, there are some
key differences between the two:

- The non-duplicate elements are stored in sorted order in the TreeSet whereas
  the HashSet elements don’t have any order to them.
- HashSet add, remove, access operations are O(1) but the same operations are
  O(log n) for TreeSet.
- TreeSet doesn’t allow null values but HashSet allows them (only one null value
  is allowed).

## Initializing a TreeSet

Since a TreeSet stores elements in a sorted order the elements should either
implement the Comparable interface or we should pass a custom Comparator when
initializing a TreeSet.

```java
import java.util.TreeSet;

public class TreeSetExample {
    public static void main(String[] args) {
        TreeSet<Integer> prices = new TreeSet<>();
        prices.add(50);
        prices.add(20);
        prices.add(100);
        prices.add(10);

        System.out.println(prices); // [10, 20, 50, 100]
    }
}
```

Here’s the same example with a custom Comparator:

```java
import java.util.Comparator;
import java.util.TreeSet;

class MaxComparator implements Comparator<Integer> {
    @Override
    public int compare(Integer o1, Integer o2) {
        return o2.compareTo(o1);
    }
}

public class TreeSetExample {
    public static void main(String[] args) {
        TreeSet<Integer> prices = new TreeSet<>(new MaxComparator());
        prices.add(50);
        prices.add(20);
        prices.add(100);
        prices.add(10);

        System.out.println(prices); // [100, 50, 20, 10]
    }
}
```

## Retrieving Elements from a TreeSet

There are several ways of accessing elements from a TreeSet because of its
sorted property. Let’s look at some of the methods for fetching elements from a
TreeSet.

```java
import java.util.TreeSet;

public class TreeSetExample {
    public static void main(String[] args) {
        TreeSet<Integer> prices = new TreeSet<>();
        prices.add(50);
        prices.add(20);
        prices.add(100);
        prices.add(10);
        prices.add(70);
        prices.add(60);

        System.out.println(prices); // [10, 20, 50, 60, 70, 100]

        // get the first element
        System.out.println(prices.first()); // 10

        // get the last element
        System.out.println(prices.last()); // 100

        // get a range of elements
        System.out.println(prices.subSet(10, 70)); // [10, 20, 50, 60]

        // get elements that are smaller than a given element
        System.out.println(prices.headSet(60)); // [10, 20, 50]

        // get elements that are larger than or equal to a given element
        System.out.println(prices.tailSet(20)); // [20, 50, 60, 70, 100]
    }
}
```

## Deleting Elements from a TreeSet

A TreeSet provides the `pollFirst` and `pollLast` methods from the
`NavigableSet` interface. It also provides the `remove` from the `Set`
interface.

```java
import java.util.TreeSet;

public class TreeSetExample {
    public static void main(String[] args) {
        TreeSet<Integer> prices = new TreeSet<>();
        prices.add(50);
        prices.add(20);
        prices.add(100);
        prices.add(10);
        prices.add(70);
        prices.add(60);

        System.out.println(prices); // [10, 20, 50, 60, 70, 100]

        System.out.println(prices.pollFirst()); // 10
        System.out.println(prices.pollLast()); // 100
        System.out.println(prices.remove(50)); // true
    }
}
```

## References

- [TreeSet Java Docs](https://docs.oracle.com/en/java/javase/17/docs/api/java.base/java/util/TreeSet.html)
