# leet-day45

# Count and Say

The "Count and Say" sequence is a sequence of digit strings defined by a recursive formula. Each term in the sequence is derived from the previous term in a specific way. To determine how to construct a term, the string is split into minimal substrings containing one unique digit each, and then the number of digits and the digit itself are concatenated.

## Problem Statement

Given a positive integer `n`, your task is to return the nth term of the "Count and Say" sequence.

## Example

**Input:**
```
n = 4
```

**Output:**
```
"1211"
```

**Explanation:**
- countAndSay(1) = "1"
- countAndSay(2) = say "1" = one 1 = "11"
- countAndSay(3) = say "11" = two 1's = "21"
- countAndSay(4) = say "21" = one 2 + one 1 = "12" + "11" = "1211"

## Approach

1. Initialize `result` with the base case "1".
2. Loop from `i = 2` to `n`, performing the following steps:
    - Generate the next term using the `generateNext` helper function.
    - Update `result` with the newly generated term.
3. Return the final `result`.

## Helper Functions

### `generateNext(const std::string& s)`

This function generates the next term of the sequence based on the current term. It iterates through the characters of the input string, counting consecutive occurrences of the same digit and appending the count and digit to the next term. After processing each digit, the count is reset.

## Complexity Analysis

- Time complexity: O(2^n)
  - Generating each term requires creating a new string that is on average twice as long as the previous term.
- Space complexity: O(2^n)
  - The space required to store each term.

## Usage

1. Instantiate the `Solution` class.
2. Call the `countAndSay` method with the desired value of `n`.
3. The method will return the nth term of the "Count and Say" sequence.

```cpp
#include <iostream>
#include <string>

class Solution {
public:
    std::string countAndSay(int n) {
        std::string result = "1"; // Base case
        
        for (int i = 2; i <= n; ++i) {
            result = generateNext(result); // Generate the next term
        }
        
        return result;
    }
    
private:
    std::string generateNext(const std::string& s) {
        std::string nextTerm;
        int count = 1;
        
        for (int i = 0; i < s.size(); ++i) {
            if (i + 1 < s.size() && s[i] == s[i + 1]) {
                count++; // Count the same digit
            } else {
                nextTerm += std::to_string(count) + s[i]; // Append count and digit
                count = 1; // Reset count
            }
        }
        
        return nextTerm;
    }
};

```

## Conclusion

The "Count and Say" sequence can be generated using a simple recursive approach where each term is derived from the previous term by counting the consecutive occurrences of the same digit. 
