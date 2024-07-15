
# JavaScript Array Cardio Practice - Day 1 — #JavaScript30 4/30
![](https://i.ytimg.com/vi/HB1ZC7czKRs/maxresdefault.jpg)



[Source URL](https://www.youtube.com/watch?v=HB1ZC7czKRs&ab_channel=WesBos)

## JavaScript Array Methods
- The filter method creates a new array with elements that pass a specified condition.
- The map method creates a new array by transforming each element in the original array.
- The sort method sorts the elements of an array in place.
- The reduce method reduces the elements of an array to a single value.
## JavaScript Coding Exercises
- Convert a list of links to a list of names and filter the list for names that include a specific string.
- Sort an array of people alphabetically by last name.
- Use reduce to sum up the instances of different transportation types in an array.
- Create an object with counts of different transportation types using reduce.
## Creating a Dictionary in JavaScript
- Start with a blank object and loop over each item to check if there is a zero value.
- If there is no zero value, create an entry for that item and increment the value.
- This allows for easy addition of new items to the dictionary.


# Understanding the `sort` Method with a Callback Function in JavaScript

The `sort` method in JavaScript is used to sort the elements of an array in place and returns the sorted array. The default sort order is according to string Unicode code points. However, when sorting numbers or custom objects, a comparison function is often provided to define the sort order.

#### Syntax

```javascript
arr.sort([compareFunction])
```

- **compareFunction** (optional): A function that defines the sort order. If omitted, the array elements are converted to strings and sorted according to their Unicode code points.

### How the Comparison Function Works

When a comparison function is provided, it is called repeatedly to compare pairs of elements in the array. The function should return:
- A negative value if the first argument (`a`) should be before the second argument (`b`).
- Zero if the arguments are equal.
- A positive value if the first argument (`a`) should be after the second argument (`b`).

The sort method uses this function to determine the relative order of the elements.

#### Example Comparison Function

```javascript
arr.sort((a, b) => a - b);
```

This comparison function sorts the array in ascending numerical order.

### Key Points

1. **Parameters `a` and `b`**:
   - In the comparison function `(a, b) => a - b`, `a` and `b` are the elements being compared.
   - **Important Clarification**: `a` is the second element, and `b` is the first element of the pair being compared. This can be verified by logging the values of `a` and `b`.

2. **Comparison Function Logic**:
   - `a - b` returns a negative value if `a < b`, indicating that `a` should come before `b`.
   - `a - b` returns zero if `a === b`, indicating that `a` and `b` are equal in order.
   - `a - b` returns a positive value if `a > b`, indicating that `a` should come after `b`.

### Detailed Example with Logging

Consider the array `[1, 3, 2, 2, 5, 2, 3, 7]`:

```javascript
let arr = [1, 3, 2, 2, 5, 2, 3, 7];
arr.sort((a, b) => {
  console.log(`Comparing a=${a}, b=${b}, result=${a - b}`);
  return a - b;
});
console.log(arr);
```

### Logging Output Explanation

1. **First Comparison**:
   - `a = 3`, `b = 1`
   - `3 - 1 = 2` (positive), so `3` should come after `1`.

2. **Second Comparison**:
   - `a = 2`, `b = 1`
   - `2 - 1 = 1` (positive), so `2` should come after `1`.

3. **Third Comparison**:
   - `a = 2`, `b = 2`
   - `2 - 2 = 0` (zero), so `2` and `2` are equal in order.

4. **Subsequent Comparisons**:
   - The sorting algorithm continues to compare and swap elements based on the comparison function.

### Final Sorted Array

After sorting, the array `[1, 3, 2, 2, 5, 2, 3, 7]` becomes `[1, 2, 2, 2, 3, 3, 5, 7]`.

### Summary

- The `sort` method in JavaScript can be customized using a comparison function.
- The comparison function `(a, b) => a - b` sorts numbers in ascending order.
- The parameters `a` and `b` represent the elements being compared, with `a` being the second element and `b` the first.
- Logging the comparisons helps understand the sorting process and verify the behavior of the comparison function.

By understanding and utilizing the comparison function, you can effectively control the sorting order of arrays in JavaScript.

Important: For the strings you can not use a.first - b.first > 0 inside the sort callback function, you have use something like this a.first > b.first cos you are not comparing numbers.