# Feature Documentation: Question Creation and Compilation

## Overview
In this feature, questions are created by combining three distinct parts: **head**, **body**, and **tail**. The **body** represents the primary content visible to the user, where they interact or provide solutions. The **head** and **tail** are configurable sections that can include imports, setup code, or test cases. These parts are combined in the order **head → body → tail** when the question is sent for compilation.

This modular design allows flexibility in defining the problem scope while maintaining consistent scaffolding (head and tail) for evaluation or execution.

---

## Example 1 ( List Formatter)

The following example illustrates a question requiring a Python function in the body that returns list of even numbers.

### **Head**
```python
# Importing necessary modules
from typing import List
import sys
```

### **Body**
This part is visible to the user:
```python
    # Write your code below
    def find_even_numbers(nums: List[int]) -> List[int]:
        return [num for num in numbers if num % 2 == 0]
```

### **Tail**
```python
# Test cases (hidden from the user)
if __name__ == "__main__":
    
    user_input = input()
    numbers = list(map(int, user_input.split()))
    
    result = find_even_numbers(numbers)
    print(" ".join(str(key) for key in result))
```

### **Test Case Values**
   - `Input Parameters`:
   
        ```1 2 3 4 5 6 7 8```
   - `Expected Output`:

        ```2 4 6 8```


## Example 2 (Dictionary Formatter)

The following example illustrates a question requiring a Python function in the body that return a dictionary containing frequencies of the numbers, like {2: 4, 5: 1}.

### **Head**
```python
# Importing necessary modules
import sys
```

### **Body**
This part is visible to the user:
```python
    # Write your code below
    def count_occurrences(numbers):
    # Create an empty dictionary to store occurrences
    occurrences = {}
    
    # Loop through the list to count occurrences
    for num in numbers:
        if num in occurrences:
            occurrences[num] += 1
        else:
            occurrences[num] = 1

    # Return the dictionary
    return occurrences
```

### **Tail**
```python
# Test cases (hidden from the user)
if __name__ == "__main__":
    
    # Take custom input from the user
    user_input = input()
    # Convert the input string to a list of integers
    numbers = list(map(int, user_input.split()))

    # Call the function and display the result
    result = count_occurrences(numbers)
    if len(result):    
        for key in sorted(result.keys()):
            #cutomize this formatter as per your need
            print(key, result[key]) 

```

### **Test Case Values**
   - `Input Parameters`:
   
        ```1 1 5 6 7 8```
   - `Expected Output`:
        ```
        1 2
        5 1
        6 1
        7 1
        8 1
        ```


## Example 3 ( Array Formatter)

The following example illustrates a question requiring a Python function in the body that add 1 to each element in array.

### **Head**
```python
# Importing necessary modules
import sys
```

### **Body**
This part is visible to the user:
```python
    # Write your code below
    def add_one_to_array(arr):
        """
        Accepts an array and adds 1 to each element.
        
        Parameters:
        arr (list): List of integers
        
        Returns:
        list: List with 1 added to each element
        """
        return [x + 1 for x in arr]
```

### **Tail**
```python
# Test cases (hidden from the user)
if __name__ == "__main__":
    # Take custom input from the user
    input_array = input().strip().split()  # Input taken as space-separated values
    # Convert string array to int array
    int_array = [int(x) for x in input_array]
    # Call user function
    updated_array = add_one_to_array(int_array)
    # Print the result
    print(' '.join(map(str, updated_array)))
```

### **Test Case Values**
   - `Input Parameters`:
   
        ```1 2 3 4```
   - `Expected Output`:

        ```2 3 4 5```
