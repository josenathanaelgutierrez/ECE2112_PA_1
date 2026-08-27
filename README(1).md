# ECE 2112: Advanced Computer Programming and Algorithms
## Experiment 1: Introduction to Python Programming

### Objective of the Activity
The primary objectives of this laboratory activity are to:
- Use basic Python functions, operators, and string operations.
- Manipulate strings using indexing, slicing, and built-in string methods.
- Apply sequence unpacking to manipulate the elements of a list.
- Construct simple Python functions that return a specified result without using external libraries or complex loops.

### Experimental Approach and Detailed Discussion

#### A. Word Rotation Problem
**Goal:** Create a function `rotate_word(text)` that moves the first character of a non-empty string to the end while keeping all remaining characters in their original order and preserving capitalization.

**Approach:**
This problem is solved by leveraging Python's string slicing capabilities. Because strings are immutable in Python, we extract specific parts of the original string and concatenate them to build the output.
1. The first character is isolated using the index `0` (i.e., `text[0]`).
2. The rest of the string is extracted using a slice from index `1` to the end of the string (i.e., `text[1:]`).
3. The final result is constructed by concatenating the remainder of the string with the first character: `text[1:] + text[0]`. 
4. This approach natively handles single-character edge cases, as `text[1:]` gracefully evaluates to an empty string, simply returning the original character.

#### B. Username Builder Problem
**Goal:** Create a function `make_username(first_name, last_name)` that formats and combines two names into a specific lowercase username joined by a period.

**Approach:**
This problem relies heavily on built-in string methods to sanitize and standardize user inputs.
1. **Case Conversion:** The `.lower()` method is applied to both the `first_name` and `last_name` variables to ensure the final output is strictly lowercase.
2. **Whitespace Removal:** To handle names with spaces (e.g., "Ana Maria"), the `.replace(" ", "")` method is chained to the string to strip out all space characters.
3. **String Concatenation:** Once both strings are processed, they are concatenated together with a period `.` acting as the delimiter between the first and last names (e.g., `processed_first + "." + processed_last` or using an f-string `f"{processed_first}.{processed_last}"`).

#### C. Bookend Swap Problem
**Goal:** Create a function `swap_bookends(items)` that accepts a list of at least two elements and returns a new list where the first and last elements have swapped positions, leaving the middle elements in their original order.

**Approach:**
This problem strictly requires the use of extended sequence unpacking (PEP 3132) to decouple the list elements cleanly.
1. **Unpacking:** The input list is unpacked into three distinct variables using the syntax: `first, *middle, last = items`. 
   - `first` captures the element at index `0`.
   - `last` captures the element at index `-1`.
   - `*middle` uses the splat operator (`*`) to greedily capture all intermediate elements into a new list.
2. **Reconstruction:** A new list is constructed by placing `last` at the beginning, followed by the unpacked `middle` elements, and appending `first` at the end: `[last, *middle, first]`.
3. This sequence unpacking guarantees that the original list is not modified, fulfilling the requirement to return a brand new list.
