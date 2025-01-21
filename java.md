# Feature Documentation: Question Creation and Compilation

## **Language:** JAVA 

## Overview
In this feature, questions are created by combining three distinct parts:
**head**, **body**, and **tail**. The **body** represents the primary content visible to the user, where they interact or provide solutions. The **head** and **tail** are configurable sections that can include imports, setup code, or test cases. These parts are combined in the order **head → body → tail** when the question is sent for compilation.

This modular design allows flexibility in defining the problem scope while maintaining consistent scaffolding (head and tail) for evaluation or execution.

---

## Example 1 ( List Formatter )

The following example illustrates a question requiring a Java function in the body that returns list of even numbers.

### **Head**
```java
// Import necessary modules
import java.util.List;
import java.util.Scanner;
import java.util.Arrays;
import java.util.ArrayList;
import java.util.function.Function;
import java.util.function.Predicate;
import java.util.stream.Collectors;
```

### **Body**
This part is visible to the user:
```java
// Create a solution class with public function that will be completed by the user
class Solution {
    public static List<Integer> solution(List<Integer> numbers) {
        List<Integer> evens = new ArrayList<Integer>();
        
        // Filter even numbers
        for (int num : numbers) {
            if (num % 2 == 0) {
                evens.add(num);
            }
        }
        return evens;
    }
}
```

### **Tail**
```java
class Main {
    public static void main(String[] args) {
        Scanner scannerObj = new Scanner(System.in);
        String inputString = scannerObj.nextLine();

        // Split the string by specified delimiters (comma, period, or whitespace)
        String[] stringArray = inputString.split("[,\\s]");

        // Convert the String[] to a List<String>
        List<String> inputList = Arrays.stream(stringArray)
                                       .filter(element -> !element.isEmpty())
                                       .collect(Collectors.toList());


        /*************************************************************************************************
         *  NOTE:
         * This line is question dependent please change the type of array according to the required type.
         * Provide parser from string to required object.
         * And Filter Function to filter the object.
         *************************************************************************************************/
        List<Integer> parsedData = Main.processAndFilter(inputList, Integer::parseInt, num -> true);

        // Execute user function against the parsed output
        List<?> result = Solution.solution(parsedData);

        // Join and print the result (as Strings)
        System.out.println(String.join(" ", result.stream().map(Object::toString).toArray(String[]::new)));
    }

    /**
     * A generic method to process and filter elements from a list.
     *
     * @param inputList The input list of strings.
     * @param parser    A function to convert a string to the desired type.
     * @param filter    A predicate to filter the converted elements.
     * @param <T>       The type of elements in the resulting list.
     * @return A list of filtered and converted elements.
     */
    static <T> List<T> processAndFilter(List<String> inputList, Function<String, T> parser, Predicate<T> filter) {
        return inputList.stream()
                        .map(parser)          // Convert String to the desired type
                        .filter(filter)       // Filter based on the given predicate
                        .collect(Collectors.toList());
    }
}
```

### **Test Case Values**
   - `Input Parameters`:
   
        ```1 2 3 4 5 6 7 8```
   - `Expected Output`:

        ```2 4 6 8```