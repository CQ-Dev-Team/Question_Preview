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
import java.util.ArrayList;
import java.util.Scanner;
import java.util.List;
```

### **Body**
This part is visible to the user:
```java
// Create a solution class with public function that will be completed by the user
class Solution {
    public static List<Integer> findEvenNumbers(ArrayList<Integer> numbers) {
        // User input start here
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
        // Split the string by the specified delimiters (comma, period, or whitespace)
        String[] stringArray = inputString.split("[,\\.\\s]");
        // Convert the String[] to an int[]
        ArrayList<Integer> inputArray = new ArrayList<Integer>();
        for (int i = 0; i < stringArray.length; i++) {
            if (!stringArray[i].isEmpty()) {
                inputArray.add(Integer.parseInt(stringArray[i]));
            }
        }
        List<Integer> result = Solution.findEvenNumbers(inputArray);
        // Join user result
        String listString = "";
        for (int s : result)
        {
            listString += s + " ";
        }
        // Print the result
        System.out.println(listString);
    }
}
```

### **Test Case Values**
   - `Input Parameters`:
   
        ```1 2 3 4 5 6 7 8```
   - `Expected Output`:

        ```2 4 6 8```