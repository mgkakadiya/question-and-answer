
# Java Stream Examples

## 1. Filter Example
Filter a list of integers to keep only even numbers:

```java
import java.util.Arrays;
import java.util.List;
import java.util.stream.Collectors;

public class StreamExample {
    public static void main(String[] args) {
        List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);
        
        List<Integer> evenNumbers = numbers.stream()
            .filter(n -> n % 2 == 0)
            .collect(Collectors.toList());

        System.out.println(evenNumbers);  // Output: [2, 4, 6, 8, 10]
    }
}
```

## 2. Map Example
Convert a list of strings to uppercase:

```java
import java.util.Arrays;
import java.util.List;
import java.util.stream.Collectors;

public class StreamMapExample {
    public static void main(String[] args) {
        List<String> names = Arrays.asList("john", "jane", "doe");

        List<String> upperCaseNames = names.stream()
            .map(String::toUpperCase)
            .collect(Collectors.toList());

        System.out.println(upperCaseNames);  // Output: [JOHN, JANE, DOE]
    }
}
```

## 3. Reduce Example
Sum a list of integers:

```java
import java.util.Arrays;
import java.util.List;

public class StreamReduceExample {
    public static void main(String[] args) {
        List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);

        int sum = numbers.stream()
            .reduce(0, Integer::sum);

        System.out.println(sum);  // Output: 15
    }
}
```

## 4. Sorted Example
Sort a list of strings alphabetically:

```java
import java.util.Arrays;
import java.util.List;
import java.util.stream.Collectors;

public class StreamSortedExample {
    public static void main(String[] args) {
        List<String> names = Arrays.asList("John", "Alice", "Bob");

        List<String> sortedNames = names.stream()
            .sorted()
            .collect(Collectors.toList());

        System.out.println(sortedNames);  // Output: [Alice, Bob, John]
    }
}
```

## 5. Distinct Example
Remove duplicates from a list of integers:

```java
import java.util.Arrays;
import java.util.List;
import java.util.stream.Collectors;

public class StreamDistinctExample {
    public static void main(String[] args) {
        List<Integer> numbers = Arrays.asList(1, 2, 3, 2, 4, 3, 5);

        List<Integer> distinctNumbers = numbers.stream()
            .distinct()
            .collect(Collectors.toList());

        System.out.println(distinctNumbers);  // Output: [1, 2, 3, 4, 5]
    }
}
```

## 6. FlatMap Example
Flatten a list of lists:

```java
import java.util.Arrays;
import java.util.List;
import java.util.stream.Collectors;

public class StreamFlatMapExample {
    public static void main(String[] args) {
        List<List<String>> listOfLists = Arrays.asList(
            Arrays.asList("a", "b", "c"),
            Arrays.asList("d", "e", "f"),
            Arrays.asList("g", "h", "i")
        );

        List<String> flatList = listOfLists.stream()
            .flatMap(List::stream)
            .collect(Collectors.toList());

        System.out.println(flatList);  // Output: [a, b, c, d, e, f, g, h, i]
    }
}
```

## 7. AnyMatch / AllMatch / NoneMatch Example
Check if any, all, or none of the elements match a condition:

```java
import java.util.Arrays;
import java.util.List;

public class StreamMatchExample {
    public static void main(String[] args) {
        List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);

        boolean anyEven = numbers.stream().anyMatch(n -> n % 2 == 0);
        boolean allEven = numbers.stream().allMatch(n -> n % 2 == 0);
        boolean noneEven = numbers.stream().noneMatch(n -> n % 2 == 0);

        System.out.println("Any even: " + anyEven);   // Output: true
        System.out.println("All even: " + allEven);   // Output: false
        System.out.println("None even: " + noneEven); // Output: false
    }
}
```

## 8. ForEach Example
Perform an action for each element in a list:

```java
import java.util.Arrays;
import java.util.List;

public class StreamForEachExample {
    public static void main(String[] args) {
        List<String> names = Arrays.asList("John", "Jane", "Doe");

        names.stream().forEach(name -> System.out.println(name));
        // Output:
        // John
        // Jane
        // Doe
    }
}
```
